---
layout: post
title: "Why you should start hacking Android"
permalink: /why-android-security
categories: Android
---

Android application security is like the land that time forgot. Mobile security is behind the times - issues like hard-coded sensitive data, unencrypted transmission of sensitive data, and other simple vulnerabilities abound. Billions of devices run Android applications, and only a handful of security researchers are seriously focused on analyzing them. Meanwhile, there's a wild bonanza in web application security, where some of the cutting edge research looks like the equivalent of a graduate level thesis! Why does reality look like this? I don't know, but I'm convinced that Android app security has been underappreciated and should see a surge of interest soon. Let me share what has convinced me to focus my energy on Android security.

First, let's look at a graph from HackerOne's 2020 annual report showing how many hackers on the platform hack mobile applications:

![HackerOne 2020 Report Graph](/public/2020-08-31-HackerOne-Annual-Report-2020-Graph.png)
*HackerOne 2020 Annual Report*

That dark blue sliver, around 3% of the graph, is the amount of interest that exists in Android application security compared to other assets on HackerOne. While the folks looking at web apps spend substantial effort to find undiscovered assets, Android apps sit alone in the corner, unloved. HackerOne even tried to drum up more interest in Android Security with [#AndroidHackingMonth blogposts](https://www.hackerone.com/blog/AndroidHackingMonth) in February 2020, and one researcher who started looking at Android after seeing these blogposts (that's less than 6 months ago) already [scooped up $30k in bounties](https://abss.me/posts/fcm-takeover/) from a single vulnerability. Let's check BugCrowd's 2020 report:

![BugCrowd 2020 Report Graph](/public/2020-08-31-BugCrowd-Annual-Report-2020-Graph.png)
*BugCrowd 2020 ITMOAH Report*

Huh, BugCrowd's graph implies that Android is where hackers are "weakest". Not much competition there either. Let's look elsewhere, at Sebastian Porst (Google Play Protect's engineering manager) presenting at Bugcrowd's LevelUp 0x05. The two interesting tidbits I picked up on in the 4 minutes of video between minute 7 and minute 11 of this talk are that **1.** 75% of the bug bounty payments that Google made on their Google Play Security Reward program occurred in the 90 days before the presentation (so between July and Oct 2019), which means interest was ramping up and **2.** The number of vulnerabilities fixed in the 3 years prior to this talk (so 2016-2019) may make the Android app ecosystem security initiative the biggest application security program to date. Conveniently, Sebastian proceeds to outline different bug categories that you can start looking for.

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/51S8PeuzlmI?start=420" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
*BugCrowd LevelUp 0x05 Android app vulnerabilities presentation*

So basically Google's Android bug bounty program, which covers any app with over 100 million installs (that's around 500 targets, according to [androidrank.org](https://www.androidrank.org/android-most-popular-google-play-apps?category=all&sort=4&price=all)), is known to have many vulnerabilities and pays well. Okay, sounds like that's motivation enough, but there's more data from Google. This one comes directly from the [Google Play Security Rewards Program website](https://www.google.com/about/appsecurity/play-rewards/). To summarize the chart below, Google is saying that easy-to-find vulnerabilities exist in Android apps, and instead of classifying them as out of scope, Google instead describes these vulnerabilities and still offers a reward. Very kind of them!

![Google Play Security Rewards Known Issues chart](/public/2020-08-31-GooglePlaySecurityRewards.png)
*Google Play Security Rewards Known Issues Chart*

Of course, that chart is only for the low hanging fruit. The more complete list of rewards contains higher rewards, naturally. And remember that HackerOne, BugCrowd, Intigriti, and other sites have additional Android targets, many of which are conveniently curated in this [Github repo](https://github.com/arkadiyt/bounty-targets-data).

![Google Play Security Rewards full chart](/public/2020-08-31-GooglePlaySecurityRewardsFull.png)
*Google Play Security Rewards Chart*

Oh, and let's wrap up by reminding everyone that you can download and decompile Android applications, instrument them with Frida on a rooted device, and basically examine all the ins and outs of the application that you might want to see. How many other target assets can claim to be this close to whitebox open-source testing? I don't see many hands being raised.

Let's recap: we have many targets, a large number of expected vulnerabilities, decent rewards, not much competition, and open source assets ready for examination. Not to mention that it's possible to download hundreds of applications and use scripts to statically analyze the applications quickly. I'm sold, and in the coming months, I hope to share more info about my adventures looking at Android application security. If you can't wait to dive in, take a look at [@0xteknogeek's](https://twitter.com/0xteknogeek) [#AndroidHackingMonth Guide](https://www.hackerone.com/blog/androidhackingmonth-intro-to-android-hacking) for a decent primer on how to get started.
