17

## Daedalus setup

Note: This doc has been written primarily considering the installation
on Linux Machine (Ubuntu)

### **Installing of phpstorm (You can use any other IDE as well)**

sudo snap install phpstorm \--classic

### **Installing Nginx**

[https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04){card-appearance="inline"}

[https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04){card-appearance="inline"}

### **Installing php**

sudo apt-get install php7.1 apt install php7.1-fpm

### **Phpmyadmin**

Download phpmyadmin 5.2version and install from
[here](https://www.phpmyadmin.net/downloads/)

nginx setup for phpmyadmin

Phpmyadmin config server { underscores_in_headers on; listen 8080; root
\[/opt/homebrew/var/www/Projects/ad-platform/phpMyAdmin\]; //change
index index.php ; location / { try_files \$uri \$uri/ /index.php?\$args;
add_header Access-Control-Allow-Origin \*; } location \~ \\.php\$ {
add_header Access-Control-Allow-Origin \*; fastcgi_pass
unix:/run/php/php7.1-fpm.sock; //change fastcgi_index index.php;
fastcgi_split_path_info \^(.+\\.php)(/.+)\$; fastcgi_param
SCRIPT_FILENAME \$document_root\$fastcgi_script_name; include
fastcgi_params; fastcgi_read_timeout 1800; } }

3 things change in the above config

1.  `port` If the port 8080 is already in use, please change the port
    number to available one.

2.  `root` change the root path to the workspace of your phpMyAdmin
    installed

3.  `fastcgi_pass` to make sure its running on the correct path

### Nginx set up

**make changes in the below path (take the updated file from existing
team members)**

etc/nginx/sites-enabled/ default

**Note:** make sure to read all the config and follow `//change` to
change accordingly and `//check` to confirm everything is in place.

nginx configbashworker_processes 1; events { worker_connections 1024; }
http { include mime.types; default_type application/octet-stream;
sendfile on; keepalive_timeout 65; \# DAEDALUS CONFIG
========================================= server {
underscores_in_headers on; listen 8088; server_name daedalus; root
\[\~/Daedalus/admis_php/public/\]; //change index index.php; location /
{ try_files \$uri \$uri/ /index.php?\$args; add_header
Access-Control-Allow-Origin \*; } location \~ \\.php\$ { root
\[\~/Daedalus/admis_php/public/\]; //change index index.php index.html
index.htm; try_files \$uri /index.php =404; fastcgi_split_path_info
\^(.+\\.php)(/.+)\$; fastcgi_pass unix:/run/php/php7.1-fpm.sock; //check
fastcgi_index index.php; fastcgi_param SCRIPT_FILENAME
\$document_root\$fastcgi_script_name; include fastcgi_params;
fastcgi_read_timeout 1800; if (!-e \$request_filename){ rewrite
\^(.\*)\$ /index.php break; } } location \~\*
\^.+.(ico\|xml\|js\|css\|jpg\|png\|jpeg\|gif)\$ { add_header
Access-Control-Allow-Origin \*; access_log off; expires 30d; root
\[\~/Daedalus/admis_php/public/\]; //change } } \# PHPMYADMIN CONFIG
========================================= server {
underscores_in_headers on; listen 8090; root \[\~/phpMyAdmin\]; //change
index index.php ; location / { try_files \$uri \$uri/ /index.php?\$args;
add_header Access-Control-Allow-Origin \*; } location \~ \\.php\$ {
add_header Access-Control-Allow-Origin \*; fastcgi_pass
unix:/run/php/php7.1-fpm.sock; //check fastcgi_index index.php;
fastcgi_split_path_info \^(.+\\.php)(/.+)\$; fastcgi_param
SCRIPT_FILENAME \$document_root\$fastcgi_script_name; include
fastcgi_params; fastcgi_read_timeout 1800; } location \~\*
\^.+.(ico\|xml\|js\|css\|jpg\|png\|jpeg\|gif)\$ { add_header
Access-Control-Allow-Origin \*; access_log off; expires 30d; root
\[\~/phpMyAdmin\]; //change } } }

**php folder should be present**

/etc/hosts

**Make sure php folder should is present on path**

/run/ nginx

**Start Nginx server and try pma/ on browser**

### Installing MySql - 5.6.51

sudo apt install mysql-server sudo mysql_secure_installation ALTER USER
\'root\'@\'localhost\' IDENTIFIED WITH mysql_native_password BY \'\';

FYI: MYSQL error while changing the password

`ERROR 1819 (HY000): Your password does not satisfy the current policy requirements`

If mysql `#1` error then make sure your password policy set to LOW.

Check what is the validate_password set to using below command

SHOW VARIABLES LIKE \'validate_password%\';

If the output is meduim better to set to LOW.

SET GLOBAL validate_password.policy=LOW;

#### **TO kill an already running port**

sudo kill \$(sudo lsof -t -i:3000)

### Importing Database in phpmyadmin

**Note:** Take the updated db dump from the existing team members

Create a database in phpmyadmin Open the directory where your sql file
is located Open the terminal from there Login into mysql ( mysql -u root
-p) and then enter password after enter press. ( -p is necesarry) Open
the database you want - use dadealus Source db name and it will start
importing

### To create user in MySql

sqlINSERT INTO users (id, name, email, team, remember_token, password,
deactivated, reset_token, reset_token_time, type, publisher_id,
reporting_to_id, group_id, wallet_id, agency_id, default_order_id,
referred_by_user_id, inside_sales_id, created_at, last_seen, updated_at)
VALUES (NULL, \'daedalus\', \'naman@daedalus.com\', \'\', NULL, \'Hashed
pass will come here\', \'0\', NULL, NULL, \'\', NULL, NULL, \'1\', NULL,
NULL, NULL, NULL, NULL, \'2021-03-12 12:27:54\', \'2020-12-11
12:43:23\', \'2021-03-12 12:27:54\');

Note: Replace the password in the above query, generate hashed password
using bcrypt

### Setting up dhx/ and the project

### Fetch .env file data

copy .env.local to .env cp Daedalus/admis_php/.env.local .env Change
user name and password accordingly in the .env file

OR

textIf .env.local not found, then run a bash script
\"Daedalus/scripts/daedalus/secret-manager.sh\" Prerequisite: install
gcloud locally, point gcloud project to \"dh-gcp-ads-sandbox\"

### Run these commands to clear cache and generate app_key

php artisan cache:clear php artisan config:clear php artisan
key:generate

output will be something like this
`base64:IxSc24+JizSQnx/eOT6JKSb3O6bp6DggTJ5z94Gsgfdg`

Copy the key to .env under APP_KEY variable

### References

[https://linuxize.com/post/how-to-install-php-on-ubuntu-18-04/](https://linuxize.com/post/how-to-install-php-on-ubuntu-18-04/){card-appearance="inline"}

[https://www.edureka.co/community/46181/how-to-uninstall-apache2-on-ubuntu](https://www.edureka.co/community/46181/how-to-uninstall-apache2-on-ubuntu){card-appearance="inline"}

[https://www.codegrepper.com/code-examples/php/Your+Composer+dependencies+require+the+following+PHP+extensions+to+be+installed%3A+dom%2C+mbstring%2C+xml%2C+xmlwriter](https://www.codegrepper.com/code-examples/php/Your+Composer+dependencies+require+the+following+PHP+extensions+to+be+installed%3A+dom%2C+mbstring%2C+xml%2C+xmlwriter){card-appearance="inline"}

[http://www.tecadmin.net/install-php-7-on-ubuntu](http://www.tecadmin.net/install-php-7-on-ubuntu){card-appearance="inline"}

[https://linuxhint.com/change-mysql-root-password-ubuntu/](https://linuxhint.com/change-mysql-root-password-ubuntu/){card-appearance="inline"}

## Php setup for Mac:

Daedalus need 7.1 to run the project. Here is the guildelines to setup
daedalus project in mac.

To install php7.1

brew tap shivammathur/php

as mac doesnot support 7.1 to install directly.

brew install php@7.1

## VS code and Jira Integration setup:

### Install the Atlassian for VS Code extension

1.  Open VS Code and select the **Extensions** icon on the left sidebar.

2.  Search for *Atlassian*

3.  Open **Jira and Bitbucket (Atlassian Labs)**.

4.  Click **Install**.

### Authenticate Jira Cloud

1.  Open **Atlassian Settings**. Open the command palette (macOS:
    `Command + Shift + P`; Windows: `Ctrl + Shift + P`), search for
    **Atlassian: Open Settings**, and hit Enter.

2.  Open the **Jira** tab, then open the **Authentication** section if
    it\'s not visible.

3.  Click **Login to Jira Cloud**. This will open the **Atlascode
    Integration** page in your browser. If you aren\'t already logged
    in, you\'ll be prompted to log in to your Atlassian account.

4.  On the **Atlascode Integration** page, click the **Authorize for**
    dropdown menu to open the list of sites (instances) you can
    authenticate with VS Code.

5.  Select the site you want to authenticate.

6.  Click **Accept** to complete authentication.

7.  Click **Back to VS Code** to return to VS Code.

### Working with VS code and Jira:

1.  Once above steps are done, you should able to see the tasks assigned
    to you in jira.

2.  Click on any task, new window with all the details of the task is
    viewed.

3.  Top right of the window, you will find the button `Start work` .

4.  Click on `Start work`, will create new branch and checkout to new
    branch. Options for you to change are:

    1.  **Transition issue**: TODO → IN PROGRESS → DONE

    2.  **Set up git branch**:

        1.  Select Repo → default will be whatever the repo project is
            open

        2.  Source Branch → default will pointing to whatever branch in
            opened VS window. You can select master, etc

        3.  Branch Prefix → default will be empty, you can add if you
            need anything specific

        4.  Local Branch → New branch name will be created, appended
            with Jira Id and Jira summary automatically read from the
            Jira task details.\
            Make sure not to remove Jira Id \[NHADSPLTL-1111\], other
            you can change accordingly.

        5.  Click on start → will create new branch and checkout to the
            same.

5.  Any commits to the branch and push to git will automatically updated
    in your Jira task. You can control the Jira task status, comments,
    etc from VS Code itself.

## Vue JS code Setup:

### Installation of nvm and node.

1.  Install `nvm` according to your laptop platform. Here are the steps
    for Mac with homebrew.

2.  Make sure you don\'t have any existing node installed.

    brew uninstall \--ignore-dependencies node brew uninstall \--force
    node

3.  brew update brew install nvm

4.  `mkdir ~/.nvm`

5.  Add this to your bash files and source it

    export NVM_DIR=\~/.nvm source \$(brew \--prefix nvm)/nvm.sh

6.  To see the available versions in nvm `nvm ls-remote `

7.  You can install any version, we need `16.14.2`. Run
    `nvm install v16.14.2` . You can install any number of versions in
    the same way

8.  `nvm use 16.14.2` to make v-16 to use, confirm by running `node -v`.

9.  `nvm ls` will show you all the installed node versions and also
    points to currently using one.

Ref:
[https://tecadmin.net/install-nvm-macos-with-homebrew/](https://tecadmin.net/install-nvm-macos-with-homebrew/){card-appearance="inline"}

### Daedalus setup to run node server

1.  `cd Daedalus/admin_php/` run `` php artisan config:cache` ``and
    `php artisan config:clear`.

2.  change you `.env` to

    APPENVIRONMENT=local VUE_EMULATE_PROD=false VUE_HOT_RELOAD=true

3.  `cd Daedalus/admin_php/`and run `npm install`

4.  After successful installation, run `npm run hotload`

5.  Open this link in browser to confirm node is running
    `http://localhost:8555/vue-bundle-dev.js` you should see the js
    file.

### Possible error while running `npm install:`

1.  some warning
    `The package-lock.json file was created with an old version of npm`
    you can ignore the warning, top fix this follow below steps:

2.  `cd Daedalus/admin_php/` run `rm -fv package-lock.json`

3.  now `npm install` see if solved.

4.  else check if you have `node_modules` folder is created?

5.  If not, you need to downgrade the node version. `nvm install 12`
    \[this version worked for me\].

6.  Run `nvm use 12` confirm by running `node -v` this should be
    pointing to `v12.*.*` version.

7.  Now run `npm install` should run fine with some warnings, which you
    can ignore.

8.  Then run `npm run hotload` and trigger this to confirm
    `http://localhost:8555/vue-bundle-dev.js`.

9.  `package-lock.json` is needed only to build. Now you can revert to
    master change \[as `package-lock.json` is committed to repo\]

10. Now also you can change the node version to `16.*.*`as this is the
    version we are having in prod.

11. After above steps, run `cd Daedalus/admin_php/` run
    `` php artisan config:cache` ``and `php artisan config:clear`and
    check if `npm run hotload` is working fine.
