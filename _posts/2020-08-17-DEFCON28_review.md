---
layout: post
title: "DEF CON 28 Highlights"
permalink: /DEFCON28
---

The first year of virtual DEF CON wrapped up last week, and what a firehose of information it was! I first must admit this was my first DEF CON where I was watching talks live (does watching a recorded talk on Twitch count as live?) as opposed to on YouTube after the event. Overall, I was impressed with how smoothly the event ran (or at least the parts that I saw). One perk of the online conference was that the 30 minute Q&A sessions seemed to move faster and more smoothly than in-person Q&As, and 30 minutes was enough to ask quite a few questions! The five talks that I highlight below are not in any particular order, since picking highlights is always a matter of opinion anyway.

![DEF CON 28 logo](../public/2020-08-17-defcon2020.jpg)

1. I think Joshua is rightfully getting substantial attention for his "When TLS hacks you" talk, as this appears to be a new web security attack. A summary of this new attack surface is SSRF over TLS, but I think the idea of using TLS for web attacks is relatively unexplored in itself. Joshua's Q&A session was very relaxed and indicated that he hadn't poked around this new attack surface fully, which leaves a lot of room for others to fill in the gaps and move this further. On a related note, the "Domain Fronting Using TLS 1.3" talk by Erik Hunstad (which also featured novel research!) also found a new way to use TLS, and I appreciate the creativity of these researchers using technology that's in plain sight in new ways.

    <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/qGpAJxfADjo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

2. Having spent some time diving into the depths of the Bluetooth core specification, I have been keeping track of the new Bluetooth-related CVEs that have been popping up over the last several years (summarized in [this blog post](bluetooth-cves)). After unveiling InternalBlue at 35C3 a couple years ago, Jiska presented with Francesco Gringoli about a creative new attack on Bluetooth/WiFi combo chips. Since space is at a premium in smartphones, and because WiFi and Bluetooth operate at the same frequency, most phones today use combination chips that implement both WiFi and Bluetooth. However, the phone has a clock that coordinates which protocol is able to transmit to avoid interference, and it's this coordination mechanism that was attacked. Since phones will not be moving away from Bluetooth/WiFi combo chips (because of how compact and cheap they are), this and similar bugs at the intersection of different technologies will continue to be an interesting research area.

    <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/GZd66uVGKn8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

3. Server-side template injection (SSTI) was something I first learned about thanks to PortSwigger's fantastic [Web Security Academy](https://portswigger.net/web-security), and I suspect it is underrated because many of the findings to date rely on specific old versions of software to be running. However, discovering new vulnerabilities in the latest software versions is one solution to this! Munoz and Mirosh have had other awesome collaborations in the past ([Friday the 13th JSON Attacks](https://www.blackhat.com/docs/us-17/thursday/us-17-Munoz-Friday-The-13th-JSON-Attacks-wp.pdf) is worthwhile to read or skim), and this one produced over 30 CVEs - quite a collection. While the CVE in Microsoft Sharepoint seems to be getting a lot of press, there are many other well-known CMS software (HubSpot, Atlassian Confluence) that will likely be seeing the impact of this over the coming months, if they're not patched.

    <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/DeU3H6-9zCE" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

4. An astronaut. At DEF CON! With cool space photos!! Pam's talk was lots of fun and gave a lot of cool insider information about experiences and observations based on experience of American spaceflight. To paraphrase one thing Pam said, the security risks are magnified when human lives are involved, and the ISS has people living up there 24/7/365. There's obviously concerns with GPS security and other satellite hacking (a topic which got a substantially larger amount of interest this year), but this talk offered a perspective on the human element. Combining astronauts, space, and security just seems like a fantastic combo.

    <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/u5XLmlm59As" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

5. Pedro Umbelino and Joao Morais presented some awesome vulnerabilities they uncovered in some of the most installed Android apps - the Google camera application and Samsung's Find My Mobile application. The impact they were able to demonstrate with their findings was pretty impressive, as they put a fair bit of effort into adding capabilities to their proof of concept apps.

    <iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/qbj-4NXsE-0" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

**BONUS:** Let's face it, security can get pretty technical and no one likes being the dummy in the room. The War Story Bunker was an entertaining audio-only session on Discord where people chimed in with their stories of DEF CON and pen testing experiences. There were many epic wins and epic fails! Are you worried about deleting data during a pentest? Some of this year's stories described accidentally taking down entire networks over substantial geographic areas! With these crazy stories to compare to, I expect to feel a lot better about any of the (reasonable) mistakes I might make.

Unfortunately, there's no recording of the audio-only War Story Bunker session that I know of!
