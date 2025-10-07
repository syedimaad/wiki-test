**[Login IP]{.underline}**

IP:[192.168.1.42]{style="color: rgb(38,50,56);"}

[**Use below user for the change**]{.underline}

su - newshunt-selfcare

[**Before starting/stopping export the security key**]{.underline}

\
export DECRPT_PASS=\"xb2mjwjStvgHQk8MM44Opw6t6\";

cd /home/newshunt-selfcare/tomcat/bin/

./controller.sh start/stop/restart

[**Change below properties File for mail change**]{.underline}\
\
/home/newshunt-selfcare/tomcat/webapps/ROOT/WEB-INF/classes/ldap-config.properties

email.admin=Infra Devops Team \<infra-devops@verse.in\>

**-Sanal K**
