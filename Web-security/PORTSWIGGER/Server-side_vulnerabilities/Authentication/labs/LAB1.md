![](images/Pasted%20image%2020261113020633.png)

![](images/Pasted%20image%2020261113020758.png)

- I 1st open burp suite then intercept the traffic in the log in page to send it to repeater and intruder since the challenge is about brute forcing.
![](images/Pasted%20image%2020261113020942.png)

![](images/Pasted%20image%2020261113020951.png)

![](images/Pasted%20image%2020261113021032.png)

![](images/Pasted%20image%2020261113021144.png)

- I then pressed the clear button 1st in intruder in order to remove any marked payload.
- I could use cluster bomb attack for this since it is brute force but based on my experience it will take up too much time processing so I used sniper attack instead.
- I 1st highlighted the username value and added the list of most common usernames then clicked start.
![](images/Pasted%20image%2020261113021432.png)

![](images/Pasted%20image%2020261113021456.png)

![](images/Pasted%20image%2020261113021559.png)

- I then did the same for the value of password and waited for the process to finish
- When the username sniper attack was done, I then noticed something off where only one of the payload has a different length which is app.
![](images/Pasted%20image%2020261113022309.png)

- I then tried it in the repeater and saw its response saying invalid password.
![](images/Pasted%20image%2020261113022344.png)

- Based on the response, the username I used may be the right username but we can not confirm it until we find out the password of this certain account.
- Quick note: change the value of username in the intruder before starting the sniper attack, otherwise it will not show a difference in burpsuite
![](images/Pasted%20image%2020261113023003.png)

- After waiting, I then noticed that one of the payloads has a different status code from the the others. Most of the payloads has a status code of 200 which means that the client's request has succeeded and the server has returned the expected response while status code 302 means that using those credentials can redirect the user to another page.
![](images/Pasted%20image%2020261113023447.png)

- I 1st tried it into the repeater and based on its response, we were successfully redirected 
![](images/Pasted%20image%2020261113023536.png)

![](images/Pasted%20image%2020261113023615.png)