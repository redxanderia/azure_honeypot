# azure_honeypot

**Introduction:**

For my first cybersecurity project, I set up a honeypot via Microsoft Azure.
A honeypot is a cybersecurity mechanism designed to lure attackers by mimicking a vulnerable system or network. It's essentially a trap set up to detect or study unauthorized access or malicious activity.

However, for this project specifically, I will only be looking through its logs after leaving the virtual machine open for a couple days and analyzing malicious IP addresses. I figured that this would be a great opportunity for me to get exposed to the cybersecurity world and see first hand how it would look like when attackers get involved in the tech world.

![cowrielog](https://github.com/redxanderia/azure_honeypot/assets/161082036/58d2231d-a04c-43fe-a08f-3cad27cffc77)
> Screenshot of an overview of my honeypot in Microsoft Azure.

**Overview:**

I used Microsoft Azure to create my honeypot virtual machine. It uses Linux OS, version: Ubuntu 20.04.6 LTS. By making my virtual machine vulnerable, I opened ports 80 and 22, and left it powered on for a couple days. I also installed cowrie to help attract attackers. Cowrie is a medium interaction SSH and Telnet honeypot designed to log brute force attacks and shell interaction performed by an attacker. 

**Log Details:**

After leaving my virtual machine on for a couple days, I entered the command `tail -f cowrie.log` to look at the logs and found a long list of unknown IP addresses. Please feel free to look at the logs in the attached files.

**Findings:**

I analyzed a couple of IP addresses that I found in the logs by using https://urlscan.io/. From the logs, I chose three to analyze.

`Mar 22 18:16:17 honeypot sshd[17028]: Invalid user test2 from 91.128.181.91 port 38196
Mar 22 18:16:17 honeypot sshd[17028]: error: maximum authentication attempts exceeded for invalid user test2 from 91.128.181.91 port 38196 ssh2 [preauth]`
* urlscan gave me results saying 'We could not scan this website!' with the error text: `net::ERR_CONNECTION_REFUSED`. This IP address was actually found more than 10 times trying to access my VM. However, there are many reasons why this error might've popped up. I figured that whoever was trying to access my VM unauthorized has a DNS issue or insecure TLS.

`Mar 22 19:39:15 honeypot sshd[24922]: Received disconnect from 122.114.28.225 port 46310:11: Bye Bye [preauth]
Mar 22 19:39:15 honeypot sshd[24922]: Disconnected from 122.114.28.225 port 46310 [preauth]`
* urlscan has found that this IP address is located in China. It looks like they were able to log into my VM briefly then disconnected.

`Mar 22 17:09:59 honeypot sshd[11620]: Invalid user ubuntu from 119.247.141.124 port 37382
Mar 22 17:10:00 honeypot sshd[11620]: error: maximum authentication attempts exceeded for invalid user ubuntu from 119.247.141.124 port 37382 ssh2 [preauth]
Mar 22 17:10:00 honeypot sshd[11620]: Disconnecting invalid user ubuntu 119.247.141.124 port 37382: Too many authentication failures [preauth]`
* urlscan has found that this IP address is located in Hong Kong. Similar to the first IP address I analyzed, this one had more than 50 attempts trying to log in as well. However, I noticed that they are trying multiple usernames to log in. For example, this one says user ubuntu. If you refer back to the logs, they've tried usernames admin, oracle, test1, many others.

**Summary:**

This project helped me to gain a better understanding of the world of cybersecurity. I got to experience first-hand how it looks like to get infiltrated by unauthorized users, as well as learning how to inspect the logs. Creating and observing a honeypot is only my first step into getting more skilled at becoming a cyber analyst.

**References:**

https://github.com/cowrie/cowrie
