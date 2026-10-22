## Common Network Security Threats: A Research Report

*October 2026*

## Table of Contents

1. [Introduction](#1-introduction)
2. [DoS and DDoS Attacks](#2-dos-and-ddos-attacks)
3. [Man-in-the-Middle (MITM) Attacks](#3-man-in-the-middle-mitm-attacks)
4. [IP Spoofing](#4-ip-spoofing)
5. [DNS Poisoning and Spoofing](#5-dns-poisoning-and-spoofing)
6. [Comparison of the Four Threats](#6-comparison-of-the-four-threats)
7. [Conclusion: Three Takeaways for a Network Administrator](#7-conclusion-three-takeaways-for-a-network-administrator)
8. [References](#8-references)

---

## 1. Introduction

Networks carry almost everything we rely on now: banking, hospital records, school portals, the power grid. Most underlying protocols were built when the goal was simply to get machines talking to each other, and nobody thought much about attackers. The gap shows. A flood of junk traffic can take a major internet provider offline for hours, a connection that is quietly intercepted can give away a password without anyone noticing, and a forged address or a tampered DNS record can send a customer to a fake site that looks identical to the real one. The tools for all this are easy to find, and there are millions of badly secured devices out there waiting to be hijacked. This report covers four common threats: DoS/DDoS, man-in-the-middle, IP spoofing and DNS poisoning/spoofing. Each section explains how the attack works, goes through a real incident, looks at the damage and lists three mitigations. A comparison table follows, and the report closes with three takeaways for a network administrator.

---

## 2. DoS and DDoS Attacks

### How it works

A denial-of-service (DoS) attack tries to knock a service offline by using up something it needs, whether that is bandwidth, open connections or processing power. If the flood comes from a single machine, it is a DoS attack. If it comes from thousands of machines at once, it is a distributed denial-of-service (DDoS) attack, and that is the version that causes real damage, because there is no single source to block.

CISA, the FBI and MS-ISAC group DDoS attacks into three types. Volumetric attacks try to eat all the available bandwidth. Protocol attacks take advantage of weaknesses in how network protocols work. Application attacks go after a specific application or service. MITRE's example of the first type is easy to picture: send 10 Gbps of traffic to a server that sits behind a 1 Gbps internet connection,ction and the connection is exhausted, however powerful the server is. Botnets, which are large groups of hijacked devices, and spoofed source addresses turn up in many of these attacks.

### Real-world example: the Dyn attack, October 2016

On 21 October 2016, attackers started flooding Dyn, a company that handles DNS for a long list of well-known websites. People had trouble reaching Twitter, Amazon, Tumblr, Reddit, Spotify and Netflix, among others. Researchers at the security firm Flashpoint tied at least part of the attack to a Mirai botnet, built mostly from hacked digital video recorders and IP cameras made by a Chinese company called XiongMai Technologies.

Mirai finds its victims by scanning the internet for devices that still use factory-default usernames and passwords. With the XiongMai devices, owners couldn't have fixed this even if they'd wanted to, because the password was hardcoded into the firmware. The author of Mirai had published its source code a few weeks earlier, so anyone could build their own botnet. A Flashpoint scan on 6 October had already found more than 515,000 devices with the same flaws. Wired later reported that the attack peaked at around 1.2 Tbps.

### Impact

Nobody broke into Dyn to steal anything. What suffered was availability: people couldn't get to services they use every day. The sites that went dark were Dyn's customers rather than the target itself, which shows how one weak point in shared infrastructure can hurt a lot of organisations at the same time. CISA also warns that a DDoS can work as a distraction, keeping the security team busy while something quieter, such as data theft, goes on in the background.

### Mitigation strategies

1. Filter the traffic upstream. When a flood is larger than your own internet connection, you can't filter it at your own door, so it has to be stopped before it gets there. Your ISP, a content delivery network or a dedicated DDoS protection provider can do this. GitHub is a good example. In 2018, it moved its traffic to a mitigation provider during a 1.35 Tbps attack and was back to normal within minutes.
2. Have a plan before you need one. CISA's advice is to work out which services are critical, understand how users reach them, sign up with a protection service in advance, and keep a written DDoS response and continuity plan that you update after every incident.
3. Keep your own devices out of botnets. Mirai worked because of default passwords. Change the defaults on cameras, routers and recorders, keep firmware current, don't expose Telnet or SSH to the internet, and replace devices that can't be fixed.

---

## 3. Man-in-the-Middle (MITM) Attacks

### How it works

In a man-in-the-middle attack, someone secretly positions themselves between two parties who think they are talking directly to each other. From there, they can read the traffic, copy it or change it before passing it on. MITRE now calls the technique adversary-in-the-middle, and notes that it often works by abusing protocols that decide where traffic goes, such as ARP and DNS.

ARP spoofing is the classic local version. ARP matches IP addresses to the hardware (MAC) addresses of devices on the same network, and it has no authentication. A device will accept a forged reply claiming "that IP address is me" and start sending its traffic to the attacker. A SANS Institute paper puts the general idea in similar terms: the attack depends on convincing two hosts that the computer in the middle is the other host, whether through a DNS spoof or ARP spoofing on the local network.

Encryption can be targeted too. An attacker holding a fraudulent but trusted certificate can pose as a website, and the victim's browser will still show the usual padlock. Another approach is to push a connection down to an older, weaker version of TLS.

### Real-world example: the DigiNotar breach, 2011

DigiNotar was a Dutch certificate authority, a company whose job is to vouch that a website's certificate is genuine. Attackers got into its systems in June 2011, and on 10 July they issued the first rogue certificate, a wildcard certificate for `*.google.com`. DigiNotar detected the intrusion on 19 July, but the public only learned about the problem at the end of August, when the certificate turned up being used against Gmail users in Iran. Fox-IT's investigation later found that around 300,000 users, almost all of them in Iran, had been exposed to a man-in-the-middle attack through it.

A security feature in Google's Chrome browser flagged the fake certificate and helped bring the attack to light. After that, Microsoft, Google and Mozilla all released updates so their software would stop trusting DigiNotar.

### Impact

The people affected thought their Gmail sessions were private and encrypted, and they weren't. The certificate was issued on 10 July and wasn't revoked until late August, which left a long window for interception. Going by who was targeted, the goal looks like reading private communications, not ordinary fraud. The wider problem is trust. Browsers accepted DigiNotar as an authority that could vouch for any domain, so one compromised certificate authority put every site at risk.

### Mitigation strategies

1. Encrypt everything and validate certificates. MITRE recommends encrypting all wired and wireless traffic and protecting any web traffic that carries credentials with TLS. In practice, that means HTTPS everywhere, current TLS versions only, and HSTS so browsers refuse to quietly drop to an unencrypted connection.
2. Lock down the local network. On managed switches, enable DHCP snooping and Dynamic ARP Inspection, which tie IP addresses to switch ports and block forged ARP messages. Static ARP entries can protect a few critical machines, but MITRE points out they are impractical on large networks.
3. Watch for it, and train people. Signs of ARP poisoning include several IP addresses suddenly mapping to one MAC address and bursts of unsolicited ARP replies. Users should also be taught to treat a certificate warning as a reason to stop, not something to click through.

---

## 4. IP Spoofing

### How it works

Every IP packet carries a source address, and the protocol itself does nothing to check that it is true. An attacker can simply write a different one. Spoofing is rarely the end goal. It is a disguise, used to hide where an attack comes from, to pose as a trusted machine and, most importantly, to run reflection and amplification attacks. In those, the attacker sends small requests to third-party servers with the victim's address as the source, and every reply lands on the victim.

UDP is the usual choice for this because it has no handshake. TCP's handshake makes blind spoofing much harder, which is why reflection attacks lean on UDP services.

### Real-world example: the GitHub memcached attack, February 2018

On 28 February 2018, attackers went after GitHub using memcached servers that had been left open to the internet with UDP enabled. They sent small queries with GitHub's address forged as the source, and each server replied with a much bigger response aimed at GitHub. GitHub's incident report gives the amplification factor as up to 51,000, so one byte from the attacker could turn into as much as 51 KB arriving at the target.

Traffic peaked at 1.35 Tbps, or 126.9 million packets per second, and came from over a thousand networks and tens of thousands of endpoints. GitHub was unavailable from 17:21 to 17:26 UTC and intermittently down until 17:30. Wired called it the most powerful DDoS recorded up to that point and pointed out that it needed no botnet.

### Impact

The outage was short. GitHub moved its traffic to Akamai's mitigation service within minutes and says the confidentiality and integrity of user data were never at risk. What makes the attack worrying is how little the attacker had to send: one byte in, up to 51 KB out. The victim also couldn't just block the sources, because they were ordinary servers doing what they had been set up to do. The people running those servers had no idea they were involved.

### Mitigation strategies

1. Apply ingress filtering (BCP 38). The IETF's best-practice document describes filtering at the edge of a network so that packets with source addresses that don't belong to that network get dropped. It won't stop floods sent from genuine addresses, but it does stop an attacker inside the network from sending forged ones. The catch is adoption, since it only really works when many networks do it.
2. Don't treat an IP address as proof of identity. Use cryptographic authentication such as TLS, SSH keys or IPsec. At your own firewall, drop packets that arrive from outside while claiming an internal source address, which follows the same logic as BCP 38.
3. Close the reflectors. Don't expose UDP services such as memcached to the open internet. Wired noted that the fix works on two levels: mitigation providers can add filters for this type of traffic, and owners of exposed servers can take them off public access.

---

## 5. DNS Poisoning and Spoofing

### How it works

The Domain Name System (DNS) translates the names people type into the IP addresses computers use. If an attacker can make that translation return the wrong answer, a user can type the right name and still land on the attacker's server. There are two main routes.

Cache poisoning slips a forged answer into a DNS resolver's memory, so the resolver keeps handing out the wrong address to everyone who asks until the entry expires. In 2008, the researcher Dan Kaminsky showed how practical this was. A DNS query carries a 16-bit transaction ID, which means only 65,536 possible values, and an attacker who makes enough attempts can guess it. The fix was to randomise the UDP source port as well, which multiplies the number of values an attacker has to guess.

DNS hijacking skips the guessing. The attacker changes the real DNS records, usually by stealing the login to an account at a domain registrar or DNS provider. Changing the DNS settings on a victim's router is another route.

### Real-world example: the 2019 DNS infrastructure hijacking campaign

In January 2019, CISA published alert AA19-024A about a worldwide DNS infrastructure hijacking campaign. The attackers used compromised credentials to change where an organisation's domain names pointed. They edited address (A), mail exchanger (MX) or name server (NS) records so that traffic went to infrastructure they controlled, and they obtained valid encryption certificates for the victims' domains. That let them sit in the middle, inspecting or altering traffic before passing it on to the legitimate service.

CISA also issued Emergency Directive 19-01 after several federal agency domains were affected, telling agencies to take specific steps to secure their DNS.

### Impact

When a domain's DNS is hijacked, everything tied to it can be redirected: the website, email, and any login that depends on the domain. Because the attackers had valid certificates for those domains, the redirected sites could still present proper encryption. Passwords, email and the organisation's good name were all exposed. NIST makes the same point in general terms: an attack on DNS can affect an entire organisation.

### Mitigation strategies

1. Protect the accounts that can change DNS. CISA's alert recommends updating the passwords on every account that can modify DNS records, enabling multi-factor authentication on registrar accounts, and regularly auditing public DNS records to confirm they point where they should.
2. Deploy DNSSEC. DNS Security Extensions add digital signatures to DNS data, so a resolver can check that an answer is genuine and unchanged. NIST's current DNS guide covers using DNSSEC to protect the integrity and authenticity of DNS information, and the Unbound project notes that DNSSEC is the only way to actually detect forged data in this kind of cache poisoning.
3. Harden and monitor your resolvers. Keep DNS software patched and make sure it randomises source ports and query IDs, which makes guessing attacks far harder. NIST also describes DNS as a place to enforce security policy and a source of early warning signs, so logging DNS queries and using protective DNS filtering are worth turning on.

---

## 6. Comparison of the Four Threats

The ratings below are my own general assessments, based on the sources in this report. They aren't exact measurements, and real difficulty depends on the target and on the attacker's resources.

| Threat | Attack vector | Who is at risk | Difficulty to execute | Ease of mitigation |
| --- | --- | --- | --- | --- |
| DoS / DDoS | Flooding a target's bandwidth, protocols or applications, usually with a botnet or reflected traffic | Any internet-facing service, especially DNS providers, e-commerce sites, ISPs and critical infrastructure | Low to medium. Botnet code is freely available, and attack services can be rented | Moderate to hard. Large floods need upstream help from an ISP, CDN or protection provider |
| Man-in-the-Middle | Positioning between two parties through ARP or DNS abuse, rogue Wi-Fi or fraudulent certificates | Users on shared or untrusted networks, anyone sending credentials without proper encryption, organisations that rely on certificate trust | Medium. Usually needs local network access or a compromised piece of infrastructure | Moderate. TLS, switch-level protections and monitoring work well but have to be set up everywhere |
| IP Spoofing | Forging the source address in packets, mostly UDP, to hide identity or to reflect and amplify traffic | DDoS victims, organisations that trust IP addresses for access, owners of exposed servers used as reflectors | Low for sending forged packets; higher if the goal is to hijack a connection | Hard for the victim. Real prevention depends on many networks applying ingress filtering |
| DNS Poisoning / Spoofing | Forging DNS answers in a resolver cache, stealing registrar or DNS account credentials, or changing router DNS settings | Anyone using the affected domain or resolver, including customers of banks, government bodies and large organisations | Medium to high against patched resolvers; low when credentials are stolen or a router has weak settings | Moderate. Account security and patching are easy; DNSSEC works well but isn't deployed everywhere yet |

---

## 7. Conclusion: Three Takeaways for a Network Administrator

Looking back over the four threats, they have one thing in common: each takes advantage of something the network trusted without checking. Three practical lessons come out of that.

1. Add checks where the protocols don't have any. IP doesn't verify source addresses, ARP doesn't verify who is replying, and plain DNS doesn't verify that an answer is real. Each gap has a control that covers it: ingress filtering, Dynamic ARP Inspection, DNSSEC, and properly validated TLS. Most of these aren't turned on by default, so they only help once somebody sets them up.
2. Plan for the attack you can't fully prevent. The 2016 Dyn attack and the 2018 GitHub attack were both enormous, but GitHub was back within minutes because it already had a mitigation provider ready to switch to. Know which services are critical, arrange upstream protection, and write the response plan down before you need it.
3. Take care of the small things first. The Dyn botnet was built on default passwords. The GitHub attack used servers that should never have been reachable from the internet. The 2019 DNS campaign started with stolen credentials. Changing defaults, enabling multi-factor authentication for registrar and DNS accounts, patching resolvers, and shutting down services nobody needs close off the easiest entry points, which attackers usually try first.

---

## 8. References

1. Rose, S., Liu, C., & Gibson, R. (2026). *Secure Domain Name System (DNS) Deployment Guide* (NIST Special Publication 800-81r3). National Institute of Standards and Technology. https://doi.org/10.6028/NIST.SP.800-81r3
2. CISA, FBI, & MS-ISAC. *Understanding and Responding to Distributed Denial-of-Service Attacks* (joint guide, first released October 2022, updated March 2024). Cybersecurity and Infrastructure Security Agency. https://www.cisa.gov/resources-tools/resources/understanding-and-responding-distributed-denial-service-attacks
3. CISA. (2019, January 24). *Alert AA19-024A: DNS Infrastructure Hijacking Campaign.* https://www.cisa.gov/ncas/alerts/AA19-024A
4. MITRE. *Network Denial of Service, Technique T1498.* MITRE ATT&CK. https://attack.mitre.org/techniques/T1498/
5. MITRE. *Adversary-in-the-Middle: ARP Cache Poisoning, Sub-technique T1557.002.* MITRE ATT&CK. https://attack.mitre.org/techniques/T1557/002/
6. MITRE. *Adversary-in-the-Middle, Technique T1557.* MITRE ATT&CK. https://attack.mitre.org/techniques/T1557/
7. Krebs, B. (2016, October 21). Hacked Cameras, DVRs Powered Today's Massive Internet Outage. *Krebs on Security.* https://krebsonsecurity.com/2016/10/hacked-cameras-dvrs-powered-todays-massive-internet-outage/
8. Newman, L. H. (2018, March 1). GitHub Survived the Biggest DDoS Attack Ever Recorded. *WIRED.* https://www.wired.com/story/github-ddos-memcached/
9. Kottler, S. (2018, March 1). February 28th DDoS Incident Report. *The GitHub Blog.* https://github.blog/news-insights/company-news/ddos-incident-report/
10. Fox-IT. *DigiNotar Certificate Authority breach* (investigation report published by the Dutch government). 
