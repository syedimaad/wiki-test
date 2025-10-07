+--------+-----------------+---------------+------------+---------------+
| **SI** | **Issue **      | **Priority**  | **Status** | **Team**      |
+--------+-----------------+---------------+------------+---------------+
| 1.     | Browsable Web   | Critical      | Fixed      |               |
|        | Directories     |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 2.     | CGI Generic SQL | Critical      | Fixed      |               |
|        | Injection       |               |            |               |
|        | (blind, time    |               |            |               |
|        | based)          |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 3.     | PHP vulnerable  | High          |            |               |
|        | version         |               |            |               |
|        | detection       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 4.     | BMC Server      | High          |            |               |
|        | Automation RSCD |               |            |               |
|        | Agent Weak ACL  |               |            |               |
|        | XML-RPC         |               |            |               |
|        | Arbitrary       |               |            |               |
|        | Command         |               |            |               |
|        | Execution       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 5.     | SSL Version 2   | Medium        | Fixed      | Infra/Ravi    |
|        | and 3 Protocol  |               |            | Kumar         |
|        | Detected        |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 6.     | SSL Certificate | Medium        | Fixed      | Infra/Ravi    |
|        | Signed Using    |               |            | Kumar         |
|        | Weak Hashing    |               |            |               |
|        | Algorithm       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 7.     | Apache Tomcat   | High          |            |               |
|        | vulnerable      |               |            |               |
|        | version         |               |            |               |
|        | detection       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 8.     | SNMP Agent      | High          |            |               |
|        | Default         |               |            |               |
|        | Community Name  |               |            |               |
|        | (public)        |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 9.     | SSL Medium      | Medium        | Fixed      | Infra/Ravi    |
|        | Strength Cipher |               |            | Kumar         |
|        | Suites          |               |            |               |
|        | Supported       |               |            |               |
|        | (SWEET32)       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 10\.   | Apache          | Medium        |            |               |
|        | mod_status      |               |            |               |
|        | /server-status  |               |            |               |
|        | Information     |               |            |               |
|        | Disclosure      |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 11\.   | Apache          | Medium        |            |               |
|        | vulnerable      |               |            |               |
|        | version         |               |            |               |
|        | detection       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 12\.   | HSTS Missing    | Medium        |            |               |
|        | From HTTPS      |               |            |               |
|        | Server (RFC     |               |            |               |
|        | 6797)           |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 13\.   | Nginx           | Medium        |            |               |
|        | vulnerable      |               |            |               |
|        | version         |               |            |               |
|        | detection       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 14\.   | TLS Version 1.0 | Medium        | Excluded   | Infra/Ravi    |
|        | & 1.1 Protocol  |               |            | Kumar         |
|        | Deprecated      |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 15\.   | SSL Self-Signed | Medium        |            | Infra/Ravi    |
|        | Certificate     |               |            | Kumar         |
+--------+-----------------+---------------+------------+---------------+
| 16\.   | SSL Certificate | Medium        |            | Infra/Ravi    |
|        | Cannot Be       |               |            | Kumar         |
|        | Trusted         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 17\.   | SSL RC4 Cipher  | Medium        | Fixed      | Infra/Ravi    |
|        | Suites          |               |            | Kumar         |
|        | Supported (Bar  |               |            |               |
|        | Mitzvah)        |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 18\.   | SSL Certificate | Medium        |            |               |
|        | Expiry          |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 19\.   | SSL Weak Cipher | Medium        | Fixed      | Infra/Ravi    |
|        | Suites          |               |            | Kumar         |
|        | Supported       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 20\.   | SNMP            | Medium        |            |               |
|        | \'GETBULK\'     |               |            |               |
|        | Reflection DDoS |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 21\.   | JQuery          | Medium        |            | Infra/Ravi    |
|        | vulnerable      |               |            | Kumar         |
|        | version         |               |            |               |
|        | detection       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 22\.   | HTTP TRACE /    | Medium        |            |               |
|        | TRACK Methods   |               |            |               |
|        | Allowed         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 23\.   | Git Repository  | Medium        |            |               |
|        | Served by Web   |               |            |               |
|        | Server          |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 24\.   | Web Application | Medium        |            | Infra/Ravi    |
|        | Potentially     |               |            | Kumar         |
|        | Vulnerable to   |               |            |               |
|        | Clickjacking    |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 25\.   | SSL/TLS         | Medium        | comment    | Infra/Ravi    |
|        | Protocol        |               |            | Kumar         |
|        | Initialization  |               |            |               |
|        | Vector          |               |            |               |
|        | Implementation  |               |            |               |
|        | Information     |               |            |               |
|        | Disclosure      |               |            |               |
|        | Vulnerability   |               |            |               |
|        | (BEAST)         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 26\.   | SSL/TLS         | Medium        | Fixed      | Infra/Ravi    |
|        | Diffie-Hellman  |               |            | Kumar         |
|        | Modulus \<=     |               |            |               |
|        | 1024 Bits       |               |            |               |
|        | (Logjam)        |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 27\.   | SSL/TLS         | Medium        |            | Infra/Ravi    |
|        | EXPORT_RSA \<=  |               |            | Kumar         |
|        | 512-bit Cipher  |               |            |               |
|        | Suites          |               |            |               |
|        | Supported       |               |            |               |
|        | (FREAK)         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 28\.   | SSH Weak        | Medium        | comment    | Infra/Ravi    |
|        | Algorithms      |               |            | Kumar         |
|        | Supported       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 29\.   | SSH Terrapin    | Medium        | comment    | Infra/Ravi    |
|        | Prefix          |               |            | Kumar         |
|        | Truncation      |               |            |               |
|        | Weakness        |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 30\.   | OpenSSH         | Medium        |            |               |
|        | vulnerable      |               |            |               |
|        | version         |               |            |               |
|        | detection       |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 31\.   | WordPress User  | Medium        |            |               |
|        | Enumeration     |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 32\.   | Web Server      | Low           |            |               |
|        | Transmits       |               |            |               |
|        | Cleartext       |               |            |               |
|        | Credentials     |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 33\.   | Web Server Uses | Low           |            |               |
|        | Basic           |               |            |               |
|        | Authentication  |               |            |               |
|        | Without HTTPS   |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 34\.   | Web Server      | Low           |            |               |
|        | Allows Password |               |            |               |
|        | Auto-Completion |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 35\.   | SSH Weak MAC    | Low           |            |               |
|        | Algorithms      |               |            |               |
|        | Enabled         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 36\.   | SSH Server CBC  | Low           |            |               |
|        | Mode Ciphers    |               |            |               |
|        | Enabled         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 37\.   | SSH Weak Key    | Low           |            |               |
|        | Exchange        |               |            |               |
|        | Algorithms      |               |            |               |
|        | Enabled         |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 38\.   | SSL Certificate | Low           |            |               |
|        | Chain Contains  |               |            |               |
|        | RSA Keys Less   |               |            |               |
|        | Than 2048 bits  |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 39\.   | web.config File | Low           |            |               |
|        | Information     |               |            |               |
|        | Disclosure      |               |            |               |
+--------+-----------------+---------------+------------+---------------+
| 40\.   | Elasticsearch   | Low           |            |               |
|        | Unrestricted    |               |            |               |
|        | Access          |               |            |               |
|        | Information     |               |            |               |
|        | Disclosure      |               |            |               |
+--------+-----------------+---------------+------------+---------------+
