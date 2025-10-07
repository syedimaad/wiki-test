+-----------+-----------------+--------------+--------------+------------+------------+
| **SI**    | **Issue**       | **Team       | **Priority** | **Status** | **Verified |
|           |                 | Addressing   |              |            | by sec**   |
|           |                 | issue**      |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 1.        | Login bypass    | infra        | Critical     | Fixed      | Done       |
+-----------+-----------------+--------------+--------------+------------+------------+
| 2.        | Redis Server    | DB           | Critical     | pending    |            |
|           | Unprotected by  |              |              |            |            |
|           | Password        |              |              |            |            |
|           | Authentication  |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 3.        | Java JMX Agent  | DB           | Critical     | pending    |            |
|           | Insecure        |              |              |            |            |
|           | Configuration   |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 4.        | SSL Medium      | network      | High         | Fixed      | Done       |
|           | Strength Cipher |              |              |            |            |
|           | Suites          |              |              |            |            |
|           | Supported       |              |              |            |            |
|           | (SWEET32)       |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 5.        | Grafana Labs    | Infra        | High         | Fixed      | Done       |
|           | Security Bypass |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 6.        | Jenkin\'s       | Dependency   | High         | pending    |            |
|           | vulnerable      | on Eng       |              |            |            |
|           | version         |              |              |            |            |
|           | detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 7.        | Python          | Engineering  | High         | Fixed      | Done       |
|           | Vulnerable      |              |              |            |            |
|           | Version         |              |              |            |            |
|           | Detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 8.        | Apache Tomcat   | Engineering  | High         | Fixed      | Done       |
|           | Vulnerable      |              |              |            |            |
|           | Version         |              |              |            |            |
|           | Detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| 9.        | Elastic Kibana  | Engineering  | High         | Fixed      | Done       |
|           | vulnerable      |              |              |            |            |
|           | version         |              |              |            |            |
|           | detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **10.**   | Apache Tomcat   | Engineering  | Medium       | Fixed      | Done       |
|           | Default Files   |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **11.**   | Elasticsearch   | Engineering  | Medium       | Review+    |            |
|           | Unrestricted    |              |              | Pending    |            |
|           | Access          |              |              |            |            |
|           | Information     |              |              |            |            |
|           | Disclosure      |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **12.**   | Grafana Labs    | DH           | Medium       | pending    |            |
|           | Stored XSS      |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **13.**   | Grafana Labs    |              | Medium       | Fixed      | Done       |
|           | Incorrect       |              |              |            |            |
|           | Authorization   |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **14.**   | Grafana Labs    | Infra        | Medium       | Waiting    |            |
|           | vulnerable      |              |              | for stable |            |
|           | version         |              |              |            |            |
|           | detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **15.**   | JQuery 1.2 \<   | Engineering  | Medium       | Fixed      | Done       |
|           | 3.5.0 Multiple  |              |              |            |            |
|           | XSS             |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **16.**   | Web application | Google       | Medium       | pending    |            |
|           | information     |              |              |            |            |
|           | disclosure      |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **17.**   | Apache Spark    | infra        | Medium       | pending    |            |
|           | Vulnerable      |              |              |            |            |
|           | Version         |              |              |            |            |
|           | Detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **18.**   | SSL Anonymous   | network      | Medium       | Fixed      | Done       |
|           | Cipher Suites   |              |              |            |            |
|           | Supported       |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **19.**   | SSL/TLS         | network      | Medium       | Fixed      | Done       |
|           | Protocol        |              |              |            |            |
|           | Initialization  |              |              |            |            |
|           | Vector          |              |              |            |            |
|           | Implementation  |              |              |            |            |
|           | Information     |              |              |            |            |
|           | Disclosure      |              |              |            |            |
|           | Vulnerability   |              |              |            |            |
|           | (BEAST)         |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **20.**   | SSL Certificate | network      | Medium       | Fixed      | Done       |
|           | Cannot Be       |              |              |            |            |
|           | Trusted         |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **21.**   | SSL Self-Signed | network      | Medium       | Fixed      | Done       |
|           | Certificate     |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **22.**   | SSL Certificate | infra        | Medium       | In         |            |
|           | Expiry          |              |              | progress   |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **23.**   | HSTS Missing    | Not          | Medium       | Not        |            |
|           | From HTTPS      | relevant     |              | relevant   |            |
|           | Server (RFC     |              |              |            |            |
|           | 6797)           |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **24.**   | Web Application | infra        | Medium       | Inprogress |            |
|           | Potentially     |              |              |            |            |
|           | Vulnerable to   |              |              |            |            |
|           | Clickjacking    |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **25.**   | Nginx           | infra        | Medium       | In         |            |
|           | vulnerable      |              |              | progress   |            |
|           | version         |              |              |            |            |
|           | detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **26.**   | HTTP TRACE /    | infra        | Medium       | pending    |            |
|           | TRACK Methods   |              |              |            |            |
|           | Allowed         |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **27.**   | OpenSSH         | Engineering  | Medium       | Fixed      | Done       |
|           | vulnerable      |              |              |            |            |
|           | version         |              |              |            |            |
|           | detected        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **28.**   | SSH Terrapin    | infra        | Medium       | pending    |            |
|           | Prefix          |              |              |            |            |
|           | Truncation      |              |              |            |            |
|           | Weakness        |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **29.**   | NetScaler       | Security     | Medium       | Fixed      | Done       |
|           | Unencrypted Web |              |              |            |            |
|           | Management      |              |              |            |            |
|           | Interface       |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **30.**   | SSH Server CBC  |              | Low          |            |            |
|           | Mode Ciphers    |              |              |            |            |
|           | Enabled         |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **31.**   | SSH Weak Key    |              | Low          |            |            |
|           | Exchange        |              |              |            |            |
|           | Algorithms      |              |              |            |            |
|           | Enabled         |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **32.**   | Web Server      |              | Low          |            |            |
|           | Transmits       |              |              |            |            |
|           | Cleartext       |              |              |            |            |
|           | Credentials     |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **33.**   | Web Server      |              | Low          |            |            |
|           | Allows Password |              |              |            |            |
|           | Auto-Completion |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
| **34.**   | ICMP Timestamp  |              | Low          |            |            |
|           | Request Remote  |              |              |            |            |
|           | Date Disclosure |              |              |            |            |
+-----------+-----------------+--------------+--------------+------------+------------+
