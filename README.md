## Linux-admin_labs
Click the :penguin: to do the exercises
<!--
| Command| Description |Example |
|------|---------------|--------|
|      |               |        |
|      |               |        |
<details><summary>:penguin: </summary>

```

   
```
</details>

**************************************
--->
<details><summary>:penguin: SSH , process, multi user access</summary>

```
It’s time to begin reconnaissance on your teammate, agent Rene Mathis. DO NOT VIEW OR LOG INTO LINUX2 LOCALLY. Linux2 is Mathis’ desktop computer, looking over his shoulder to watch his screen or sitting down and logging into it would raise his suspicions. If he is the accomplice, we need to know what he’s been up to since returning to HQ. Agent Gregg Beam will be standing by to detain him in the event that you find any damning evidence.
 This continues from Linux Lab 1C Phase 1. Log into Linux1 with your personal “student” account.
 By default, where does a Linux computer store the credentials for its users: locally, on the domain, somewhere else?
o Does Linux2 have a “student” user account?
o From Linux1, what’s the full command (with arguments) you would use to remotely SSH into Linux2?

o Try SSH’ing into Linux2 as that account. Did it work?
  If not, what is the error basically indicating?
 Find a way to SSH into Linux2 without using the topology button.
 Once inside, run a command that’ll display which accounts are currently logged into
Linux2. Record their names and whether they’re logged in locally or remotely:
 Has Mathis attached any additional storage drives onto Linux2? If so, how much total space does each drive have and has he partitioned any of them? Have any of them been mounted?
o From the administrator’s home directory on Linux2, see if you are able to view their contents without changing your working directory. What command did you use to accomplish this?
o What are the names and types of files in there?
 Agent Gregg Beam is observing Mathis from his cubicle. He’s just reported seeing Mathis remove a CD from Linux2, but Gregg’s desk is a few cubicles away and he’s not sure if it’s the same CD we seized during the takedown in France. Check Mathis’ home directory, what files does he have in there?
 Agent Beam sent an update: apparently he can hear the CPU fans of Linux2 all the way from his desk. Use a command to view which programs Mathis are currently running on Linux2 in real-time. Are there any processes that are consuming more than 10% of his CPU resources on Linux2?
        
o If so, what is the name and PID of its parent process of those processes?
  Chief Mallory:
“Agent Beam walked over to Fiona Mactaggart’s desk and caught a glimpse of
Mathis’ CD while chatting with her. He says it’s definitely the one from the takedown in France. We can’t afford to wait any longer. Revoke all of Mathis’ computer privileges on Linux2 NOW.”
o Once agent Beam starts heading towards Mathis, he’s going to sense what’s about to happen. You’re going to need a plan to accomplish the following things without giving Mathis time to react and start deleting evidence:
 Remove Mathis’ sudo privileges on Linux2.
 Disable Mathis account on Linux2 to prevent him from logging in.
 Force Mathis to log out of Linux2.
 Which of these things will Mathis not be aware of initially and which of
these things will Mathis be aware of immediately or very quickly?
 Create a plan with the necessary actions needed to accomplish all three of these tasks in a very short amount of time.
 How are you going to disable Mathis’ account?
 Does disabling an account immediately force the user to log out of the Linux system?
 When do changes to a user’s group memberships come into effect: when you make the change or when the user logs back into Linux2:
 Regarding how you’re going to kick Mathis off his own computer, when a user logs into a Linux system, a process is created that corresponds to the user being logged in. If you kill that process, the user will be logged out immediately. Use the command top to view all currently running processes (aka programs) on Linux2, then press h to view the help and figure out how to filter to see only processes Mathis is running. What’s the PID for the process
    
that corresponds to Mathis being logged into the CLI?
 o When you’re ready, carry out your plan!
o Agent Gregg Beam reports that Mathis has successfully been detained and
handed over to security. You now have permission to walk over to Mathis’ desk (in other words, using the topology tab).
 Go ahead and verify that Mathis’ account can no longer authenticate into Linux2. Can Mathis log into Linux2 at this point?
o What was the name of the process that was taking up more than 10% of Linux2’s CPU resources earlier?
 Use a command to view real-time processes. Is that process still running?
 If so kill the process and verify it is no longer running.
    
   
```
</details>


<details><summary>:penguin: Disk Management</summary>

```
Chief Mallory has called you into his office. The Ministry of Intelligence has faced significant setbacks lately: one agent KIA’ed after turning on his teammates, the prolific arms smuggler LeChiffre on the run...and then there’s Rene Mathis.
As the team’s field technician, his skills were crucial to the operation’s success, but someone on the team tipped off LeChiffre. We have to know who. You need to do some quiet digging, determine whether Mathis and Tom Mitchell were working together to help LeChiffre and preserve the evidence before Rene Mathis can cover his tracks.
 If Mathis is up to something, you’ll be up against someone with almost as much I.T. privileges as yourself. Let’s see what hardware resources you’ve got at your disposal on Linux1.
o You’ve used the LS command to list the contents of a folder, now it’s time to use a similar command to list information on your CPU. Figure out which type of CPU Linux1 has: Intel, AMD, Arm? Also, what GHz is your CPU running at?
o Let’s go deeper with the CPU and find its exact product name (which starts with an “X” followed by four numbers). What command did you use to get that

information?
 o A CD-ROM was seized as evidence during the takedown operation in France and its contents will need to be analyzed on Linux1. Does Linux1 have a CD ROM drive? What command did you use to figure that out?
o Does Linux1 have any unused storage devices with at least 400 MB of space? If so, what’s the name of their device file?
o Time to find out whether Linux1 has any SSDs on it.
 You’ve learned about a type of LS command that’ll list block devices (aka
storage devices). Check out the help for that command – by using the man command with it. Which option will allow you to choose the columns of information that it prints out?
 Linux tracks whether each of its storage devices is a platter drive (aka hard drive) or an SSD, but it does this in an interesting way. Think about it this way, does the circular platter do inside a hard drive: does it stay still or does it rotate?
 The option you found for lsblk will allow you to specify multiple columns you want to see together. All you have to do is separate the column names with commas (for example: column1,column2,column3). Use the option for lsblk to print the name, type, and size columns for each block device on Linux1.
 Now use --help with lsblk to figure out which additional column you could add to the output to identify the SSD drives on Linux1. Which column was it?
o Create a folder called evidence-storage in the root directory. In other words, the folder’s absolute path should be /evidence-storage
 Make sure your account is the user and group owner on this folder.
     
o Choose one of the storage drives on Linux1 with at least 400 MB of available space (We’ll save the remaining free storage drive as a contingency).
 Create a partition with all the available space on that drive. Once you’ve created a new partition, how do you check to make sure the partition is the correct size before saving your changes to the partition table?
 Is the partition you made on a HDD (Hard Disk Drive) or an SSD? Based on that, what would be the best filesystem to format the partition as?
 What are the two commands you could use to format the partition? Choose one and use it to format your partition!
 Finally, mount your new partition onto /evidence-storage and ensure the partition will be mounted whenever the computer boots up. How did you accomplish the second part of this objective?
 Set the user and group owners on that folder to be the student account. Change permissions on that folder so that the user and group owner have read, write, execute and everyone else has no permission.
o It’s not clear what you’ll encounter while investigating Mathis. You’re going to create some test files for target practice. At the top of your personal home directory, create a folder called target-practice. Inside of it create the following:
 A text file called identify-me1.txt. Add the following text to it and save it:  Hello there world!
 A file called identify-me2, add the following text and save it:  Hello, can you read this?
 A file called identify-me3.txt with this exact text:  #!/bin/bash
 A folder called identify-me4.txt
o The file command allows you to identify an object’s type. Let’s get some
practice on the range:
 In the target-practice folder, what does the file command say identify-
me4.txt is?
     
 Of the four “identify-me” objects you made, which does the file command identify as plain “ASCII text” files?
 What type of file is identify-me3.txt?
 Does putting a .txt or .doc or .jpeg at the end of a file name actually convert that file to a text file or an image file?
```
</details>

<details><summary>:penguin: File permission and user management access</summary>

```
After a fairly successful operation in France, and with most of the targets in custody awaiting interrogation, it’s time to examine the one glaring detail.
Chief Mallory:
I want to start by saying that our counterparts at the CIA are incredibly pleased. The moment we saw the blueprints, everyone knew that casino was going to be an operational nightmare. Capturing four of the five targets without incident is a huge win. At the same time, we cannot afford to ignore the obvious. Somehow LeChiffre managed to slip away.
Agent Beam has finished re-­­qualifying and has been cleared for active field work once more. As you and he were both at HQ during the ground team’s operation in Nice, it was fairly easy to verify your movements and actions that day. You’ve both been cleared of suspicion. I need you and he to start working together on something delicate. Ms Vesper Lind from the Treasury Department came to me and accused agent Rene Mathis of fouling up the mission.
We’ve been unable to verify where Mathis was just prior to the CIA takedown. Mathis’ own mission report fails to give any details about it, though he does mention clumsily locking his user own account out of
 
Linux1 the night before the poker tournament. If that’s true, then Mathis wouldn’t have been able to log in, but I can’t see how else Le Chiffre could have known which exit to slip out through. No one has touched that system since the investigation started. I need you to confirm the validity of these statements.
 Confirm the status of the rmathis account on Linux1. Is it locked out? o Justify your determination by explaining how a sys-admin can
tell whether an account is enabled, disabled, or locked?
 What secondary groups is Mathis’ account a member of?
 Could the rmathis account have reached the location of the
takedown-names.txt file?
 What permission to takedown-names.txt file does the rmathis account have currently? Are any special permission bits set?
 What command will let you substitute your user account for Mathis’?
 Use that command to test his level of access to the takedown file.
 Is there ANY possible way Mathis might have been able to read the takedown file? Why or why not?
                                  
```
</details>

<details><summary>:penguin: File permission & access</summary>

```
The mystery of Mitchell’s accomplice will have to wait. Your team has been given the green light to launch the operation. While the agents attend briefings and prep their kit, you’ve been tasked with setting up the necessary file and directory structure to support the team’s efforts in the town of Nice (pronounced “niece”) in France.
Objectives
 This lab continues from 1BP1. Log into Linux1 with your student account you made in
phase 1.
 In your personal home directory, create a folder and name it after the country where
this operation will take place (use lowercase letters).
o Now create a subdirectory inside of that folder named after the town (lowercase
letters, agent!).
 Inside the town’s directory, create three directories representing the following key
locations:
o garibaldiSquare o atlasMontBank o casinoRoyale
 Inside of the atlasMontBank directory, create a file called treasury-note.txt that contains a very brief summary of the Secretary’s instructions. Do not waste hard drive space by
 
coping the entire message into the file, just get the key details he wants recorded. Your file should only have three short lines of text.
o Note from the Treasury secretary Patrick Waldegrave:
 Chief Mallory has telephoned me to say the operation in Nice is on. Ms.
Vesper Lind and I have worked out a reasonable allocation of operational funds. I need you to make a note so the team will have a record of the key details. To start, we’ve transferred a sum of $10,000,000 in US currency into account ID 0CN55. To ensure proper handling, we’re sending one of our treasury agents, Ms. Lind, to accompany your field agents and observe the match. The funds in 0CN55 should cover the initial buy-in, but Ms. Lind has been authorized to provide access to a contingency fund of $5,000,000 in account HJZT8 for buying back in. Your undercover chap Mr. Beach assures me this is entirely unnecessary. I sincerely hope so...Good hunting!
o Make the following ownership and permission changes to the file with the treasury secretary’s instructions:
 User Owner: Vesper Lind
 User Owner Permission: read, write, execute
 Group Owner: treasury
 Group Owner Permission: read, write
 Everyone Permission: read
 What would these permissions look like if you set them in octal?
o What is the parent folder of treasury-note.txt?
 Configure that folder so that your student account is the user owner and the group owner is the Treasury group. What was the command and parameters that you used?
 Ensure the Treasury Department’s staff are able to create, rename and delete files in this folder. The others/everyone should only be able to enter the folder and see its contents.
 Which object did you edit the permissions of?
 What permissions did you set on it?
     
 Summarize these permissions into octal:
  Inside the casinoRoyale directory, setup a sub‐directory to hold intelligence briefs on the card players. Call it highStakesMatch.
o Inside highStakesMatch, create a directory called players.
 Inside the players directory, create text files with info for each of the
following individuals:  mrBeach.txt
o Name: Arlington Beach
o Affiliation: MI6
o Description: undercover, will not be armed
 mrFontaine.txt
o Name: Mr Fontaine
o Affiliation: Clerkenwell Crime Syndicate
o Description: UK Based, has a small presence in Ireland  mrTomelli.txt
o Name: Mr Tomelli
o Affiliation: La Stidda
o Description: Sicilian Mafia
 madameWu.txt
o Name: Madame Wu
o Affiliation: 14K Tai Huen Chai
o Description: offshoot of the Chinese Triad  mrLeiter.txt
o Name: Felix Leiter
o Affiliation: CIA
o Description: deep cover, will not be armed
 mrFukutu.txt
o Name: Mr Fukutu
o Affiliation: Inagawa-Kai
o Description: Yakuza based in the Japanese Kanto region  leChiffre.txt
o Name: Le Chiffre
o Affiliation: Le Milieu Corso‐Marseillais
o Description: Human Slave Traffickers working out of
Marseille
 The CIA and MI6 are planning to apprehend the targets immediately after the
tournament, but with undercover agents and scumbags listed together in the players directory, we need to get a list that contains only the names of criminals.
o Create an empty text file called takedown-names.txt and in the players directory.

o Come up with a command and a glob pattern that would catch Mr Tomelli’s and Madame Wu’s files and write it down below:
 Once you’ve got it working, redirect the output from this command into the takedown-names.txt file.
o Similar objective, this time the glob pattern must catch only Mr Fontaine’s and Mr Fukutu’s file names.
 Once you’ve got it working, redirect the output into the takedown- names.txt file.
o Confirm that you have the file names for all the criminal bosses listed in your takedown-names.txt file. Add any that are missing.
o Once the takedown file has been created and the target names added to it, it’s time to hand the file off to our friends at the CIA. Make the following ownership and permission changes to the takedown file to ensure the CIA are the only ones with access to it:
 User Owner: Felix Leiter
 User Owner: Permission: read, write, execute
 Group Owner: cia
 Group Owner Permission: read
 Everyone Permissions: none.
 Summarize these permissions into three octal digits:
 Ms Lind has sent a crucial update on the team’s progress. In the highStakesMatch folder, create a text file called mission-updates.txt with the following update:
o Update: Agent Beach’s identity may have been compromised
o Use a command to append the text from the mission-updates.txt file into Agent
Beach’s file in the players directory. Write down the command you used to accomplish this:
 Agent Gisela Stuart believes the permissions for the takedown file allow non-CIA agents to read the contents of the file. Without logging out of Linux1 as your student account, what command will allow you to instantly become another user?
o Use that command to become a non-CIA user and test whether they can read the takedown file. Record the username you became and whether or not they were able to view the contents of the takedown file.
     
 Agent Mathis wants to see if he can tap into the cameras on the Casino Royale’s network. He’s considering using the softeware package nmap and wants to know if Linux1 already has that installed. What command can you use to view currently installed packages on a Linux system?
o Is the nmap package installed on Linux1?
o What command can you use to check if nmap is available on the Officeial Debian repository?
o Let’s get some specific information on nmap. What version of nmap is available on the Debian repository?
 Agent Bill Tanner reports that he changed his working directory to the atlasMontBank folder but was unable to view the Treasury Secretary’s message when he ran the following command: cat treasury-Note.text
o Why was Agent Tanner not able to view the file’s contents?
     
```
</details>


<details><summary>:penguin: File permissions </summary>

```
The mystery of Mitchell’s accomplice will have to wait. Your team has been given the green light to launch the operation. While the agents attend briefings and prep their kit, you’ve been tasked with setting up the necessary file and directory structure to support the team’s efforts in the town of Nice (pronounced “niece”) in France.
Objectives
 This lab continues from 1BP1. Log into Linux1 with your student account you made in
phase 1.
 In your personal home directory, create a folder and name it after the country where
this operation will take place (use lowercase letters).
o Now create a subdirectory inside of that folder named after the town (lowercase
letters, agent!).
 Inside the town’s directory, create three directories representing the following key
locations:
o garibaldiSquare o atlasMontBank o casinoRoyale
 Inside of the atlasMontBank directory, create a file called treasury-note.txt that contains a very brief summary of the Secretary’s instructions. Do not waste hard drive space by coping the entire message into the file, just get the key details he wants recorded. Your file should only have three short lines of text.
o Note from the Treasury secretary Patrick Waldegrave:
 Chief Mallory has telephoned me to say the operation in Nice is on. Ms.
Vesper Lind and I have worked out a reasonable allocation of operational funds. I need you to make a note so the team will have a record of the key details. To start, we’ve transferred a sum of $10,000,000 in US currency into account ID 0CN55. To ensure proper handling, we’re sending one of our treasury agents, Ms. Lind, to accompany your field agents and observe the match. The funds in 0CN55 should cover the initial buy-in, but Ms. Lind has been authorized to provide access to a contingency fund of $5,000,000 in account HJZT8 for buying back in. Your undercover chap Mr. Beach assures me this is entirely unnecessary. I sincerely hope so...Good hunting!
o Make the following ownership and permission changes to the file with the treasury secretary’s instructions:
 User Owner: Vesper Lind
 User Owner Permission: read, write, execute
 Group Owner: treasury
 Group Owner Permission: read, write
 Everyone Permission: read
 What would these permissions look like if you set them in octal?
o What is the parent folder of treasury-note.txt?
 Configure that folder so that your student account is the user owner and the group owner is the Treasury group. What was the command and parameters that you used?
 Ensure the Treasury Department’s staff are able to create, rename and delete files in this folder. The others/everyone should only be able to enter the folder and see its contents.
 Which object did you edit the permissions of?
 What permissions did you set on it?
    
 Summarize these permissions into octal:
  Inside the casinoRoyale directory, setup a sub‐directory to hold intelligence briefs on the card players. Call it highStakesMatch.
o Inside highStakesMatch, create a directory called players.
 Inside the players directory, create text files with info for each of the
following individuals:  mrBeach.txt
o Name: Arlington Beach
o Affiliation: MI6
o Description: undercover, will not be armed
 mrFontaine.txt
o Name: Mr Fontaine
o Affiliation: Clerkenwell Crime Syndicate
o Description: UK Based, has a small presence in Ireland  mrTomelli.txt
o Name: Mr Tomelli
o Affiliation: La Stidda
o Description: Sicilian Mafia
 madameWu.txt
o Name: Madame Wu
o Affiliation: 14K Tai Huen Chai
o Description: offshoot of the Chinese Triad  mrLeiter.txt
o Name: Felix Leiter
o Affiliation: CIA
o Description: deep cover, will not be armed
 mrFukutu.txt
o Name: Mr Fukutu
o Affiliation: Inagawa-Kai
o Description: Yakuza based in the Japanese Kanto region  leChiffre.txt
o Name: Le Chiffre
o Affiliation: Le Milieu Corso‐Marseillais
o Description: Human Slave Traffickers working out of
Marseille
 The CIA and MI6 are planning to apprehend the targets immediately after the
tournament, but with undercover agents and scumbags listed together in the players directory, we need to get a list that contains only the names of criminals.
o Create an empty text file called takedown-names.txt and in the players directory.

o Come up with a command and a glob pattern that would catch Mr Tomelli’s and Madame Wu’s files and write it down below:
 Once you’ve got it working, redirect the output from this command into the takedown-names.txt file.
o Similar objective, this time the glob pattern must catch only Mr Fontaine’s and Mr Fukutu’s file names.
 Once you’ve got it working, redirect the output into the takedown- names.txt file.
o Confirm that you have the file names for all the criminal bosses listed in your takedown-names.txt file. Add any that are missing.
o Once the takedown file has been created and the target names added to it, it’s time to hand the file off to our friends at the CIA. Make the following ownership and permission changes to the takedown file to ensure the CIA are the only ones with access to it:
 User Owner: Felix Leiter
 User Owner: Permission: read, write, execute
 Group Owner: cia
 Group Owner Permission: read
 Everyone Permissions: none.
 Summarize these permissions into three octal digits:
 Ms Lind has sent a crucial update on the team’s progress. In the highStakesMatch folder, create a text file called mission-updates.txt with the following update:
o Update: Agent Beach’s identity may have been compromised
o Use a command to append the text from the mission-updates.txt file into Agent
Beach’s file in the players directory. Write down the command you used to accomplish this:
 Agent Gisela Stuart believes the permissions for the takedown file allow non-CIA agents to read the contents of the file. Without logging out of Linux1 as your student account, what command will allow you to instantly become another user?
o Use that command to become a non-CIA user and test whether they can read the takedown file. Record the username you became and whether or not they were able to view the contents of the takedown file.
     
 Agent Mathis wants to see if he can tap into the cameras on the Casino Royale’s network. He’s considering using the softeware package nmap and wants to know if Linux1 already has that installed. What command can you use to view currently installed packages on a Linux system?
o Is the nmap package installed on Linux1?
o What command can you use to check if nmap is available on the Officeial Debian repository?
o Let’s get some specific information on nmap. What version of nmap is available on the Debian repository?
 Agent Bill Tanner reports that he changed his working directory to the atlasMontBank folder but was unable to view the Treasury Secretary’s message when he ran the following command: cat treasury-Note.text
o Why was Agent Tanner not able to view the file’s contents?
     

```
</details>


<details><summary>:penguin: Group account management </summary>

```
Agent Gregg Beam has been found innocent, the identity of Mitchell’s true accomplice is still unknown, and MI6 has formed a joint task force with GCHQ and the CIA. While agent Beam undergoes fitness tests and marksmanship re-qualifications, your department has been forging ahead with the next operation in France. For your part, you’ll be preparing Linux1 for deployment in the field with the team.
 Log into Linux1 with the default administrator account and create your own personal “student” account. Add it to the necessary group so that you have super user privileges.
o What was the name of the group you added your student account to?
 Use a command to print the contents of the file /etc/group onto the screen. o Write down the command you used:
o There are two categories of user groups in Linux. What’s the category of group that gets named after a specific user account and gets listed as the “group
owner” on any files or folders they create?
 Add the following user accounts with the standard password (secretPassword) on Linux1: o Arlington Beach
 Username: abeach o Vesper Lind
 Username: vlind o Rene Mathis
 Username: rmathis (give Mathis super user privileges on Linux1 too) o Gareth Mallory
 Username: gmallory o Fiona Mactaggart
 Username: fmactaggart o Bill Tanner
 Username: btanner o Patrick Waldegrave
 Username: pwaldegrave o Gisela Stuart
 Username: gstuart o Felix Leiter
 Username: fleiter
 Create the following groups on Linux1:
o MI6
 Group Name: mi6
 Members: Mr Beach, Mr Mallory o MI6 – Information Systems Technicians
 Group Name: mi6-ist
 Members: Rene Mathis, Student o MI5
 Group Name: mi5
 Members: Fiona Mactaggart, Bill Tanner o Treasury
 Group Name: treasury
 Members: Vesper Lind, Patrick Waldegrave o CIA
 Group Name: cia
 Members: Felix Leiter, Gisela Stuart
 Use the cat command to print the contents of the file /etc/group onto the screen. Write
down the name of a secondary group you see in the output from /etc/group:
```
</details>



<details><summary>:penguin: System login access</summary>


```
After the close call in Italy with the double agent Tom Mitchell, section chief Gareth Mallory has requested the following changes:
“We have reason to believe that Mitchell wasn’t working alone – we think it might be agent Gregg Beam. Until we can complete our investigation, I need you to disable both of their accounts.”
 What file holds all user accounts on a Linux system? What is the absolute path to reach that file?
 When editing that file, how does a sys-­­admin set a user account to be disabled?
 Most Linux users who do their work through the command line use the Bash shell. Looking at the entry for your user account, what shell are you using? Was Mitchell using the same as well?

 Do you think a user would be able to log into the Linux CLI if they didn’t have a shell assigned to them?
• Your team mate Rene Mathis wants to run a quick test to see if that’s true. Try setting his account’s shell to be /bin/rubbish and then see if his account is able to log into Linux1.
 The Chief has asked you to set the password on Mitchell’s account to Cantgetin00. While logged into Linux1 as the administrator account, what command would allow you to do that for another user’s account?
   
```
</details>

<details><summary>:penguin: File management </summary>

```
The art of physical surveillance can take years to master, but honing the ability to pick out just the right European-cut black leather coat is one of several skills that allow our field agents to fit in anywhere in the world. But for the team’s next operation in Siena, the last walled town in Italy, blending in will be easy.
The day of the operation has been picked to coincide with Siena’s annual Palio, a medieval horse race that draws enormous crowds from the entire province. You’ve been given authorization to continue using the “administrator” credentials on Linux1 that Mathis created for you.
Objectives:
 Inside the “administrator” account’s personal home directory, create a folder using the name of the town where the team will be deployed to. Use all lowercase letters.
 What is the absolute path to folder with the town’s name?
     
 Inside the town’s directory, make three new sub-directories:
o evals
o palio
o targets
 In the evals directory, create files named after the team members’ accounts
and with their name, affiliation, role, and height for each team member:
o tMitchell.txt
• Name: Tom Mitchell
• Affiliation: MI6
• Role: Field Agent
• Height: 5’11”
o cMontes.txt
• Name: Camille Montes
• Affiliation: Bolivian Intelligence and Security
• Role: Field Agent
• Height: 5’7”
o gBeam.txt
• Name: Gregg Beam
• Affiliation: MI6
• Role: Field Agent
• Height: 6’1”
o sFields.txt
• Name: Sarah Fields
• Affiliation: MI6
• Role: Counter Intelligence Analyst
• Height: 5’5”
o rMathis.txt
• Name: Rene Mathis
• Affiliation: MI6
• Role: IT Field Support
• Height: 5’9”
 Inside the palio directory, create the following subdirectories:
o fieldReports
o talamone
o teamMembers
 Under talamone, create a text file called shippingManifest.txt. Read the
Quartermaster’s message and summarize it into three short lines of text. After each line, use the enter key to drop down to the next line. Do not waste hard drive space by copying the entire message into the file. Imagine you are writing this on a tiny sticky note.
Note from the Quartermaster: “Several items need updating. Would you mind terribly adding a note about the updated shipping manifest? Item number 13 is still the E-­­K-­­G machine you requested. Medical requested we switch to the latest model, that’s what’s on the shipment now. Mathis informed me he wasn’t able to get Item 7 ready in time, so just add a line

in to the file about that and make sure the OPS team gets the message. And last, but not least, we managed to get item number 22 approved at the last moment. The trick was finding someone trustworthy to gas-up the Aston Martin. It should be waiting for the team when they arrive. Cheers.”
 Inside the targets directory, create the following files and fields of info inside the files. Do not include extensions in the file names.
o dGreene
• Name: Dominic Greene
• Note: possibly already being surveilled by the CIA, agent Gregg Beam will reach out to Felix Leiter for confirmation
o white
• Name: Mr White
• Note: full name unknown at this point o Medrano
• Name: General Medrano
• Note: agent Montes is working with her section chief in
Bolivian Intelligence to verify this individual’s identity o fGuillen
• Name: Colonel Fernando Guillen
• Note: appears to have previous ties to General Medrano, but
agent Montes believes they have only recently begun working
together
 In the “administrator” account’s personal home directory, make a folder
called italy.
 What command is used to move a file or folder? Write the command you
would use to move the siena folder and all of its contents, into the italy folder:
o Does that command have a –r option for recursion?
o When you’re sure you’ve got the right command and the right paths, run it and see what happens.
o Were the siena folder and all its contents were also moved over correctly?
o Did you have to add any extra options with your command?
                    
 Log into WKS01 with the domain “student” account and use the Paint application to NEATLY draw the hierarchy of all the files and folders you’ve created. Start from the italy folder and work your way down. Make sure your capitalization matches the way the names of the folders and files appear in the system. You do not need to write down the contents of files, but your hierarchy diagram should make it clear which folder they’re in. Show the hierarchy to your instructor before moving on! See below for an example.
o Example:
 Change your working directory to /home/administrator/italy/siena. From
this location, what’s the name of the folder you’re inside of?
 Write down the absolute path to your current working directory.
 Starting at /home/administrator/italy/siena, use a relative path to change your working directory to the palio directory. Write down the full command you used.
 Ensure your working directory is the palio folder, use another relative path to change your working directory to the evals folder. Write down the full command that you used.
 The night shift agents need to be able to go into the teamMembers folder and see the same agent files that are in the evals directory. To accomplish this, you’re going to replace the teamMembers directory with a type of link.
o First, check the teamMembers directory to make sure that it is empty (or at least, make sure it has nothing of value in it). Once you’ve done that, delete that directory.
o Now, the new link you create should be inside the same directory where the old teamMembers folder used to be. Your new link should be called teamMembers and it should target the evals folder.
o Write down the command you used to make the teamMembers link.
o What type of link did you create: a hard link or symbolic link?
o If your links target gets renamed or moved to a different directory, will
your link still work?
o How does your link point to its target, by the target’s inode number or by a path?
o Time to use your new teamMembers link! Change your working directory to the teamMembers link and add the following text to Tom Mitchell’s agent evaluation file:
• Status Report: Tom Mitchell confirmed KIA (double agent). Section chief Gareth Mallory has been informed and will begin an investigation shortly.
 Your fellow IT Rene Mathis has suggested you should delete the teamMembers link and recreate it, using a type of link that would continue working, even if the evals directory gets moved to another location. What kind of link is Mathis talking about? Is this a good idea? Why or why not?  Use a command to display all the files in teamMembers that end with the letter s. Write down the full command and glob pattern you used.
    
 Use a command to display all files in teamMembers whose second letter is an M. Write down the full command and glob pattern that you used.
 Use a command to display the files in targets directory with the fifth letter e. Write down the full command and glob pattern that you used.
 What command and glob pattern will list the files in the teamMembers directory that have an M and then a t at some point after that in their filename?
 Continuing from the last objective, what command would you use if we only want the agents whose names have an M and then an i separated by none, one or more characters?
 What’s the difference between the wildcards ? and *
   ```                                

</details>
<details><summary>:penguin: User management</summary>

```
It is the 21st Century and humankind is once again in conflict.
Hack-tivists, black-hats and nation-state spies prowl the internet, exploiting the mistakes of sloppy System Administrators. What’s more, the cyber-criminals of today are forging increasingly closer ties with organized crime. That’s where you come in.
You and your fellow agents at MI6, the British equivalent of the CIA, are preparing to launch a series of operations in Europe. Your first priority is to prepare Linux1 for deployment in the field.
 MI6 has an agency policy that all Linux systems must have an account called “administrator” that has super user privileges. Your IT teammate, agent Rene Mathis, has already taken care of creating this account on Linux1 and Linux2.
o Log into Linux1 with the “administrator” account.
o Password: standard password used in the course.
 Create the following accounts using the initial of the agent’s first name
and then their full last name in all lower-case letters (ex: Joe Smith -> jsmith):
o Rene Mathis
o Felix Leiter
o Camille Montes o Bill Tanner
 
o Gregg Beam
o Tom Mitchell
 Windows admins use the term “folder”, but Linux admins frequently use the term “directory”. Is there a difference between a “folder” and a “directory”?
 In a Linux system, the Root Directory is the folder that contains everything else on that system. Unlike other Linux folders, it doesn’t have a name with letters or numbers. Instead, it’s represented by a single symbol. What symbol is used on Linux to represent the Root Directory?
(Hint: it’s one of the symbols you can type on your keyboard.)
 Give a detailed explanation on the difference between an absolute and a relative path on Linux and include an example of each type of path. How are these similar to absolute and relative paths on Windows?
 What is the absolute path to the file that stores all user accounts on a Linux system?
o Does that file have a file extension in its name (like .txt or .doc or .conf)?
          
 On Linux, each user has their own personal home directory. What is the absolute path to Tom Mitchell’s personal home directory on Linux1?
 Imagine if a new user account rsilva were created for Mr Raoul Silva (but don’t actually make one). What do you think would be the absolute path to Mr. Silva’s home directory?
 What’s the immediate parent directory of Tom’s, Gregg’s and the rest of the team’s personal home directories? Write down the absolute path to that directory.
 A skilled Linux user must be able to discern files from folders in a heartbeat. Which options for the ls command gives you the information to determine whether an object in Linux is a file or folder?
Time to sharpen your skills.
 In the administrator account’s personal home directory, make a directory called burkinaFaso. What was the command you used to make it?
 Now make a folder called slovakia.txt. What was the command you used this time?
 Finally, create a text file called montserrat. (Don’t worry about putting any text in it, though you can if you want to.) There are several ways to create a text file on Linux, which method did you use?
                                   
 Earlier you wrote down an option for the ls command that would help you identify files from folders. Using that option, which of the three objects you just made are files and which are directories from your Linux system’s perspective:
 Does Linux require file names to have an extension (like .txt, .doc, .jpg)?
o Try renaming burkinaFaso to burkinaFaso.txt.
o Now try opening that folder with the nano command. What
message does nano give you at the bottom of the screen?
o When you changed the directory’s name, did you change the type of object it is?
• What command can you use to confirm your theory?
 ```                       
</details>

