# cordova-inappbrowser-iframetest

InAppBrowser intercepts window.open calls and evaluates the target (optional parameter that defaults to _self)

* _self: Opens in the Cordova WebView if the URL is in the white list, otherwise it opens in the InAppBrowser.
* _blank: Opens in the InAppBrowser.
* _system: Opens in the system's web browser.

Anchor tags in HTML code will bypass InAppBrowser and and will per default be called in app (in Cordova WebView). That's an issue especially for 3rd vendor providers of HTML mashups

You can override the default behavior for links part of your OWN code easily: http://stackoverflow.com/questions/1760096/override-default-behaviour-for-link-a-objects-in-javascript || https://gist.github.com/JonathanHindi/6301111

But iFrames NOT UNDER OWN control with different origin are protected :(

Some people will disable the iframe links: https://forums.meteor.com/t/cordova-how-to-prevent-links-in-embedded-iframes-to-replace-application/10140

Some will handle links natively individually: http://stackoverflow.com/questions/23962457/phonegap-how-to-make-links-from-iframes-open-in-inappbrowser
