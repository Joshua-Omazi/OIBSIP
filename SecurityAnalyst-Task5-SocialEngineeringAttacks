# Social Engineering Attacks: A Research Report

*October 2026*

## Table of Contents

1. [Introduction](#1-introduction)
2. [Phishing](#2-phishing)
3. [Pretexting](#3-pretexting)
4. [Baiting](#4-baiting)
5. [Quid Pro Quo (Bonus)](#5-quid-pro-quo-bonus)
6. [Comparison of the Attacks](#6-comparison-of-the-attacks)
7. [Employee Security Awareness Training: A 5-Point Checklist](#7-employee-security-awareness-training-a-5-point-checklist)
8. [Conclusion: Three Takeaways](#8-conclusion-three-takeaways)
9. [References](#9-references)

---

## 1. Introduction

Social engineering is the use of deception to get a person to do something that helps an attacker, such as giving away a password, opening a file, approving a login or letting a stranger through a door. Nothing has to be hacked. The attacker only has to be believable.

It is considered one of the most effective attack vectors because people are much harder to patch than software. We want to be helpful, we respond to authority, we are curious, and when we are busy we skim. Attackers build their messages around exactly those habits. Verizon's 2025 Data Breach Investigations Report analysed 12,195 confirmed breaches and found that a human element was involved in about 60% of them. That figure includes honest mistakes as well as deception, but deception is a large part of it. A SANS Institute paper makes the same point from the defender's side. It describes social engineering as one of the most effective methods criminals have, says security teams have been slow to study why people fall for it, and argues that although stopping it completely is close to impossible, understanding why staff become easy targets can still reduce how often it works.

The practical result is that a company can have strong firewalls and up-to-date software and still lose control of its network because one employee believed a phone call or opened one email. The cases in this report happened to well-known organisations with serious security teams, and they are worth studying for what went wrong and also for what would have stopped the attack.

---

## 2. Phishing

### How it works

Phishing is a message that pretends to come from someone the victim trusts and tries to get them to click, open or reply. The aim is usually a password, a payment or a way onto the victim's computer. Criminals like it because sending a thousand messages costs almost nothing, and only a few people have to respond for it to pay off.

A typical attack follows a short sequence. The attacker picks a target and a story, then sends a message designed to get a quick reaction rather than careful thought. The victim clicks through to a fake login page, opens an attachment that carries malicious code, or simply replies with what was asked for. The attacker then uses the stolen password, or the foothold on the computer, to go further.

CISA lists the usual warning signs: urgent or emotional wording, often threatening bad consequences if you don't act straight away; requests for personal or financial details; shortened links that hide the real address; and sender names or links with small errors, such as a misspelt brand. CISA also points out that bad grammar used to give phishing away, but AI tools can now produce clean, professional text, so the other signs matter more than spelling.

### Types of phishing

| Type | What it is |
| --- | --- |
| Spear phishing | Aimed at one person or a small group. The attacker has done some research, so the message uses real names, projects or colleagues and is much harder to spot than a mass email. |
| Whaling | Spear phishing aimed at senior people such as executives and finance heads, who can approve payments or have wide access. |
| Vishing | Phishing by phone. The caller claims to be from a bank, a help desk or an authority, and uses the pressure of a live conversation to rush the victim. |
| Smishing | Phishing by text message, usually a link plus a short, urgent reason to tap it, such as a missed delivery or a locked account. |

### Real-world example: the RSA SecurID breach, March 2011

In March 2011, RSA, the security division of EMC, announced that attackers had broken into its network and taken information about SecurID, its two-factor authentication product. Governments, banks and defence contractors relied on SecurID, so this was a serious breach at a company whose job was to protect other companies.

RSA later described how it began. Two small groups of EMC employees received emails with the subject line "2011 Recruitment Plan". Each email had an Excel spreadsheet attached. Hidden in the spreadsheet was a Flash file that exploited a zero-day flaw in Adobe Flash, meaning a flaw that nobody had yet fixed because only the attackers knew about it. When at least one employee opened the file, a customised version of the remote access tool Poison Ivy was installed, and the attackers had a way in.

From that one machine they moved through the network, went after the credentials of people with access to valuable data, collected what they found and sent it out over FTP to an outside server. RSA said certain information had been taken but gave few details, which left many customers unsure whether their tokens could still be trusted.

### Impact

The damage spread well beyond the first computer. Lockheed Martin said weeks later that it had fended off an attack involving information from the RSA breach, and a leaked memo said the defence contractor L-3 Communications had been hit in a similar way. In July 2011 EMC reported that it had spent around $66 million on the incident. That covered the investigation, tightening its own systems and working with customers, including monitoring and replacing tokens. The figure leaves out any harm to RSA's reputation. The email itself was not sophisticated. It had an ordinary subject line and needed only one person to open it.

### Prevention recommendations

1. Filter and authenticate email. Use spam and malware filtering, and set up SPF, DKIM and DMARC so that forged mail pretending to be from your own domain gets rejected. A lot of phishing never reaches an inbox this way.
2. Use phishing-resistant multi-factor authentication. A hardware security key only works on the genuine site, so a password typed into a fake page is no use to the attacker on its own.
3. Limit the damage one click can do. Sandbox or block risky attachments, keep software patched, give people only the access they need, and watch for odd outbound traffic. Patching alone would not have stopped RSA's attackers because the flaw was unknown at the time, so the layers that contain a break-in are what count when something gets through.
4. Make reporting quick. A "report phishing" button in the mail client, with feedback on what happened next, lets the security team pull a bad email from every inbox within minutes of the first report.

---

## 3. Pretexting

### How it works

Pretexting is when an attacker invents a believable situation, the pretext, and plays a part in it to get information or access. Phishing usually depends on a single deceptive message. Pretexting is closer to acting. The attacker might pose as a new colleague, an auditor, a supplier or the IT help desk, and the story is built so that helping feels like the normal thing to do.

A good false scenario is built in stages. First comes research: names, job titles, who reports to whom and the company's own jargon, collected from LinkedIn, the company website and old breaches. Next the attacker chooses a role that has a good reason to ask, such as IT, HR, finance or a vendor. Then they add a reason to act now, such as a fault that needs fixing, a deadline or a changed process. The early requests are small and harmless, like confirming a name or which system someone uses, and each answer makes the next request seem more natural. Only after that comes the real ask, whether it is a password, an approval or access to a system. Because a real person is adapting as the conversation goes, pretexting is harder to catch with filters than a mass email is.

### Real-world example: the Twitter hack, July 2020

On 15 July 2020, tweets offering to double any bitcoin sent to an address appeared on a string of well-known Twitter accounts. The investigation by the New York State Department of Financial Services (DFS) showed the scam had begun with phone calls the afternoon before.

The attackers called several Twitter employees, and their story fitted the moment well. Twitter had switched to remote working in March 2020, and VPN trouble was a common complaint. The callers said they were from Twitter's IT help desk and were following up on a VPN problem. They sent the employees to a website that looked just like Twitter's real VPN login.

The next part is what made it work. While an employee typed their details into the fake page, the attackers entered the same details into Twitter's real login. That sent a multi-factor authentication prompt to the employee's phone, which looked like part of the process they had just been told about, and some employees approved it. The DFS report says at least one employee "believed the Hackers' lies".

### Impact

The first account the attackers got into did not have much power. They used it to browse internal pages and learn how Twitter's systems and processes worked, then used that knowledge, along with personal details about staff, to go after employees who could reach the account support tools. In total 130 accounts were compromised, 45 of them were used to post tweets, and the scam took in roughly $118,000 in bitcoin.

The DFS did not put the blame on one careless person. It found no sign that any employee helped knowingly, and it pointed to how the company was set up: app-based multi-factor authentication that could be talked around, more than a thousand people with access to the internal tools, and no chief information security officer in post from December 2019 until the attack. It said a hardware security key would have stopped the attackers, and Twitter said it is moving to them.

### Prevention measures

1. Call back on a number you already have. For any unexpected request for credentials, access or a change to how something is done, hang up and ring the person or department using the company directory, not a number the caller gave. A real help desk will not mind.
2. Use hardware keys, and never approve a prompt you did not start. A hardware key cannot be approved by someone who has been talked into it, and it only works for the real site. Staff should also have a firm rule that an unexpected multi-factor prompt is treated as an attack and reported.
3. Limit access and require a second person for risky actions. If few people can reach powerful tools, and the riskiest actions need a second employee to sign off, one fooled employee cannot do much harm. The DFS report recommends both.

---

## 4. Baiting

### How it works

Baiting offers something tempting and waits for the victim to take it. The temptation is usually curiosity or the chance of something free. The attacker doesn't need to chase anyone, because the bait only has to be left where the right person will find it.

Physical baiting uses real objects. The standard example is an infected USB drive dropped in a car park, a lobby or a toilet, sometimes labelled with something like "Salaries" or "Confidential" so that people want to look. Plugging it in can run malware without the user doing anything else. A nastier version is a device that pretends to be a keyboard. The computer trusts keyboards, so the device can type commands on its own without the user opening a single file.

Digital baiting works the same way online. It includes pirated software or films that are really malware, free tools and browser extensions with something hidden in them, fake software updates, and ads promising prizes or giveaways. The victim goes looking for a free download and installs the attack themselves.

Curiosity is well documented. In a study presented at the IEEE Symposium on Security and Privacy in 2016, researchers from the University of Illinois and Google left 297 USB drives around a large university campus. The first one was plugged in less than six minutes later, and the researchers estimated that this kind of attack succeeds somewhere between 45% and 98% of the time depending on how success is counted. The paper's title says it plainly: users really do plug in USB drives they find.

### Real-world example: FIN7's mailed USB devices, 2020 to 2022

FIN7 is a financially motivated criminal group. Instead of leaving drives lying around, it mailed them to its victims.

In 2020 the FBI warned about packages sent to hotels, restaurants and retailers that were made to look like they came from Best Buy. Inside were a USB drive and a fake gift card, and from May 2020 some also contained a teddy bear. Some victims said the attackers followed up by phone or email to pressure them into plugging the drive in.

The group came back in late 2021 with a new disguise. According to an updated FBI alert from January 2022, packages were sent through the US Postal Service and UPS, pretending to be from Amazon or the US Department of Health and Human Services. Depending on the disguise, the package held a letter about COVID-19 guidelines, a counterfeit gift card or a forged thank-you note. Inside were "BadUSB" devices, which present themselves to the computer as a keyboard. This matters because a keyboard is accepted even on machines where USB storage has been blocked. Once plugged in, the device typed in commands by itself and installed malware.

### Impact

The targets were businesses in transportation and insurance from August 2021, and US defence companies from November 2021. The FBI said the aim was to get into the victim's network and deploy ransomware, including the BlackMatter and REvil families, using tools such as Cobalt Strike, Metasploit and PowerShell scripts. The public reporting does not give figures for how many victims plugged the devices in or what it cost them, so the scale of the damage is not known. What the campaign does show is the effort that went into the bait. It looked like normal business mail from a trusted brand, arrived the normal way, and was addressed to someone who had every reason to open it.

### Prevention measures

1. Control which USB devices can connect. Allow only devices approved by hardware ID or checked by the security team, and turn off autorun. This is also the control that stops keyboard-style devices like FIN7's.
2. Give staff a clear rule and an easy alternative. Nobody should plug in a drive they found or received unexpectedly. Tell them to hand it to IT instead, so the safe choice is also the easy one, and to check unexpected parcels with the supposed sender through a known contact.
3. Restrict installs and scan downloads. Allow software only from an approved list or company store, run endpoint protection that scans downloads and removable media, and block known malicious sites. This covers digital baiting as well as the physical kind.

---

## 5. Quid Pro Quo (Bonus)

### How it works

Quid pro quo means "something for something". The attacker offers help or a benefit and asks for something back, so the victim feels they are getting a fair deal and doesn't question it.

The most common form is fake tech support. Someone phones staff, or contacts large numbers of people at random, saying they are from IT and can fix a slow computer or a security problem. To "help", they ask the victim to read out a password, install a remote support tool or switch off antivirus for a moment. Another form offers something free, like software, a gift or a survey reward, in return for personal details or a download. It overlaps with pretexting, since the attacker is playing a role, and with baiting, since there is a tempting offer. What marks it out is the exchange itself: the victim is helped, and is asked to do something in return.

### Prevention

1. Make it a rule that IT never asks for passwords and never offers help nobody asked for. Real support follows a ticket the employee raised, so an unexpected offer of help is itself a warning sign.
2. Before anyone installs remote access software or changes a security setting for a caller, confirm the request with the real help desk through a number from the company directory.
3. Let only IT install remote support tools, so that even a persuaded employee cannot give an attacker control of their machine, and report every attempt, including failed ones, so colleagues can be warned.

---

## 6. Comparison of the Attacks

| Attack type | Primary target | Psychological lever exploited | Best countermeasure |
| --- | --- | --- | --- |
| Phishing | Any employee with an email address or phone; executives and finance staff in spear phishing and whaling | Urgency and fear, plus trust in a familiar sender or brand | Phishing-resistant MFA (hardware keys), backed by email filtering and easy reporting |
| Pretexting | Staff who can grant access or release information, such as help desk, HR, finance and new starters | Authority and the wish to be helpful | Call-back verification on a known number, and least privilege with second-person approval for risky actions |
| Baiting | Anyone who might pick up a device or download something "free" | Curiosity and the appeal of free things | USB allowlisting, a clear policy on unknown devices, and approved-software-only installs |
| Quid pro quo | Employees who might welcome help with a technical problem | Reciprocity: a favour feels like it deserves one in return | A rule that IT never makes unsolicited contact, and independent checking of any support request |

Two things run through all four attacks. Each one relies on an ordinary human instinct, such as trust, helpfulness, curiosity or reciprocity, rather than a technical flaw. And the best defence in each case pairs a technical control that limits the damage with a simple habit that interrupts the attack, like checking through a known channel. Neither is enough alone.

---

## 7. Employee Security Awareness Training: A 5-Point Checklist

Awareness training sticks when it is practical and repeated. These five points can form the core of a programme for all staff.

1. Know the red flags. Everyone can name the common signs of an attempt: urgency or threats, unusual requests for passwords or payments, mismatched sender addresses or links, and offers that seem too good to be true. This applies to email, calls, texts and physical items.
2. Verify before you act. Anything unusual gets confirmed with the person or department through a contact you already trust, never one supplied in the message or call. A real colleague or help desk will not take offence.
3. Protect your login and your prompts. Never share a password, never approve a multi-factor prompt you did not start, and use hardware keys or the approved authenticator wherever the organisation provides them.
4. Treat unknown devices and downloads as hostile. Do not plug in found or unexpected USB drives, do not install software that is not on the approved list, and pass anything suspicious to IT.
5. Report quickly, without blame, and practise. Everyone knows how to report a suspected attack, including one they already fell for, and knows they will be thanked rather than punished. The organisation backs this up with regular simulated phishing and vishing exercises, and shares what it learns from real attempts.

---

## 8. Conclusion: Three Takeaways

Phishing, pretexting, baiting and quid pro quo look different, but they share one idea: it is easier to persuade a person than to break a system. The RSA breach started with a spreadsheet, the Twitter hack with a phone call about a VPN problem, and the FIN7 campaign with a parcel that looked like it came from Amazon.

1. The people caught out were not foolish. In every case they were busy and responding to something that looked normal, so training should aim to build habits such as checking through a known channel, not to make staff feel they must never make a mistake.
2. Technical controls can take pressure off people. Hardware keys, USB allowlisting and least privilege each turn a human mistake into a smaller problem, and the Twitter report said outright that a hardware key would have stopped that attack.
3. Culture counts as much as tools. When staff feel safe asking "is this real?" and reporting mistakes straight away, an organisation has its best chance of catching an attack early.

---

## 9. References

1. Verizon. (2025). *2025 Data Breach Investigations Report.* https://www.verizon.com/business/resources/reports/dbir/
2. Alexander, M. (2016). *Methods for Understanding and Reducing Social Engineering Attacks.* SANS Institute Information Security Reading Room. https://www.sans.org/reading-room/whitepapers/critical/methods-understanding-reducing-social-engineering-attacks-36972
3. CISA. *Recognize and Report Phishing.* Cybersecurity and Infrastructure Security Agency. https://www.cisa.gov/secure-our-world/recognize-and-report-phishing
4. New York State Department of Financial Services. (2020). *Twitter Investigation Report.* https://www.dfs.ny.gov/system/files/documents/2026/07/Twitter-Investigation-Report.pdf
5. TechTarget. (2020, October). Twitter hackers posed as IT staff, used VPN issues as a lure. https://www.techtarget.com/cybersecurity/news/252490684/Twitter-hackers-posed-as-IT-staff-used-VPN-issues-as-a-lure
6. Help Net Security. (2020, July 31). Twitter employees were spear-phished over the phone. https://www.helpnetsecurity.com/2020/07/31/twitter-employees-spear-phished/
7. Dark Reading. (2011, April). RSA Details SecurID Attack Mechanics. https://www.darkreading.com/cyberattacks-data-breaches/rsa-details-securid-attack-mechanics
8. Nextgov. (2011, August). Anatomy of the attack on RSA. https://www.nextgov.com/cybersecurity/2011/08/anatomy-of-the-attack-on-rsa/218887/
9. Help Net Security. (2011, July 28). What did the RSA breach end up costing EMC? https://www.helpnetsecurity.com/2011/07/28/what-did-the-rsa-breach-end-up-costing-emc/
10. Gatlan, S. (2022, January 7). FBI: Hackers target US defense firms with malicious USB packages. *BleepingComputer.* https://www.bleepingcomputer.com/news/security/fbi-hackers-target-us-defense-firms-with-malicious-usb-packages/
11. Tischer, M., et al. (2016). *Users Really Do Plug in USB Drives They Find.* IEEE Symposium on Security and Privacy. https://research.google/pubs/users-really-do-plug-in-usb-drives-they-find/
