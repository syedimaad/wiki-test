# Prerequisites

1.  To run the command, user account(your ldap) that has sudo access to
    below remote servers

2.  ssh-client (preinstalled on Mac & Linux; use putty for windows)

# Servers

10.93.0.17

# Steps

1.  from terminal, `ssh satosh.dhanyamraju@10.93.0.17` (use your ldap id
    & password)

2.  `sudo -i -u dh-analytics`

3.  you\'ll be on the correct directory to run below command 

`confluent-5.1.0/bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic analytics-events | grep "dh.Q2tFUHorTno2d1VRRlluOUY4d25wQT09A"| grep event_name --color=always`
