\

Step 1 :-  Login to 192.168.2.199 server with phoenix admin user

step 2 :-  Go to /home/phoenix.admin/dashboard

step 3 :-   take the back up of all-servers-with-ip.csv

   Command :-     cp   -p   all-servers-with-ip.csv   
 all-servers-with-ip.csv.xxxDate

step 4 :- edit the file and add the provided hosts details by sreeraj

  Should be below manner.

     192.168.10.148,Public,dh-news,dh-news,dh-news

    192.168.10.149,Public,dh-news,dh-news,dh-news

And make sure the added hosts are enabled password-less access for newly
added hosts.

  Ex:- 

\[phoenix.admin@neo7 dashboard\]\$ ssh 192.168.10.148\
\[phoenix.admin@dhpub-ws-n12 \~\]\$

\

Note :- Remove immediately the hosts which we have released/in shutdown
mode.

\

\

\
