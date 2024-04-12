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

**Summary:**

I analyzed a couple of IP addresses that I found in the logs by using https://urlscan.io/.

**References:**

https://github.com/cowrie/cowrie
