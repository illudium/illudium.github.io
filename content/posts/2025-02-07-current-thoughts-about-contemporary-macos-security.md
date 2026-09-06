---
title: "Current Thoughts About Contemporary Macos Security"
date: 2025-02-07T00:00:00
draft: false
---
# Current Thoughts about Contempoary macOS Security
Original Publication Date: 2024-02-07
---
## Current Thoughts about Contempoary macOS Security

When it comes to managing Security for macOS in a corporate environment, the first critical requirement is to understand that 
macOS is not Windows. Of course this is known and understood by all veteran Mac Admins, but it bears repeating
for anyone who might have extensive experience handling Security policies and protections for Windows,
but is newly tasked with pursing the same for macOS.

Continuing from the above understanding, it's important to ensure that the proper tools and practices are pursued, 
for effectively protecting macOS, and avoid any misunderstandings (or worse disasters) that can arise 
by attempting to treat two very different computer operating systems as the same.

One thing that protecting both OSes (macOS and Windows) have in common, is that the best security is a layered approach, and with that in mind: Your first best layer of protection is user awareness and training (Security awareness and best-practices for users).

In terms of Security researchers who represent expertise most worthy of your attention, I recommend you devote some time and attention to Patrick Wardle (his website is https://objective-see.org/index.html) and Phil Stokes (his blog is here: https://sqwarq.wordpress.com). 
Which is not intended to imply any disregard for anyone else ! But please do your own research, and be a particularly careful consumer when it comes to bold statements or claims relating to the security of macOS.

An understanding of the native security capabilites of macOS and Apple hardware, should cover at least ASLR, SIP as well as Gatekeeper, Notarization, and XProtect. I recommend further reading listed at the end of this post.

In the current day and age (and probably as far back as the last 5-7 years), another critical layer of a meaningful security posture is DNS-level protection/filtering. Common choices here are Netskope, DNSFilter, Cisco Webroot (look for any history of compatibiility issues), and Zscaler amongst others. At a smaller scale, you might care to trial NextDNS.

If you're working with Jamf (or not, it's not a requirement), I recommend you look into Jamf Protect  (for historical context, read about the past work of Patrick Wardle).

In terms of Security Software for macOS, opinions differ greatly here.
Some like to believe that nothing more is needed than the native features of the Apple software and hardware. Given the state of the current threat landscape (for technology and online communications), such a perspective is probably overly-confident and probably unduly biased in favor of Apple.
That said, in my opinion, many common "Anti-Virus" offerings don't actually offer anything that specifically protects against the current real-world threats that exist for - and are specific to- macOS.  In other words, I'm not entirely convinced that many of them accomplish anything ...that is properly or thoroughly effective. Beware of products that appear to "check a box" (eg when it comes to compliance requirements), and please look carefully into whether the product does provide the intended goal of effectively protecting macOS.

However, so-called "Next-Gen" security software can indeed provide real, worthwhile protections. Common choices here with cross-platform support are Crowdstrike Falcon https://www.crowdstrike.com/platform/endpoint-security/, and Sentinel One https://www.sentinelone.com
If you need to deal with regulatory compliance, I recommend you read Apple's article very nicely directing us to the [macOS Security Compliance Project (mSCP)](https://support.apple.com/guide/certifications/macos-security-compliance-project-apc322685bb2/web)

Jamf also has information here: Enforcing CIS, STIG and More to Meet Auditor Standards
Additional considerations should of course include keeping your fleet up to date, which means MDM is a requirement. While I've mentioned Jamf, other popular choices (also not limited to the MDM exclusively) for macOS are Kandji, Mosyle, Addigy, and SimpleMDM. However, if you're specifically Sys/DevOps (GitOps, CF management) oriented in your practices, you could do well to look at FleetDM, Zentral, or even roll your own with MicroMDM and perhaps AutoPkg, Munki, Chef, Puppet, Salt or Ansible.
At this time, while I use Intune extensively with Windows, it would not yet be a first choice for macOS. It might be fine for your needs for iOS
Additionally, you should of course choose a trustworthy Identity Provider and configure it appropriately.  

Additional information about iOS security is available from Apple.
Additional further reading from Apple:
https://support.apple.com/guide/security/welcome/web,  https://www.apple.com/macos/security/ , https://support.apple.com/guide/security/protecting-against-malware-sec469d47bd8/web, as well as https://support.apple.com/guide/security/hardware-security-overview-secf020d1074/1/web/1
