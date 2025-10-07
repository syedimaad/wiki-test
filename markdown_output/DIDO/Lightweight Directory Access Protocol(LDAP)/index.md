- **LDAP(Lightweight Directory Access Protocol) :**

  [An application protocol]{style="text-decoration: none;"}[
  ]{style="text-decoration: none;"}[for accessing and maintaining
  distributed directory information
  services]{style="text-decoration: none;"}[
  ]{style="text-decoration: none;"}[over an IP network. Directory
  services]{style="text-decoration: none;"}[
  ]{style="text-decoration: none;"}[play an important role in developing
  intranet]{style="text-decoration: none;"}[
  ]{style="text-decoration: none;"}[and Internet applications by
  allowing the sharing of information about users, systems, networks,
  services, and applications throughout the
  network.]{style="text-decoration: none;"}

  A common use of LDAP is to provide a central place to store usernames
  and passwords. This allows many different applications and services to
  connect to the LDAP server to validate users

  \

[ ]{style="text-decoration: none;"}[PROTOCOL OVERVIEW :]{.underline}

[ ]{style="text-decoration: none;"}[A client starts an LDAP session by
connecting to an LDAP server, called a
]{style="text-decoration: none;"}[Directory
System]{style="text-decoration: none;"}[ Agent
]{style="text-decoration: none;"}[(DSA), by default on
]{style="text-decoration: none;"}[TCP]{style="text-decoration: none;"}[
]{style="text-decoration: none;"}[and
]{style="text-decoration: none;"}[UDP]{style="text-decoration: none;"}[
]{style="text-decoration: none;"}[port]{style="text-decoration: none;"}[
]{style="text-decoration: none;"}[389, or on port 636 for LDAPS (LDAP
over SSL, see below. The client then sends an operation request to the
server, and the server sends responses return. With some exceptions, the
client does not need to wait for a response before sending the next
request, and the server may send the responses in any order. All
information is transmitted using
]{style="text-decoration: none;"}[[Basic Encoding
Rules]{style="text-decoration: none;"}](https://en.wikipedia.org/wiki/Basic_Encoding_Rules)[(BER).]{style="text-decoration: none;"}

The client may request the following operations:

-  StartTLS --- use the LDAPv3 [Transport Layer Security
  ]{style="text-decoration: none;"}(TLS) extension for a secure
  connection

-  Bind ---[authenticate ]{style="text-decoration: none;"}and specify
  LDAP protocol version

- Search --- search for and/or retrieve directory entries

- Compare --- test if a named entry contains a given attribute value

- Add a new entry

- Delete an entry

- Modify an entry

- Modify Distinguished Name (DN) --- move or rename an entry

- Abandon --- abort a previous request

- Extended Operation --- generic operation used to define other
  operations

- Unbind --- close the connection (not the inverse of Bind)

\
[ ]{style="text-decoration: none;"}[DIRECTORY SERVICE :]{.underline}
[Directory service or name service maps the names of network resources
to their respective network addresses. It is a shared information
infrastructure for locating, managing, administering and organizing
everyday items and network resources, which can include volumes, folders
etc.]{style="text-decoration: none;"}

\

[**INSTALLING AND CONFIGURING OPENLDAP SERVER :**]{.underline}

[**\**]{.underline}

1.  Install the required packages of LDAP using :

    **yum -y install openldap\* migrationtools**

    **\**

2.  Create LDAP root password for administration purposes using and Copy
    the encrypted password from below output and keep it aside.:

    **slappasswd**

    **\**

3.  Edit the open LDAP server configuration file using :

    **cd /etc/openldap/slapd.d/cn=config\
    vi olcDatabase={2}hdb.ldif**

    Change the variables of "olcSuffix" and "olcRootDN" according to
    your domain.

    **olcSuffix: dc=learnitguide,dc=net\
    olcRootDN: cn=Manager,dc=learnitguide,dc=net**

    Add below lines at end of the opened file. Replace the olcRootPW
    with your copied password , and then save and exit the file.
    OlcTLSCertificate is just specifying the certificate locations here
    but  It'll be actually be created in step 6.

    **olcRootPW: {SSHA}bHSiwuPJEypHS6zHSE2Uy7M69sQjmkPL\
    olcTLSCertificateFile: /etc/pki/tls/certs/learnitguideldap.pem\
    olcTLSCertificateKeyFile:
    /etc/pki/tls/certs/learnitguideldapkey.pem**

    \

4.  Provide the monitor privileges. Replace "dc=my-domain,dc=com" to
    your domain component as you've described earlier in the below file.

    **vi olcDatabase={1}monitor.ldif**

    \

5.  Verify the configuration using :

    **slaptest -u**

    **\**

6.  Create the self-signed certificate using :

    **openssl req -new -x509 -nodes -out
    /etc/pki/tls/certs/learnitguideldap.pem -keyout
    /etc/pki/tls/certs/learnitguideldapkey.pem -days 365**

    Provide the company details to create the certificate. Verify the
    same using :

    **ll */etc/*pki/tls/certs/\*.pem**

    **\**

7.  Enable and start the slapd service

    **systemctl start slapd**

    **systemctl enable slapd**

    **\**

8.  Configure the LDAP database using :

    **cp /usr/share/openldap-servers/DB_CONFIG.example
    /var/lib/ldap/DB_CONFIG\
    chown -R ldap:ldap /var/lib/ldap/**

    Add the following LDAP schemas

    **ldapadd -Y EXTERNAL -H ldapi:/// -f
    /etc/openldap/schema/cosine.ldif\
    ldapadd -Y EXTERNAL -H ldapi:/// -f /etc/openldap/schema/nis.ldif\
    ldapadd -Y EXTERNAL -H ldapi:/// -f
    /etc/openldap/schema/inetorgperson.ldif**

    **\**

9.  Create base projects in OpenLDAP using migrationtools which we've
    already installed earlier

    **cd /usr/share/migrationtools/\
    vi migrate_common.ph**

    Edit migrate_common.ph by replacing the following entries :

    **\$DEFAULT_MAIL_DOMAIN = \"learnitguide.net\";**

    **\$DEFAULT_BASE = \"dc=learnitguide,dc=net\";**

    **\$EXTENDED_SCHEMA = 1;**

    **\**

10. Generate a base.ldif file for your domain inside the same
    migrationtools directory using :

    **touch /root/base.ldif**

    Specify the structure by copying the follwing content :

    **dn: dc=learnitguide,dc=net\
    objectClass: top\
    objectClass: dcObject\
    objectclass: organization\
    o: learnitguide net\
    dc: learnitguide\
    \
    dn: cn=Manager,dc=learnitguide,dc=net\
    objectClass: organizationalRole\
    cn: Manager\
    description: Directory Manager\
    \
    dn: ou=People,dc=learnitguide,dc=net\
    objectClass: organizationalUnit\
    ou: People\
    \
    dn: ou=Group,dc=learnitguide,dc=net\
    objectClass: organizationalUnit\
    ou: Group**

    **\**

11. Create local users ans set their passwords using :**useradd
    ldapuser1**

    **useradd ldapuser2\
    echo \"redhat\" \| passwd \--stdin ldapuser1\
    echo \"redhat\" \| passwd \--stdin ldapuser2**\
    [F]{style="text-decoration: none;"}[ilter out the users and groups
    to different locations using : ]{style="text-decoration: none;"}\
    **grep \":10\[0-9\]\[0-9\]\" /etc/passwd \> /root/passwd**\
    **grep \":10\[0-9\]\[0-9\]\" /etc/group \> /root/group**\
    Convert individual files to ldif format using : \
    **./migrate_passwd.pl/root/passwd /root/users.ldif**\
    **./migrate_group.pl /root/group /root/groups.ldif**\
    **\**

12. Import ldif users to LDAP database using : \
    [**ldapadd -x -W -D \"cn=Manager,dc=learnitguide,dc=net\" -f
    /root/base.ldif**]{style="text-decoration: none;"}[**\**
    ]{style="text-decoration: none;"}[**ldapadd -x -W -D
    \"cn=Manager,dc=learnitguide,dc=net\" -f
    /root/users.ldif**]{style="text-decoration: none;"}[**\**
    ]{style="text-decoration: none;"}[**ldapadd -x -W -D
    \"cn=Manager,dc=learnitguide,dc=net\" -f
    /root/groups.ldif**]{style="text-decoration: none;"}\
    [**\**
    ]{style="text-decoration: none;"}

13. Test the configuration using :\
    **ldapsearch -x cn=ldapuser1 -b dc=learnitguide,dc=net**\
    **\**

14. LDAP client configuration to use LDAP server\
    **yum install -y openldap-clients nss-pam-ldapd\
    authconfig-tui**\
    **\**

15. [Steps to follow ]{style="text-decoration: none;"}[for LDAP
    authentication]{style="text-decoration: none;"}\
    1.  Put '\*' on "Use LDAP".
    2.  Put '\*' on "Use LDAP Authentication"
    3.  Select next and enter
    4.  Enter server field with your server's ip address.
    5.  Enter Base DN field with your proper domain component name and
        select ok.\
        \

16. Test the client configuration using :\
    **getent passwd ldapuser1.**

> [ ]{style="text-decoration: none;"}[VIDEO LINK :
> ]{style="text-decoration: none;"}<https://www.learnitguide.net/2016/01/configure-openldap-server-on-rhel7.html>

> \
>
> NOTE
>
> The path used in the above installation is random. Ensure to use the
> correct/specified/desired location while you install it on your system
>
> \
>
> \
>
> \

\

\

\

\

\
