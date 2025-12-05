# Meow
 Source: https://app.hackthebox.com/machines/Meow

## Enumeration

To test the connection to the target, I started with a `ping -c4 <TARGET_IP>` command which successfully got a response.

<img width="997" height="339" alt="image" src="https://github.com/user-attachments/assets/7416b50d-b8ce-4473-b43b-0bbdc4d2a309" />


Great! Now let's see what's running on the machine to get a general understanding of the open ports and running services with `nmap -sV <TARGET_IP>`.

<img width="1010" height="403" alt="image" src="https://github.com/user-attachments/assets/4c6296e6-82ee-4546-888b-33dd19fe2df7" />


Well, it looks like there's only one port open: 23, which runs `telnet`.

A quick Internet search told me that `telnet` is <a href="https://phoenixnap.com/kb/telnet-windows">"a network protocol for two-way text-based communication through a CLI, allowing remote access"</a>. It is also supposedly vulnerable to attacks of its lack of encryption methods. Being the only open port, it seems this is the way forward.

## Foothold

Running `telnet` in the Terminal and looking for a `help` manual suggested that the `open` command is used to connect a target.

<img width="877" height="650" alt="image" src="https://github.com/user-attachments/assets/62679a9b-12c0-4443-88b9-af5b47213760" />


But, of course, the connection required a login which wasn't suggested elsewhere. At this point, I could hope that the service was poorly configured. I tried logging in with `admin`, with no luck, followed by `root`. Looks like we got lucky! There was no password set.

<img width="631" height="671" alt="image" src="https://github.com/user-attachments/assets/03d6fcfe-b583-4a82-8398-198e05b3c972" />


Using `ls`, I could see what was on the system, and lo and behold, sitting right there is a `flag.txt` file!

<img width="547" height="129" alt="image" src="https://github.com/user-attachments/assets/5db97e15-2fc8-4465-9880-f264c1d4140e" />


Box hacked. :)
