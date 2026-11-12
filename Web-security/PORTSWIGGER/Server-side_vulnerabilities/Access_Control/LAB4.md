![](images/Pasted%20image%2020261112212758.png)

![](images/Pasted%20image%2020261112212944.png)

- I 1st logged in using the credentials that the challenge had `wiener:peter`
- After logging in, it then showed me an api key.
![](images/Pasted%20image%2020261112213209.png)

- since we have to know the api key of carlos in order to gain access to it. I 1st tried to gather as much as clues as I can in the page's source code and in the inspector if it leaked any api key of carlos.
- After interacting with it's features, I noticed that every blog post has a users name and in it is its user id.
![](images/Pasted%20image%2020261112213716.png)

- Although the user is an administrator, the challenge is about horizontal privilege escalation which is to gain access to another users account with the same privilege as ours.
- With this clue, I hypothesized that carlos may have posted or commented on any of the posts so I opened up every post to search for a user name carlos. 
- I then found a post of carlos which is called 21st century dreaming
![](images/Pasted%20image%2020261112214050.png)

- I then viewed its page source then found its user id
![](images/Pasted%20image%2020261112214211.png)

- I copied its user id then pasted it in my own user id in the url. This is the before
![](images/Pasted%20image%2020261112214355.png)

- And this is after
![](images/Pasted%20image%2020261112214436.png)

- After pressing enter, the UI has now changed and gained access to carlos' account
![](images/Pasted%20image%2020261112214525.png)

