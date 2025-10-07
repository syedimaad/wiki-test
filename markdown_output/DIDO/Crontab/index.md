\

- **crontab --e**

  This opens vi editor for you. Create the cron command using the
  following syntax:

  1\. The number of minutes after the hour (0 to 59)

  2\. The hour in military time (24 hour) format (0 to 23)

  3\. The day of the month (1 to 31)

  4\. The month (1 to 12)

  5\. The day of the week(0 or 7 is Sun, or use name)

  6\. The command to run

\

> 

\

- **crontab -l :** To list all cronjobs

  \

- **contab -r :** Remove your crontab i.e. remove all cronjobs.

  \

- **sudo crontab -l -u user_name :** List all cronjobs of specified user

::: {}
-Seren Jhanwar
:::
