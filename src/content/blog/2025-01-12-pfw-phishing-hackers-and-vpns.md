---
author: Brian Waltz
pubDatetime: 2025-01-12
modDatetime: 2025-01-13
title: PFW - Phishing, Hackers, and VPNs
slug: PFW-VPN-2025-1
featured: true
draft: false
tags:
  - PFW
  - Hacking
  - "VPN "
  - News
description: A barrage of more sophisticated phishing campaigns has recently
  prompted PFW to broaden its VPN requirements. We explore what this looks like,
  and how it might help.
---
_As a personal note, this article represents my opinion - not that of the ACM or PFW. Further, it will be written based on my personal experiences and knowledge with respect to the subject. That said, I believe this could still be helpful to those willing to humor my thoughts._

# What's happening?

PFW has recently broadened the expectations for what services must be accessed using a VPN into the University network, affecting those who are accessing Uni resources off-campus. This is in response to an increase in both volume and sophistication of attacks targeting PFW and Purdue students (Purdue emails trickle into PFW inboxes). Specifically, the requirement has been broadened to include CAS or the Central Authentication Service. The email heads as follows:

> "As we welcome students, faculty, and staff back for the spring semester, we continue to seek ways to strengthen the security posture across the Purdue University system. Effective immediately, we will now require connection to a Virtual Private Network, or VPN, before Purdue University Fort Wayne and Indiana University Fort Wayne users can access Central Authentication Service, or CAS, while off campus." - PFW ITS

First, let it be said that this VPN is NOT new. While it is new to many students, the requirement has existed for several years. Resources which are considered targets for those off campus generally need to be accessed through the VPN when off campus. I have used the VPN for a couple of years, and in fact the student body has received information about it in the past. However, I must acknowledge that it is certainly a disruption to the typical user-flow of the average student - and it was timed poorly in implementation. I also do not believe it is the most effective solution to this problem, but I also don't necessarily believe it's the entirety of the solution.

This inconvenience is likely a large part of why many students are upset, something I entirely understand. But there is also a significant amount of misunderstanding, and conspiracy theorizing, surrounding the recent decision. _That_ is what I would like to address through some analysis of what's happening, what's affected, how this could help, and combatting a few common complaints.

# What does this affect?

## CAS

This change specifically affects CAS. CAS is the University's Single-Sign-On system (really a protocol, Shibboleth is the system).

A Single Sign On system/service (Commonly an SSO) is something that manages and administers user authentication centrally, allowing other apps to delegate requests to it. You have likely noticed that when attempting to sign-in to a variety of different websites, you get redirected to the CAS sign-in before being allowed to sign-in. Those apps trust the CAS to do all the work of managing and validating users, and the CAS just tells them what it decides in the end.

This is helpful for managing a large number of different services in a secure and efficient manner. If your users want to have a sign-in for ten websites, and all ten support CAS, then both you and them only need to manage and secure one CAS account.

But this also creates a centralized _target_.

A CAS account being stolen gives an attacker access to all of the services that user could access, until the account is properly identified and secured. This means students may have educational record, assignments, messages and communications, health information, club affiliations, financial information and more. These accounts are _certainly_ being stolen - you've likely witnessed a stolen account sending emails. I'll be writing specifically about the recent phishing emails, but it's also true that they've increased in sophistication - using information scraped from Student Life, more stylistic emails, making fake CAS pages, etc.

## Everything else?

You can use CAS protected services without the VPN. You cannot _authenticate_ to them. However if you were already authenticated, or if you authenticate on the VPN, you don't need to remain on the VPN. The website stores information about your browsing session, including whether and how you authenticated. If the website has a valid record saying you authenticated, it doesn't care whether you can authenticate again. Any flow you can complete without encountering the CAS screen (or other VPN mandated services) can be done off the VPN. I have personally validated this, though I cannot speak to every setup (e.g. if you clear cookies, use incognito, have an unsupported browser, this may not be the case).

You are not being forced to use the VPN constantly, nor in every interaction you have off campus. In fact, if you have a way of sharing sessions between devices you can have a device that has the VPN and one that doesn't.

## Liability

We talked about a bunch of information the CAS can access, and we can probably agree that CAS accounts are being accessed. Here's where the University gets interested.

Universities, especially those funded using public funds, are expected to meet certain guidelines for security and data protection. When they fail to do so, they may be subject to fees, loss of funding, or loss of certain licenses and abilities. In particular, we can think of FERPA, GLBA, COPPA, ECPA, HIPAA, and likely a couple other more federal, corporate, and local licensing and privacy rules. When student accounts have wide access, and student accounts are compromised - and used to compromise other accounts - this presents a liability issue. The University needs to make good faith attempts to secure this data, and in some cases are liable regardless of what they tried or didn't try if they fail.

Implementing VPN policies is a common response for Schools and Universities when it comes to securing and monitoring this information, alongside identifying the scope of damage(s) to information and information assets.

I could harp about this one forever, but know that the Uni's interest primarily lies here.

# What can the VPN even do? What's the intention?

Many students are confused about what the VPN could assist with, and many suspect alternative aims or incompetency. While neither avenue is outside of scope for PFW, I believe there's a solid case for the VPN and don't suspect a malicious plot. First, let's take a look at what's being said.

## Student Comments

Reviewing PFW's discord servers, the Snap stories, and actual conversations, here's a list of what I've heard:

*   The VPN is meant to block TikTok
    
*   The VPN is spyware
    
*   The VPN shouldn't affect students already using a VPN
    
*   The VPN has kernel level access
    
*   The VPN is required, for everyone
    
*   The VPN doesn't work
    
*   The VPN is a security risk
    

### The VPN is meant to block TikTok

No. The University already blocks TikTok. They have no real interests in whether you use TikTok, but can't allow it on their networks. This doesn't block TikTok from you unless you have it on while browsing TikTok - something you're not expected to do.

### The VPN is spyware

This one is interesting. It is complex to answer, and I cannot say with certainty. My ultimate answer is no, and I don't particularly see why the University would want to spy on all off-campus students - nor why they would use a blatant method when there are better methods available.

To be perfectly clear, the University has access to devices that use their Microsoft accounts. There are thousands of student devices that are 'enrolled' to PFW accounts but are private devices. Some services require that they can manage or see certain aspects of your device. There are more safeguards present in that process than there are for Cisco's VPN, but the ability has not been absent on the University's end. I am unaware of any instance of it being used. Further, if you have Microsoft ads, services, or apps in your user-journey while signed into your account, the University can likely see (either directly or by scraping their data) what was happening there as blips. If the University interest was spying, I believe it would happen.

The argument in this case is that the University can 'see all traffic' through the VPN. That is not accurate, but also not inaccurate. A VPN routes traffic through itself to an endpoint, encrypting it in the process, and once it reaches its endpoint the traffic flows normally. The endpoint does the same in reverse, sending what traffic flows to it back to the user's VPN client, where it's decrypted. VPN's are nice because to an observer outside the VPN, all they see is the connection to the VPN. To the VPN provider though, it looks normal.

Using the VPN is the same as browsing and operating from within PFW. In the modern age, almost all sites use HTTPS - the encrypted HTTP standard. This means your web-traffic, the content of the page, is encrypted. This means ISPs and VPNs alike can't actually see the _content_ of your browsing activity. Now, there is another step to the process of browsing that they can see - DNS. DNS, also known as Domain Name Servicing, converts website names like "google.com" into the address information necessary to communicate with the website.

It is possible to encrypt DNS requests, but most users don't do it, and as far as I know PFW blocks encrypted DNS. But they don't block TLS - allowing encrypted website connections. There are attacks the University could perform to weaken or subvert website encryption, but it would be processing intense and, in many cases, tedious. So, the University can see what sites you go to and when, but not necessarily what pages or what's on them.

The amount of effort, and lack of gain, for PFW to be spying through the VPN makes it extremely unlikely. However, it is true that the client presents the potential for a rogue actor to attempt to access student systems. Specifically, the VPN has remote access capabilities, local LAN capabilities, and local printer capabilities - presenting an ideal target for enumeration and lateral movement, as well as attacking the client system. It is not unheard of for rogue workers to abuse such privileges against company policies for personal gain, it's happened at TikTok, Facebook, and more. I would be interested in PFW's way of addressing this.

**NOTE:** I will note that it is likely possible to use your own compliant client with the University's VPN. Using something like Cisco OpenConnect would mitigate many of these issues, and should comply with the AnyConnect protocol. Just ensure to set the endpoint to "webvpn.pfw.edu".

### The VPN shouldn't affect students already using a VPN

The goal isn't for students to 'have a VPN'. It's for students to access campus resources from campus, and to identify a clear and common endpoint for those beyond campus. Whether you were already using a VPN or not is irrelevant to that. I will note that another VPN would likely be more secure, but I would also note that you should only use the University's VPN for accessing its resources - making this a moot concern in my opinion.

### The VPN has kernel-level access

I have seen no evidence of this, and did not need to grant such access when installing this VPN on any devices. Extraordinary claims require the matching evidence, so if I'm wrong please do correct me.

### The VPN is required, for everyone

The VPN is for off-campus students. You don't need to use it on campus. You also don't have to use if off campus if you're not attempting to access specific University resources. You are not being required to use it, you are being required to use it to access specific resources, and there is a difference.

### The VPN doesn't work

I can confirm the VPN has intermittent authentication issues. It does indeed work, but it seems that there may either by an unknown issue present, or its experiencing load issues.

### The VPN is a security risk

This is accurate. I believe the VPN presents a greater opportunity for high-risk phishing attempts due to implementation, and I believe that it may be a security risk.

While there is some inaccurate conflation between Cisco hacks and insecurities in the Cisco AnyConnect Client, the VPN client is indeed a high-risk target, and has indeed been attacked before with both novel attacks, and several year old vulnerabilities. I'd like to assume the manufacturer & University will be diligent in issuing patches, and students diligent in installing them, but reality is often disappointing.

Likewise, there exists the potential for hackers to guide students towards fake or backdoored VPN clients, defeating the point, and presenting an even higher risk. A backdoored client would be able to easily steal a user's CAS credentials, while performing attacks from their personal device & IP, and even accessing private files and information on the device.

This is a correct statement.

## What can the VPN do?

The VPN is a client that connects to an endpoint and tunnels traffic through campus internet. With West Lafayette as our ISP, this places a lot of control in PFW & Purdue's hands. Here's a list of benefits I could see:

*   Narrowing service attack points
    
*   Identifying Devices/IPs accessing the VPN
    
*   Blocking known attacker infrastructure
    
*   Allows more strict firewall rules
    
*   Protect students on less secure networks or infrastructure
    
*   Adds a step to service attacks
    

### Narrowing service attack points

If you only have to filter from a list of VPN users rather than the entire internet, your threat scope narrows. You can focus more on validating who should be accessing the VPN, what patterns they're showing and how those deviate from the norm, and requiring an attacker to become more familiar with the University's processes to launch an attack.

### Identifying Devices/IPs accessing the VPN

If a student account is compromised and used to connect to the VPN, it may be easier to identify who the attacker is based on data from the VPN or connection. This may result in larger-view goals of pursuing the people initiating these attacks, or identifying patterns indicating where the attackers come from, or when a device may be attacker controlled. This may also help in separating between good accounts, students maliciously using resources, and clearly attacker controlled accounts.

### Blocking known attacker infrastructure

When the University identifies attacker controlled websites, forms, links, or C2 infrastructure, blocking it on the University network, or blocking it from connecting to the University VPN, can stop the attack for all users of the VPN. This allows the school to control the response timeline more acutely than if they report it to the service hosting the attacker's infrastructure, which may take hours to days to perform a takedown.

### Allows more strict firewall rules

The school can focus on authenticating the VPN, rather than having to accept any connection attempted on CAS. This means the school can block an entire species of traffic, and narrow down on traffic coming into the VPN endpoint.

### Protect students on less secure networks or infrastructure

The VPN could, do what VPNs do lmao.

### Adds a step to service attacks

Ultimately you can't prevent hacks. But the goal is always to make them more time consuming, harder to launch, harder to continue, less rewarding, more likely to be traced, more likely to be punished, and more harshly punished. It's to continuously raise the bar and motivate more attackers to stop trying.

# Closing

This is not unusual. I do not suspect there is any secretive goal or motive. It is a common practice for Universities to require this of their students, and it's an unfortunate artifact of the constant attacks against Universities, and the reality that the aggregate of users - regardless of individuals - are often not interested, diligent, or attentive enough to prevent common security pitfalls. The level of University access to devices with the complete client installed (this may differ for other clients, or mobile devices) is the same as the University has to its own devices on its own network, though it has less permissions (literal operational ability) to your device than it would to its own devices. This goes from what they see in the network traffic to remote device access.

We can work to achieve better and more convenient security features as a campus, while also maintaining debate on whether or not our current practices are the best.

Stay safe y'all, and hopefully this semester slays regardless of the rocky start!

> If you have any corrections, comments, or concerns, feel free to email [acm@pfw.edu](mailto:acm@pfw.edu) with the title of this article as the subject. If the University would like to add comments or corrections, please notify us in the same manner. Thank you!