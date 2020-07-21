---
layout: post
title: "Secure your browser: Chrome"
permalink: /secure-chrome-browser
categories: Securing_your_web_browser
tags: browser chrome addons extensions web http dns
---

*For details about securing Firefox, see the equivalent [Firefox post](secure-firefox-browser-1)*

Firefox is my preferred browser, but Chrome is currently the clear marketshare leader among browsers. As of early 2020, around 65% of browser usage is Chrome. In addition, at least a couple of other popular web browsers, the Brave browser and the new Microsoft Edge browser, borrow from Chrome’s codebase.

### Chrome vs. Chromium

First, we must clarify the difference between the Chrome browser and the Chromium browser, because a lot of confusion exists between the Google's two. open source project that is the foundation for Google Chrome. Chrome uses the Chromium source code as well as Google's proprietary modifications. Therefore, while Chromium is licensed as open source software, Google Chrome is licensed as proprietary freeware.

### Can't have Chrome without the Google

If you are concerned about privacy as well as security, remember that Google creates the Chrome browser. Google makes the majority (~80%) of its revenue from advertisements. Because targeted advertising is more valuable, Google has incentive to gather data on web users to better target advertisements. By default, Chrome has some built-in features that can reduce a user’s privacy. Fortunately, there are several Chromium project forks that are built for improved privacy. For example, “[Ungoogled Chromium](https://github.com/Eloston/ungoogled-chromium)” removes google dependencies in the Chromium code, in addition to other privacy improvements. If you choose to use this Chromium fork, I highly recommend reviewing [the FAQ](https://ungoogled-software.github.io/ungoogled-chromium-wiki/faq#can-i-install-extensions-or-themes-from-the-chrome-webstore), as it explains how to overcome common hurdles, such as installing extensions from the Chrome web store. While the rest of this article will reference Chrome, Chromium can benefit from the same security improvements.

### Don’t login to Chrome

This first suggestion is obvious if you wish to minimize Google's data collection. Logging into the Chrome browser for extended periods can provide Google with insight into your web browsing habits. Note that in the most recent Chrome releases, you are automatically logged into Chrome when you login to Google services, such as Gmail, so logging in to Chrome can happen without you even noticing.

### Add features to Chrome shortcut

Some of the security features in Chrome cannot be modified in a menu of settings, but instead need to be arguments provided to Chrome when Chrome is started. To provide arguments to Chrome, you need to find the shortcut that you use to start Chrome, right click this shortcut, and select “Properties” (or “Edit”, depending on your OS), and change the path or command that starts Chrome. Several examples of features that can be added with this approach are:
- Opening Chrome in private browsing mode (AKA “incognito” in Chrome), where no history is saved, requires passing an argument to chrome, specifically `-incognito`
- To use DNS over HTTPS, use the argument `--enable-features="dns-over-https<DoHTrial" --force-fieldtrials="DoHTrial/Group1" –force-fieldtrial-params="DoHTrial.Group1:server/https%3A%2F%2Fcloudflare-dns%2Ecom%2Fdns-query/method/POST"`
- If you wish to disable canvas fingerprinting entirely (which might not be the best approach, compared to spoofing a false canvas fingerprint value), you can use the `--disable-reading-from-canvas` argument


After deciding which features you want to enable, you may end up with a shortcut to start Chrome that contains a list of command arguments such as the following:
```
/usr/bin/google-chrome-stable %U -incognito --enable-features="dns-over-https<DoHTrial" --force-fieldtrials="DoHTrial/Group1" --force-fieldtrial-params="DoHTrial.Group1:server/https%3A%2F%2Fcloudflare-dns%2Ecom%2Fdns-query/method/POST" --disable-reading-from-canvas
```

### Extensions

Fortunately, many of the browser extensions that I am familiar with in Firefox are also found in Chrome. Below is a list of Chrome extensions I prefer, but I have chosen most of these because I am familiar with using them on Firefox.
- [uBlock Origin](https://chrome.google.com/webstore/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm): blocks ads
- [Privacy Badger](https://chrome.google.com/webstore/detail/privacy-badger/pkehgijcmpdhfbdbbnkijodmdjhbjlgp): blocks third party trackers
- [Cookie Autodelete](https://chrome.google.com/webstore/detail/cookie-autodelete/fhcgjolkccmbidfldomjliifgaodjagh): Automatically deletes cookies after leaving a website
- [HTTPS Everywhere](https://chrome.google.com/webstore/detail/https-everywhere/gcbommkclmclpchllfjekcdonpmejbdp): Forces sites to use HTTPS if supported
- Fingerprint Defender for [audiocontext](https://chrome.google.com/webstore/detail/audiocontext-fingerprint/pcbjiidheaempljdefbdplebgdgpjcbe), [fonts](https://chrome.google.com/webstore/detail/font-fingerprint-defender/fhkphphbadjkepgfljndicmgdlndmoke), [WebGL](https://chrome.google.com/webstore/detail/webgl-fingerprint-defende/olnbjpaejebpnokblkepbphhembdicik), [canvas](https://chrome.google.com/webstore/detail/canvas-fingerprint-defend/lanfdkkpgfjfdikkncbnojekcppdebfp): These extensions prevent websites from fingerprinting your browser and tracking your movements across the web
- [BitDefender Traffic Light](https://chrome.google.com/webstore/detail/trafficlight/cfnpidifppmenkapgihekkeednfoenal?hl=en):  Helps prevent phishing by rating website links

### Use chrome://flags??

The most confusing part of my exploration of improving Chrome’s security is the lack of information about privacy-related and security-related flags that can be set on the special `chrome://flags` page. I assumed that this is the Chrome equivalent of Firefox’s `about:config`, but it appears to allow for much less granular control. I couldn’t even come up with a list of 5 good security features to enable on this page, so if I’m missing something obvious, please [reach out](https://erikelbieh.com/contact) and let me know! My current conclusion is that Google is targeting the average user who wants technology that "just works", even at the cost of privacy, and therefore they don't see the value in providing detailed configuration settings.

### Other best practices

This list only is only a summary of the many ways that your browser can be secured. For good measure, I will list a few miscellaneous suggestions that can also help for various reasons:
- Use strong, unique passwords and change them at least once per year. Weak or compromised passwords are still one of the most common ways that security is broken. If your password is leaked (for example, if all the accounts for a certain website were leaked onto the internet), this limits the timeframe when another person may be able to access your account.
- If you use Chrome on your mobile device, secure your mobile browser with the same steps used here. Some of these settings require a different process to set on your mobile device, such as always opening Chrome in private browsing (AKA incognito) mode.
- Change your default search engine to [DuckDuckGo](https://duckduckgo.com/). Since Google attempts to target ads by gathering data on users, the privacy-centric DuckDuckGo is a great choice for anyone wishing for a little less Google in their life. Or if you want an alternative to DuckDuckGo, you could try [Searx](https://searx.me/).
- Test your browser to make sure your expectations are aligned with reality. Some useful website are [Panopticlick](https://panopticlick.eff.org/) (to check your browser’s fingerprint), [Cloudflare’s ESNI checker](https://www.cloudflare.com/ssl/encrypted-sni/) (to check DNS over HTTPS), and [BrowserLeaks](https://browserleaks.com/) (to check a variety of browser settings).

Overall, I’d still suggest Firefox as the best web browser for someone who wants to customize their browser for security and privacy needs. The lack of easy configuration for multiple useful settings (always private browsing, DNS over HTTPS) create a privacy and security drawback in Chrome. After all, there is a reason why the [Tor browser](https://www.torproject.org/) is built on Firefox. If you're interested in switching to Firefox, check out the first article explaining [how to secure Firefox](secure-firefox-browser-1) and compare those features with Chrome's.
