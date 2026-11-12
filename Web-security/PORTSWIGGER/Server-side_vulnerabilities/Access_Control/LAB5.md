![](images/Pasted%20image%2020261112230826.png)

- I 1st started with checking its source code then eventually logging in when I did not find any clues.
- After logging in, I noticed that the URL had an account id parameter in it so I decided to change it into carlos to test it.
![](images/Pasted%20image%2020261112233333.png)

![](images/Pasted%20image%2020261112233402.png)

- At 1st I thought the password was leaked in the web pages source code. So I searched all around until I had to open the solution and peak a bit.
- That is when I had an aha moment and felt stupid at my process.
- Turns out we can just change the account id into `administrator` in order to see the administrators password.
![](images/Pasted%20image%2020261112233649.png)

- Since the password is already in the input field, we can just check its source code to see what its value is in plain sight.
![](images/Pasted%20image%2020261112233805.png)

- with that, I then logged in as administrator and pasted the password I copied at the source code. 
- It then navigated us to the administrator account where we can now delete carlos and complete the challenge.
![](images/Pasted%20image%2020261112233954.png)

![](images/Pasted%20image%2020261112234005.png)

![](images/Pasted%20image%2020261112234015.png)


---
## **My mistake:**
- since the lesson before this lab was about horizontal to vertical privilege escalation, I assumed that the process of exploitation should be like that but it seems I was following it to much and ended up overthinking it.