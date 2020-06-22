---
layout: post
title: "Secure your browser: Firefox, part 2 (advanced)"
permalink: /secure-firefox-browser-2
categories: Securing_your_web_browser
tags: browser firefox addons extensions web http dns
---

*This post builds upon the [previous Firefox post](secure-firefox-browser-1) in this series, which discusses intermediate Firefox security improvements.*

### Proceed with caution

Why do I consider the Firefox security suggestions below to be “advanced”? First and foremost, some of the settings can and will break your normal web browsing experience. Being able to pinpoint the cause of such trouble, when you encounter it, requires patience and understanding of the underlying parts involved. The second and lesser reason is that I expect only a small minority of Firefox users delve into these more effort-intensive security modifications, which means these are roads less traveled. With that said, let’s look at how to add further layers of security and privacy to Firefox.

### about:config changes

You can set thousands of internal configuration settings with the about:config URL in Firefox. This is where many “advanced” Firefox settings can be altered. The best guide I know of summarizing which about:config settings to modify is at [privacytools.io](https://www.privacytools.io/browsers/#about_config), and I suggest using at least the first half of their suggested settings, if not all of them.


![If about:config isn't good enough for you, then pick your favorite user.js configuration](/public/2020-06-22-userjs-comparison.png)

### Use a secure Firefox user.js configuration

If you want to modify dozens of about:config settings to values that have already been reviewed by a security-minded community, try using a custom user.js configuration file. The user.js file is read when Firefox starts up and sets various values found on the about:config page. The number of configuration values set in these custom user.js files can be a bit daunting to examine, so I would recommend either testing these in newly created profiles or skimming the comparison of [popular user.js projects](https://jm42.github.io/compare-user.js/). The links to the corresponding user.js projects are also found on that page. Anything that the user.js file can configure can also be configured manually using about:config. So if using an intense user.js file will impact your web browsing activities too much, consider either a simplified user.js file like [SecureFox](https://github.com/yokoffing/Better-Fox/blob/master/SecureFox.js) or manually configuration of important settings. The settings below are ones which I have only seen set in user.js files rather than tutorials explaining manual modification of about:config:
- Disabling insecure TLS cipher suites
- Disabling WebAssembly and asm.js
- Disabling DOM features


### Securing your mobile browser

If you have a smartphone, odds are you have a web browser installed on it. But have you applied the same security hardening on your phone that you use on your primary computer? Some of the features in the mobile version of Firefox are set differently than the desktop version (such as, at the time of writing, DNS over HTTPS).

### Test your configuration

Regardless of how secure you want your web browser, it is important to confirm that the security improvements you think you have applied are actually working. Some tests can be run locally, such as by using a web proxy (such as Burp Suite or OWASP ZAP) or monitoring your network traffic. However, an easier approach is to use websites that test a certain aspect of your browser’s security - a few are below:
- Tests multiple protection mechanisms at [https://browserleaks.com/](https://browserleaks.com/)
- Tests DNSSEC and related settings at [https://www.cloudflare.com/ssl/encrypted-sni/ ](https://www.cloudflare.com/ssl/encrypted-sni/)
- Check if your browser fingerprint is unique at [https://panopticlick.eff.org/](https://panopticlick.eff.org/)
- Test rel=noopener setting at [https://mathiasbynens.github.io/rel-noopener/](https://mathiasbynens.github.io/rel-noopener/)

### Leverage extensions

You are no doubt aware that Firefox has an extensive collection of extensions that can be installed, but below are a few that may add extra protection:
- [NoScript addon](https://addons.mozilla.org/en-US/firefox/addon/noscript/): provides custom enable/disable for various webpage functions
- [Don’t touch my tabs!](https://addons.mozilla.org/en-US/firefox/addon/dont-touch-my-tabs/): forces rel=noopener on links
- Fingerprint defender addons: protect against fingerprinting of [WebGL](https://addons.mozilla.org/en-US/firefox/addon/webgl-fingerprint-defender/), [AudioContext](https://addons.mozilla.org/en-US/firefox/addon/audioctx-fingerprint-defender/), [Fonts](https://addons.mozilla.org/en-US/firefox/addon/font-fingerprint-defender/), and [Canvas](https://addons.mozilla.org/en-US/firefox/addon/canvas-fingerprint-defender/)
If you’re looking for even more extensions, [this is one site](https://12bytes.org/articles/tech/firefox/firefoxgecko-configuration-guide-for-privacy-and-performance-buffs#Required_add-ons_and_settings) that has some good recommendations

### Bonus points

Some of the extensions mentioned, including uBlock Origin, have enough settings to [necessitate a wiki](https://github.com/gorhill/uBlock/wiki)! Bonus points if you use uBlock in “Hard Mode” or fully utilize the full featureset of some of the other tools mentioned (such as NoScript). Please check out additional information sources if you’re serious about securing your browser – Firefox has an extremely large number of features. And if you’re still feeling insecure after all these measures, it might be time for you to investigate the Tor project...
