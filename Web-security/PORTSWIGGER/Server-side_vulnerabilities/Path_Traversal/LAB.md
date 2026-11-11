![](images/Pasted%20image%2020261112023425.png)

## **Investigation**
- I was navigated to a webpage where there where several images and the user can view its details
![](images/Pasted%20image%2020261112023719.png)

- based on the description of the lab, I tried to click the view details button to if the url changes but it only showed the product id.
![](images/Pasted%20image%2020261112024323.png)

- Although I completed the lab without using burpsuite. I will use burpsuite in this writeup to clearly understand what is happening on the background.
- On burpsuite, we can see the images get request
![](images/Pasted%20image%2020261112024751.png)
- I then sent it to the repeater to test the filename parameter.
![](images/Pasted%20image%2020261112024853.png)

- Based on the lab description, we need to traverse to the root filesystem to read the `/etc/passwd` file, which contains system user details.
- At 1st I tested if the raw absolute `/etc/passwd` works but based on the results, it shows a bad request
![](images/Pasted%20image%2020261112025705.png)

- so we have to correctly traverse its directories in order to read the file(`../../../etc/passwd`).
![](images/Pasted%20image%2020261112025805.png)

