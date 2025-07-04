# TryHackMe: SOC Simulator

### Overview:
Worked through a hands-on Security Operations Center (SOC) simulation to learn how to investigate alerts, respond to incidents, and think like a Tier 1 SOC analyst. I used Splunk to search logs, find suspicious activity, and connect the dots to figure out how attacks happened.
Key Skills Demonstrated: 
Investigated different alerts like suspicious logins and phishing emails.

Used Splunk to search for patterns, find indicators of compromise (IOCs), and trace attacker activity across systems.

Took notes on each case, including what happened, how I found it, and how it could be stopped.

Practiced working with a SOC-style alert queue, just like in a real security team.

---
### Process:

For this project, I focused on the Introduction to Phishing room. My objectives were:

Monitor and analyze alerts

Identify and document suspicious emails and attachments

Create a detailed case report for each alert to help the team understand the full scope of the threat

Each case report included whether the alert was a true positive or false positive, along with a reasoned decision on whether escalation was necessary.

---
### Alert 1: Inbound Email Containing Suspicious External Link (False Positive)
![yhgf](https://github.com/user-attachments/assets/d4747d08-9601-49d3-8c99-44eb5a462569)

The alert was triggered by a link within the email body, I can use the playbook provided to me to see what the next steps would be to analyze the alert.
![ghtb](https://github.com/user-attachments/assets/0fadcd24-bf62-477c-bb30-1dc160156b87)

The first step for phishing email analysis is to search up the sender's domain on TryDetectThis to detect if the domain is safe or malicious. TryDetectThis is an application much like VirusTotal or URLvoid.com.
![788766](https://github.com/user-attachments/assets/a5c405ff-77df-4f78-89f5-3f755b3b5cb1)

TryDetectThis has found this URL to be safe. The next step in the phishing playbook is to see if the sender has communicated with any other recipient and search logs to see if the firewall allowed or blocked access if the recipient clicked on the link.
![prog](https://github.com/user-attachments/assets/20b85835-9cd7-4b31-bf3f-95fc3680103f)

The sender has only communicated with J. Garcia on two seperate occasions, this shows signs that the sender's intentions are not malicious.
![uut](https://github.com/user-attachments/assets/50268f75-1ad8-4bab-a167-111b4da91b91)

There is no log that shows record of the firewall allowing or blocking access so it is assumed J. Garcia did not click on the link. I can put all the information I gathered and write a case report on a false positive alert.
![85969](https://github.com/user-attachments/assets/a521a433-f683-4c9d-b325-3a5b658057b2)

---
### Alert 2: Access to Blacklisted External URL Blocked By Firewall (True Positive)
Normally we would take care of the highest severity alerts first however this alert did not come up before starting the previous one.
![tghg](https://github.com/user-attachments/assets/35fde93f-13e1-4900-ae4c-9dbc6bacf352)

We can use the other playbook provided to us for suspicious outbound connection.
![image](https://github.com/user-attachments/assets/999dd43a-0391-4074-8052-6244e07ebc01)

Firewall logs show the source IP did attempt connection but the firewall was able to block it since the URL was on the block list.
![uy](https://github.com/user-attachments/assets/4bb6264b-e6cc-475e-ace4-3738452d4881)

Just to double check the status of the link we can go to TryDetectThis again and see that the link is in fact malicious.
![tdg](https://github.com/user-attachments/assets/77c154c8-aecf-4066-a804-6bb9cb8f93eb)

Through analyzation we can conclude the alert was a true positive but does not require escalation as the attempted connection was blocked.
![ygtg](https://github.com/user-attachments/assets/f38c0016-e38b-4d35-8c18-930ce2b33128)

---
### Alert 3: Inbound Email Containing Suspicious External Link (True Positive)
![hgh](https://github.com/user-attachments/assets/8d279f65-c178-4df9-9a06-b6b51a7967a9)

Using the playbooks discussed earlier I will check the URL for malicious intent, see if the sender has communicated with anyone else, and check firewall logs for allowed or blocked access.
![yu](https://github.com/user-attachments/assets/b2edbce9-141b-4e64-8a76-d10c5112d78f)
![yhh](https://github.com/user-attachments/assets/b8873423-0fad-4706-b052-39de1c663405)
![ytuh](https://github.com/user-attachments/assets/3f488bf3-6208-4425-9706-8bc4bf734014)

The URL was deemed malicious, the sender only communicated with C. Allen, and firewall logs show connection was allowed. This makes this alert a true positive and escalation is required as connection was successful, here is the full case report:
![utyf](https://github.com/user-attachments/assets/f627e6c3-b770-4956-a62c-7c042912f9f6)

---
### Alert 4: Inbound Email Containing Suspicious External Link (True Positive)
![tghh](https://github.com/user-attachments/assets/d910b460-bd04-4b15-8724-aa3d8c5f70fe)

If we look at the link this alert is actually a precursor to alert 2. The was the phishing email sent that caused H. Harris to click on the link. We already know the link is malicious and firewall blocked access so we are ready to write the case report.
![ytr](https://github.com/user-attachments/assets/12dc611f-695f-457c-870b-4e972b0a836d)

![tg](https://github.com/user-attachments/assets/aac048e7-1666-42c6-bd73-35d2da69cf17)
I found all the true positives in the alert queue and correctly assessed each one!

---
### Reflection
![yhf](https://github.com/user-attachments/assets/a24e9776-73ef-40cf-a936-edac2c55c3bc)

Reading through the analysis of my reports I have learned that I was able to detail key aspects in each element of the incidents but I need work on more clarification and more detail on the 5 W's, mostly in the 'When', and 'Why' aspects. This project helped me gauged how work for a real SOC analyst could look like and the need for detail and clarificaion in each case report. I will continue to work on areas I lack in to become the best SOC analyst I can.
