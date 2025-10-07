The following steps outline the complete information on the password
policy and complexity change added to all virtual machines (VMs) in DH
and ADS:

1.  Disabling Root login:

    - The \"/etc/ssh/sshd_config\" file is modified to disable root
      login.

    - The line matching the regex \'\^\\#?\\s?PermitRootLogin.\*\$\' is
      replaced with \"PermitRootLogin no\".

    - The SSH service (sshd) is restarted.

2.  Changing Password:

    - Passwords for two users, namely root and phoenix.admin, are
      changed.

    - Specific lines in the \"/etc/login.defs\" file are modified to
      adjust password-related settings.

3.  Password Policy Change:

    - The password age for all users is adjusted, along with password
      aging parameters and password complexity settings.

    - The system\'s authentication configuration is updated to enable
      password history and set the immutable attribute for a file.

    - Example settings include the last password change date, password
      expiration date, password inactivity, account expiration, and
      minimum/maximum number of days between password changes.

4.  Complexity Rules:

    - Password complexity settings in the
      \"/etc/security/pwquality.conf\" file are modified.

    - The following lines are added or modified:

      - \"maxsequence = 3\": Limits the maximum number of consecutive
        characters allowed in a password sequence to 3.

      - \"difok = 5\": Specifies that a new password must have a minimum
        of 5 characters that differ from the previous password.

      - \"gecoscheck = 1\": Enforces a check on the similarity between
        the user\'s password and their GECOS field.

5.  Removing Immutable Attribute:

    - The immutable attribute is removed from the
      \"/etc/pam.d/system-auth-ac\" file using the command \"chattr -i
      /etc/pam.d/system-auth-ac\".

    - This allows modifications to be made to the file.

6.  Updating Authentication Configuration:

    - The \"authconfig\" tool is used with various options to update the
      system\'s authentication configuration.

    - Options include enabling requirements for lowercase, uppercase,
      digit, and other special characters in passwords.

    - Additional options set the minimum password length, requirement
      for characters from at least one character class, limits on
      consecutive repeating characters, and enable LDAP authentication
      and home directory creation.

    - The updated configuration is applied using the \"\--update\" flag.

7.  Enabling Password History:

    - The \"pam_pwhistory.so\" module line is inserted in the correct
      location within the \"/etc/pam.d/system-auth-ac\" file.

    - This enables password history functionality, remembering the five
      most recent passwords used by a user to prevent their reuse.

8.  Alerting:

    - The playbook and associated scripts handle alerting for expired
      and warning passwords.

    - The playbook performs the following steps:

      - Lists users with expired passwords and users with password
        expiration warnings.

      - Prints the lists of expired and warning users.

      - Collects user information and generates CSV files for both
        expired and warning users.

      - Sends email notifications with attached CSV files containing the
        password expiry report.

      - Executes a script related to creating an inventory.

9.  Cron to Reset Password:

    - The playbook and script handle resetting passwords through a cron
      job.

    - The playbook connects to specified hosts using the
      \"phoenix.admin\" user and elevated privileges.

    - It disables facts gathering, ignores errors and unreachable hosts,
      and defines variables.

    - The script \"find-user-expiry.sh\" is used to identify users with
      expired passwords and password expiration warnings.

    - The password age for those users is reset by running the \"chage
      -d today {{ item }}\" command.

    - The script outputs the usernames of expired or warning users.

Overall, the process encompasses steps to disable root login, change
passwords, adjust password policies and complexity, enable password
history, and handle alerting and cron-based password resets.
