## Firefox configuration

[ankerfox user.js](https://raw.githubusercontent.com/arkenfox/user.js/master/user.js)

### `omni.ja`
> This **Mozilla-optimized zip** file contains most of the default configuration used by Firefox.
>
> As an example, network calls to `firefox.settings.services.mozilla.com` and `content-signature-2.cdn.mozilla.net`

- [Editing contents of omni.ja](https://wiki.archlinux.org/index.php/Firefox/Privacy#Editing_the_contents_of_omni.ja)
- [Web Browsers | PrivacyTools](https://www.privacytools.io/browsers)

#### Firefox *crash reports* + prebuilt *extensions*
```
/usr/lib/firefox/browser/features/*
/usr/lib/firefox/crashreporter
/usr/lib/firefox/minidump-analyzer
/usr/lib/firefox/pingsender
```
#### *scripts* & *user.js* links
- [arkenfox](https://github.com/arkenfox/user.js) +
[*Raw* `user.js`](https://raw.githubusercontent.com/arkenfox/user.js/master/user.js) +
[*Raw* `updater.sh`](https://raw.githubusercontent.com/arkenfox/user.js/master/updater.sh) +
[*Raw* `prefsCleaner.sh`](https://raw.githubusercontent.com/arkenfox/user.js/master/prefsCleaner.sh)
- [12bytes `user-overrides.js`](https://codeberg.org/12bytes.org/Firefox-user.js-supplement) + 
[*Raw*](https://codeberg.org/12bytes.org/Firefox-user.js-supplement/raw/branch/master/user-overrides.js)

## Useful add-ons
- [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/) - Very customizable ad/content blocker using filter lists
- [uMatrix](https://addons.mozilla.org/en-US/firefox/addon/umatrix/) - Is also a powerful content blocker that provides more granular control than uBlock
- [Cookie AutoDelete](https://addons.mozilla.org/en-US/firefox/addon/cookie-autodelete/) - Works only if you set `privacy.clearOnShutdown.cookies` to `false`
- [ClearURLs](https://addons.mozilla.org/en-US/firefox/addon/clearurls/) - Strips many tracking parameters, such as the `utm_*`
---

- [HTTPS Everywhere](https://addons.mozilla.org/en-US/firefox/addon/https-everywhere/) - Redirect to https page if possible
- [HTTPZ](https://addons.mozilla.org/en-US/firefox/addon/httpz/) - Similar, but more smart
- [CanvasBlocker](https://addons.mozilla.org/en-US/firefox/addon/canvasblocker/) - Don't needed anymore as you use arkenfox `user.js`
- [Decentraleyes](https://addons.mozilla.org/en-US/firefox/addon/decentraleyes/) - Serve local copies of JavaScript rather than fetching them from a CDN.
- [Privacy-Oriented Origin Policy](https://addons.mozilla.org/en-US/firefox/addon/privacy-oriented-origin-policy/) - Preven Firefox from sending unnecessary headers
- [Privacy Badger](https://addons.mozilla.org/en-US/firefox/addon/privacy-badger17/) - Automatically learns to block invisible trackers
- [Privacy Possum](https://addons.mozilla.org/en-US/firefox/addon/privacy-possum/) - Provides additonal headers, eTags blocking
- [I don't care about cookies](https://addons.mozilla.org/en-US/firefox/addon/i-dont-care-about-cookies/) - Get rid of cookie warngings from websites
- [Temporary Containers](https://addons.mozilla.org/en-US/firefox/addon/temporary-containers/) - Open tabs in different containers
---

- [Stylus](https://addons.mozilla.org/en-US/firefox/addon/styl-us/) - Custom CSS styles rules for certain websites
- [Vimium C](https://addons.mozilla.org/en-US/firefox/addon/vimium-c/) - Adds *vim* shortcuts to browser
- [Buster](https://addons.mozilla.org/en-US/firefox/addon/buster-captcha-solver/) - Captcha solver for humans
- [KeePassXC-Browser](https://addons.mozilla.org/en-US/firefox/addon/keepassxc-browser/) - Official plugin for the KeePassXC
- [Dark Reader](https://addons.mozilla.org/en-US/firefox/addon/darkreader/) - Dark mode for every website
- [Redirector](https://addons.mozilla.org/en-US/firefox/addon/redirector/) - Redirect links

## Related Links
- [Firefox/Privacy (Archwiki)](https://wiki.archlinux.org/index.php/Firefox/Privacy)
- [Browser extensions (Archwiki)](https://wiki.archlinux.org/index.php/Browser_extensions)
- [Choose your browser carefully](https://unixsheikh.com/articles/choose-your-browser-carefully.html#tweaking-firefox)
- [Firefox Configuration Guide for Privacy Freaks and Performance Buffs](https://12bytes.org/articles/tech/firefox/firefoxgecko-configuration-guide-for-privacy-and-performance-buffs/)
- [Essential privacy (and other) addons](https://digdeeper.neocities.org/ghost/addons.html)
