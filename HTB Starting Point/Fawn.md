# Fawn
 Source: https://app.hackthebox.com/machines/Fawn

## Enumeration

First step as always, I `ping -c4 <TARGET_IP>` to test the connection and get a successful response.

<img width="626" height="222" alt="image" src="https://github.com/user-attachments/assets/a836f4f3-bf82-448b-ae37-490eea9d6fc5" />

...and followed it with an `nmap -sV <TARGET_IP>`.

<img width="771" height="242" alt="image" src="https://github.com/user-attachments/assets/2e32c02e-44f9-42fd-9dbd-2f2973a42fe0" />

It looks like port 21 is open with FTP running version vsFTPd 3.0.3. We've found our way in.

## Foothold

I tried to connect to the FTP service by running `ftp <TARGET_IP>`, but of course, we require a username and password.

I did a quick search on vsFTPd 3.0.3 and came across <a href="https://askubuntu.com/questions/354178/what-is-ftp-username-and-password-for-vsftpd">this forum post</a> in which one user warned about an "anonymous" login.

Another <a href="https://linuxconfig.org/setup-ftp-server-on-linux">site<a/> mentions that the `anonymous` login is simply just `anonymous` as the username with no password. Seems like a good login to try with nothing else available at the moment.

<img width="627" height="200" alt="image" src="https://github.com/user-attachments/assets/47afe167-b87d-4443-818c-12e6736f59c2" />

And it worked! Now that I'm connected via FTP, I just need to find the flag. `ls` shows that it's right there. I can retrieve the file with `get file.txt` to open it on my own computer now.

<img width="1259" height="428" alt="image" src="https://github.com/user-attachments/assets/761cd979-76e5-438c-b248-55ab5fee3da9" />

Box hacked. :)
