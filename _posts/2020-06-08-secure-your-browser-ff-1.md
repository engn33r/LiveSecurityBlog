---
layout: post
title: "Secure your browser: Firefox, part 1 (intermediate)"
permalink: /secure-firefox-browser-1
categories: Securing_your_web_browser
tags: browser firefox addons extensions web http dns
---

*Web browsers are the most common window to the internet, but default browser settings are not designed for security or privacy. This post is the first in a series exploring ways to improve your web browser’s security configuration.*   


To start, what security and privacy risks can a web browser play a part in? Unfortunately, there are many, including:
- **[Phishing attacks:](#phishing)** resulting in stolen credentials
- **[Drive-by downloads:](#drive-by_downloads)** resulting in ransomware or malware that can ruin your computer
- **[Man-in-the-middle attacks:](#mitm)** resulting in a third-party observing your communications, compromising accounts and sensitive data
- **[Cryptojacking:](#cryptojacking)** resulting in your computer slowing down, and increasing your electricity costs while others profit
- **[Third-party trackers:](#trackers)** resulting in creepy ads, your personal data being warehoused by many companies, increasing the risk of identity theft


These risks <ins>can be reduced by you</ins>! You accept these risks if you do not secure your browser properly. There are other risks that you can't do much about, like a government agency getting hacked or a company unknowingly giving your data to the third parties, but it makes sense to take control of the risks you can manage. So, how can you secure your browser?

### <a name="phishing"></a>Preventing phishing attacks

![Firefox security settings](/public/2020-06-08-ff-phishing.png)

Phishing is an attack where an attacker gets your sensitive credentials, such as your banking password, by tricking you to login to a fake website. Firefox has phishing protection built-in – you just need to activate it. The above screenshot shows where to find the setting in the Firefox’s “Preferences” area, but the full instructions are [on Mozilla’s website](https://support.mozilla.org/en-US/kb/how-does-phishing-and-malware-protection-work#w_how-do-i-use-the-phishing-and-malware-protection-features)

For additional protection, the antivirus maker BitDefender published a [Firefox extension](https://addons.mozilla.org/en-US/firefox/addon/trafficlight/) that can help prevent phishing by rating website links. I haven’t used this yet, but it could be useful if your are particularly concerned about this type of attack

### <a name="drive-by_downloads"></a>Preventing drive-by downloads

Drive-by downloads can force your browser to download malicious files without your knowledge, resulting in your viruses, malware, and other nasty results. Drive-by downloads prey on software bugs in your browser, usually in common pieces of software. The best thing you can do to reduce the number of browser software bugs is to disable software you don’t need. Specifically, Firefox plugins such as Java, Flash Player, Adobe Reader, or Quicktime should be [disabled or removed completely](https://support.mozilla.org/en-US/kb/disable-or-remove-add-ons#w_disabling-and-removing-plugins). Less code means less bugs. Another way to reduce the bugs in your code is by keeping your browser updated. In general, if a piece of software offer you an update, you should install the update!

### <a name="mitm"></a>Man-in-the-middle Attacks

A man-in-the-middle attack exists when an attacker controls a part of the connection between you and a website you visit, and therefore the attacker can see the data that you are sending to the website. For example, if you are connected to a free public Wi-Fi in a hotel, an attacker may unexpectedly control this Wi-Fi network. The best way to protect yourself is to use encrypted connections. The [HTTPS Everywhere extension](https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/) forces websites to use HTTPS, a form of encrypted connection, if the website supports this technology. However, HTTPS normally only protects the data you send to websites, meaning a man-in-the-middle attack could still see the URLs you are visiting. You can add further protection by enabling DNS over HTTPS, which will encrypt the URLs that you are visiting. This is another setting you can change in the “Preferences” area of Firefox. Mozilla has a detailed guide showing [how to enable DNS over HTTPS](https://support.mozilla.org/en-US/kb/firefox-dns-over-https#w_manually-enabling-and-disabling-dns-over-https)

### <a name="cryptojacking"></a>Preventing Cryptojacking

Cryptojacking is an attack where an attacker uses your computer to mine cryptocurrency to make the attacker money. An attacker can do this by putting cryptomining code into a website, such as through an advertisement. Fortunately, Firefox has built-in cryptojacking protection, seen below, which should be enabled – see [Mozilla’s guide explaining how to do that](https://blog.mozilla.org/futurereleases/2019/04/09/protections-against-fingerprinting-and-cryptocurrency-mining-available-in-firefox-nightly-and-beta/#post-2620). Going further, perhaps the best single Firefox extension I can suggest to anyone is [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/), which is my favorite adblocker. This extension alone can protect against several types of attacks listed here.

![Firefox tracker protection](/public/2020-06-08-ff-trackers.png)

### <a name="trackers"></a>Preventing third-party trackers

Third-party trackers follow you around the internet as you visit different sites, sometimes even following you to other devices (such as your phone), so that they can serve you targeted advertisements. The companies that collect this information from trackers can also sell that data, either to advertisers or malicious users, so it’s best to block these trackers when possible. The first step to blocking trackers is to use Firefox’s built-in protection, seen in the screenshot above. As you may have guessed, [Mozilla has a guide on how to do that](https://support.mozilla.org/en-US/kb/content-blocking). To go beyond Firefox’s protections, I suggest using the [Cookie Autodelete extension](https://addons.mozilla.org/en-US/firefox/addon/cookie-autodelete/) and the [Privacy Badger extension](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/) to add further layers of protection to block any trackers that slip past the built-in Firefox protections.

### <a name="other"></a>Other best practices

This list only is only a brief summary of the many ways that your browser can be secured. For good measure, I will list a few other suggestions that can help further:
- Use strong, unique passwords and change them at least once per year. If your password is leaked (for example, if all the accounts for a certain website were leaked onto the internet), this limits the timeframe when another person may be able to access your account.
- Enable [Firefox’s breach notifications feature](https://support.mozilla.org/en-US/kb/firefox-lockwise-alerts-breached-websites). This will alert you if a website has been publicly hacked and the account information leaked onto the internet.
- Change your default search engine to [DuckDuckGo](https://duckduckgo.com/). Knowing that Google makes over 80% of all its income from ads, the privacy-centric DuckDuckGo is a great choice for anyone wishing for a little less Google in their life.
- Using the [private browsing feature](https://support.mozilla.org/en-US/kb/private-browsing-use-firefox-without-history) is always a good idea if you don’t need to save your browsing history. When private browsing is enabled, cookies and other data will automatically be deleted when you close Firefox. This doesn't make everything you do completely private, but it's a helpful feature.

-----

If these security tweaks were all common sense for you, be sure to check out the [advanced Firefox browser security post](/secure-firefox-browser-2) for additional security improvements.
