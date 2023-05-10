# Splunk - BOSS OF THE SOCv3
<h2>Webserver & Compromised OneDrive Challenge</h2>

The past week I’ve been spending most of my time trying to complete a Splunk learning path to gain an understanding of different detection and incident handling approaches when it comes to various attack vectors. Today I will be completing two quick CTFs that I need to complete to finish the learning path. 

<h3>Webserver Challenge</h3>

I’m working for a brewing company that has had some trouble with malicious activity on their server. My first task is to gather information about the systems hardware, specifically the cpu.
<br>
<br>
Search string: <b>sourcetype=”hardware” cpu</b>
<br>
<br>
<img src="https://i.imgur.com/EkISr4D.jpg">
<br>
<br>
Now they would like me to search for the number of packages and dependencies that are installed by the EC2 instance cloud script when executed.
<br>
<br>
Search string: <b>sourcetype="cloud-init-output" packages</b>
<br>
<br>
<img src="https://i.imgur.com/8SVhVhl.jpg">
<br>
<br>
The organization has been having some trouble with brute force attacks against its webserver.  They want me to find the source IP and the country of origin using the iplocations function. (This function was not working, so I had to use outside OSINT sources)
<br>
<br>
Search string: <b>sourcetype=linux_secure "Failed password" OR "Invalid user"</b>
<br>
<br>
That was a very simple challenge, on to the next! 
<br>
<br>
<h3>Compromised OneDrive Challenge</h3>
<br>
In this challenge, a group of North Korean hackers have compromised the brewing companies Microsoft OneDrive and it is my duty to thwart their nefarious activities. My first task is to locate a malicious file that was uploaded to the organization's OneDrive account.
<br>
<br>
Search string: <b>sourcetype="*o365*" .lnk</b>
<br>
<br>
<img src="https://i.imgur.com/OTJl2DF.jpg">
<br>
We’ve located the .lnk file, but we need to know how many unique user IP addresses had access to the file? 
<br>
<br>
Search string: <b>sourcetype="*o365*" *.lnk  Operation=AnonymousLinkUsed ClientIP="*"</b>
<br>
<br>
The file was quarantined by the AV, but not before multiple hosts were compromised. Find the hosts that were affected. 
<br>
<br>
Search string: <b>sourcetype="WinEventLog:Application" *.lnk</b>
<br>
<br>
<img src="https://i.imgur.com/EGQxpAe.jpg">
<br>
That’s a wrap for now. These were very easy, but practice makes perfect, and I was able to breeze through them in a few minutes. I have 3 more Splunk CTFs to finish that will wrap up the Splunk learning path that I've been working on. Until next time! 




























