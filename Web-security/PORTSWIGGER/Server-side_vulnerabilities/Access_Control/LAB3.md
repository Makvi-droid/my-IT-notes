![](images/Pasted%20image%2020261112054208.png)

- based on the description of the challenge, I hypothesized that we can change the admin value of a user from `false` to `true`. Changing the users admins value can give the user an admin privilege or permission.
- I logged in using the credentials given in the description.
![](images/Pasted%20image%2020261112054517.png)

- After logging in, I then opened the inspector and navigated to where the cookies are stored which is in storage tab.
![](images/Pasted%20image%2020261112054941.png)

- As we can see in the cookies, my hypothesis was right that we can edit the users the admin value from `false` to `true` in order to escalate or give the user admin permission and privileges.
- After changing the admin value, the UI has now changed and an admin panel has appeared.
![](images/Pasted%20image%2020261112055149.png)
- The challenge has now been completed and I can delete the user that challenge wants me to delete.
