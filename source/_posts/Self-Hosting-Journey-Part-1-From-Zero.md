---
title: Self-Hosting Journey - Part 1 - From Zero
date: 2024-12-22 15:18:35
author: Draka
categories:
  - Self-Hosting
tags:
  - Cybersecurity
  - Privacy
  - Guide
  - Tutorial
  - Tech
---
Hi! In this blog post series I want to share my self-hosting project. I will start by explaining, even for beginners, what self-hosting is and the reasons that led me to this project. I will share all my reasoning, thoughts and choices throughout the various posts, but now let's not waste time and get started right away.

## What is Self-Hosting?
Self-hosting refers to the practice of hosting and managing applications on your own servers, rather than relying on Software-as-a-Service (SaaS) cloud solutions. For those less familiar with technology, you might not realize that many of the services you already use are actually SaaS. In today's world, nearly everyone relies heavily on cloud services. Below is a non-exhaustive list of commonly used SaaS:

- Google Photos, Google Drive, iCloud, and similar services for automatic backups of data, chats, and photos from smartphones
- Dropbox, Google Drive, iCloud, OneDrive, and similar platforms for storing and sharing files
- Google Workspace (Docs, Sheets, Calendar), Microsoft 365 (Word, Excel, PowerPoint, Teams)
- Outlook, Gmail, Yahoo, and similar services for managing email
- Netflix, Spotify, Prime Video, and similar services for streaming videos and music

All of these services have self-hosted alternatives that you can run on your hardware (a mini-pc, a laptop, a Raspberry PI, or other board), giving you complete control and autonomy over your data and applications.

{% asset_img self_hosting_1.png 620 620 %}

## Why Start Self-Hosting?

If I were asked to provide reasons why self-hosting can be beneficial, I would list the following:

- **Privacy:** By avoiding third-party services, you prevent sharing your data with external entities, helping to maintain your privacy. This is a complex topic that I want to further discuss in the next section.
- **Security:** By managing your own infrastructure, you can achieve a very high level of security. On the other hand, when using third-party services, we must blindly trust them, and we have to consider that their attack surface is certainly much larger than ours. Moreover, since we have seen data breaches occur even with the most secure and protected companies in the past, I would recommend you to self-host your environment (obviously if you are able to follow the security best practices).
- **Cost-Effectiveness:** Self-hosting eliminates the need for recurring subscription fees, instead you will still incur costs for electricity and hardware. 
- **Customization and Flexibility:** Self-hosting allows you to fully customize your solution to meet your specific needs, giving you complete control over your services. You can choose which service to install and sometimes also customize them.
- **Learning Experience:** Self-hosting opens up many opportunities to learn about new technologies, protocols, and tools. It’s an excellent chance to expand your knowledge and skill set.
- **Fun:** This is subjective, but if you're passionate about computers and technology, self-hosting would be for sure an enjoyable and rewarding experience.

Self-hosting isn't without its challenges. Having full control over your data and services means you are solely responsible for securing your infrastructure. You need to back up and manage your data, keep your software up to date, and maintain both your hardware and software. You also need to purchase the necessary devices and ensure they run 24/7, covering the cost of electricity.

### Privacy and Security

Privacy is usually one of the main reasons that move people to start self-hosting its own services, and so I want to spend some words in favor of that. 
Maybe someone is just thinking: “I have nothing to hide. Why should I care about my privacy?”.
It is likely that you do not know what privacy is. Privacy is about control over personal space and information, not about hiding wrongdoing. Privacy is the assurance that your data is only seen by the parties you intend to view it.
It’s important to distinguish between privacy and secrecy. For example, while we all know what happens in a bathroom, we still close the door. This is because we value privacy, not secrecy. There are certain aspects of our lives, such as personal health information or sexual behavior, that we wouldn’t want the whole world to know, and that’s perfectly okay. The need for privacy is entirely legitimate, and it’s a fundamental part of being human. Privacy is about empowering you to control your own information, not about concealing secrets.
Moreover privacy is a human right which is intimately linked with our many notions of freedom, it is inherent to all of us, and we are entitled to.
Privacy is also strictly related to security and anonymity, but they must not to be confused.
- **Security** is the ability to trust the applications you use, it is based on the CIA paradigm, **Confidentiality**, **Integrity**, and **Availability**
- **Anonymity** is the ability to act without a persistent identifier, that allow not to be tied to a real identity.

After this explanation, we can return to our main topic: self-hosting.  
Self-hosting does not automatically "solve" the problem of privacy and security.  
If you don’t want to stop using internet services, which in today’s world would mean becoming disconnected and marginalized from society, you cannot achieve full security and privacy.  
Security, privacy, and usability are a trade-off, and balancing them is one of the most difficult tasks to face. However, this must be our objective.  
I believe that self-hosting is a powerful "tool" that gives you the opportunity to gain better control over this trade-off and helps you bring it closer to your set point.

If I moved you interest about the privacy topic I strongly recommend you to have a look at: https://www.privacyguides.org/en/

### Further Considerations

Have you ever thought about the possibility that your cloud accounts could be banned by "mistake", causing you to lose all your data, sometimes your reputation, and even potentially get into legal trouble?  
A few months ago, my TikTok account was banned by an automatic algorithm without any valid reason. I was lucky, after filing a claim, my account was reinstated in a few months. I had used TikTok occasionally and mainly passively (never posted a video or commented on a post), so I didn’t care much about the account. However, some people today rely on these accounts for work, and a ban could have a significant impact on their business (for example, think of an influencer).  
I repeat, I was fortunate that I didn’t use the account extensively, but Mark was not as lucky as I was. Mark, a man from San Francisco, was banned by Google after he sent an image of his son's genitals to a doctor via his smartphone, using Google services. The image was flagged by an automatic algorithm, and he was banned for sharing sexual abuse material. As a result, Mark was blocked from all Google services, including voice and data traffic on his mobile phone, since it was connected to Google Fi. Furthermore, he was investigated and had to undergo a judicial process, which ultimately ended in his acquittal.

Full article at: https://www.nytimes.com/2022/08/21/technology/google-surveillance-toddler-photo.html

## Common Use-Cases

There are many possible self-hosting scenarios. Each user creates their environment based on their needs and desires. The following are some of the most common use cases:

### 1. Personal Website or Blog

Using self-hosted platforms like **WordPress**, **Ghost**,  **Jekyll** or **Hugo**, allow you to easily create and host your own website. Hosting your website on your own server gives you complete control over its design, functionality, and security.

### 2. Private Cloud Storage

If you're looking for a way to store your files securely and privately, a self-hosted cloud storage platform like **Nextcloud** or **OwnCloud** is an excellent choice. You can sync your files across devices, share files securely, and maintain full control over your data.

### 3. Media Streaming Server

Self-hosting a media server is perfect for organizing and streaming your personal media library. **Plex** and **Jellyfin** are popular platforms that let you host your own media server and stream it to various devices, all while keeping your data private.

### 4. Email Server

Hosting your own email server provides greater control and privacy over your communication. You can use software like **Postfix**, **Dovecot**, or **Mail-in-a-Box** to set up your server.

### 5. Home Automation

Self-hosting in the realm of home automation allows you to manage and customize your smart home devices without relying on third-party cloud services. By hosting platforms like **Home Assistant** or **OpenHAB** on your own server, you can create a highly personalized and secure smart home environment, automate routines, and integrate a variety of devices all while keeping your data private and within your control.

## What you Need to Get Started

Starting with self-hosting can be as simple or as complex as you want it to be. Basically you need only a single board or pc and an internet connection, but if you want you can let your imagination roam and add as many device as you want.

For most of the cases, you don't need an expensive server, especially when you are just starting. There are several options, depending on the scope of your project:

- **Personal Computer:** An old PC or laptop can work.
- **Raspberry Pi:** For low-power, cost-effective setups, a Raspberry Pi or a similar board is an excellent option.
- **Dedicated Server or VPS:** You could also use a dedicated server or a Virtual Private Server (VPS) from a provider like DigitalOcean or Linode. This option could be convenient, but I would not recommend it. This option shifts some responsibilities to your VPS provider, potentially reducing some of the self-hosting advantages discussed before and adding additional costs for renting the VPS.

{% asset_img self_hosting_2.png 400 400 %}

## My Self-Hosting Project
In my self-hosting project, I have set several key goals that align with my professional growth. Below is an outline of what I aim to achieve:

**1. Learn and Improve Skills**
- Set up a small-to-medium-sized corporate-like network.
- Configure key security systems: SIEM, IDS/IPS, and firewall.
- Automate infrastructure deployment using Infrastructure as Code (IaaC) tools like Terraform and Ansible.
- Perform penetration tests to assess the security of the deployed infrastructure.
- Build a security training lab for hands-on learning and practice.

**2. Enhance Security and Privacy**
- Transition from cloud services to self-hosted solutions where possible.
- Use privacy-oriented protocols (e.g., DNS over HTTPS, VPN) for home network traffic.
- Host a personal VPN to add security when connecting to public networks.

**3. Save Money**
- Replace paid services with free self-hosted alternatives (e.g., file storage instead of Google Drive).
- Choose low-power, silent hardware to reduce energy costs and noise.

Whether you're a beginner or have some experience, you're in the right place. Join me on this journey where I’ll share valuable insights and practical tips of any kind, covering everything from hardware selection and benchmarking to choosing the right application tools and implementing cybersecurity-driven hardening techniques. 

Stay tuned for the next post! 👋✨
