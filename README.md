# cordova-inappbrowser-iframetest

## Use Case

3rd party iframes contain different kind of links. Most of the links are navigation links between html pages of the same domain. The html pages will be openend in iframe. Exampe is a href="otherPage.html"
However, certain links in the iframe, especially to foreign content,  will be openend in cordova webview and "capture" entire app with no back navigation option. Example is a href="http://www.google.com" target=_blank

## Techncial background

### Standard behavior (no iFrame)

Links (a href) will be opened in cordova webview per default.

The InAppBrowser window behaves like a standard web browser, and can't access Cordova APIs. For this reason, the InAppBrowser is recommended if you need to load third-party (untrusted) content, instead of loading that into the main Cordova webview. 

InAppBrowser intercepts window.open calls and evaluates the target (optional parameter that defaults to _self) as follows:

* _self =  Opens in the Cordova WebView if the URL is in the white list, otherwise it opens in the InAppBrowser.
* _blank = Opens in the InAppBrowser.
* _system = Opens in the system's web browser.

So dynamic link calls via window.open are handled by InAppBrowser.
But static anchor tags in HTML page will bypass InAppBrowser and still be called in app (in Cordova WebView)

You can override the default behavior for links part of your OWN HTML code easily: http://stackoverflow.com/questions/1760096/override-default-behaviour-for-link-a-objects-in-javascript || https://gist.github.com/JonathanHindi/6301111

Some will handle links natively individually (in case you want to consider target information then it requires access and manipulation of HTML content via javascript if you want to handle): http://stackoverflow.com/questions/23962457/phonegap-how-to-make-links-from-iframes-open-in-inappbrowser

### iFrame behavior

* _self =  Opens in iFrame.
* _blank = Capture the whole Cordova WebView.
* _system = Capture the whole Cordova WebView.

In case webpages are loaded via file protocol (as it's the case for cordova) you can manipulate 3rd party iframes dynamically via javascript. However, in case webpages are loaded via an http web server then same-origin policy applies => 3rd party iframes content cannot be manipluated (SAP C4C case) :(

Some people will disable all iframe links to be on the same side: https://forums.meteor.com/t/cordova-how-to-prevent-links-in-embedded-iframes-to-replace-application/10140

## Purpose of the app

Demonstrate the behavior as outlined in techncial background sections.
Examples in iFrame:
- a href="http://www.google.com"  will be opened in iFrame
- a href="http://www.eidinger.info" target="_blank" will be opened in cordova web view and capture whole application

## Other useful information

https://github.com/phonegap/phonegap/wiki/iFrame-Usage
