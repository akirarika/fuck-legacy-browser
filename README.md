# fuck-legacy-browser
🌍 When legacy browsers visit your modern website, a full-screen prompt will be obtained.

We may want to give some hints to legacy browsers, informing them that they must upgrade their browsers in order to continue accessing our website.

We may hope that:

- It is non-intrusive, not a Vue or React component, and has no impact on our existing code at all.

- We also don't want it to redirect to third-party pages, have no advertisements, and won't provide any browser download links.

- It will cover the entire page to prevent users from seeing incorrect styles or using invalid functions.

- The user's Safari browser version must be at least 18.0. If the user is using an Android phone, the WebView version must be at least 108.

![](./435C65590F3A61B3DE69574D4B6DB405.png)

## Prompt

Starting from September 16, 2025, the prompt messages have been carefully crafted. First, we clearly explain the reasons to users. For example, on iOS, we advise users to update their system rather than their browser—since non-technical users often have no concept of updating a browser.

On non-Mac computers, where users typically use Windows devices, we recommend using the built-in Edge browser and prompt them to update it to the latest version.

At the same time, we avoid blaming users for using outdated technology or older devices—a psychological technique known as “Serviceable Attribution”. This helps maintain user goodwill. Our approach reframes the issue as our responsibility to improve device support, emphasizing that we are actively working to enhance compatibility across more devices.

For iPhone users:

```
This app requires a device running iOS 18.0 or later to function properly.

We sincerely apologize. Our team is working tirelessly to improve app compatibility, and we will strive to support more devices in the future so that more users can enjoy a smooth experience. ✨
```

For macOS users:

```
This app requires Safari 18.0 or macOS Sequoia (or later) to function properly.

We sincerely apologize. Our team is working tirelessly to improve app compatibility, and we will strive to support more devices in the future so that more users can enjoy a smooth experience. ✨
```

For non-iOS mobile users (typically Android users):

```
This app requires the latest system version to function properly.

If your system is already up to date, it's possible that your device is not yet supported. We sincerely apologize!

Our team is working tirelessly to improve app compatibility, and we will strive to support more devices in the future so that more users can enjoy a smooth experience. ✨
```

(Note: Although users could update WebView, many regions—especially China—do not have access to Google Play. Instead, each phone brand has its own app store, and many systems prohibit installing apps outside of these stores. Therefore, updating WebView is often difficult and not straightforward for users. Hence, the recommendation here is to update the system.)

For non-macOS computer users (typically Windows users):

```
This app requires the latest browser version to function properly.

We recommend using Edge browser and updating it to the latest version.

We sincerely apologize. Our team is working tirelessly to improve app compatibility, and we will strive to support more devices in the future so that more users can enjoy a smooth experience. ✨
```

## Install

Create a `<script>` tag at the beginning of the `<head>` tag in your HTML and paste the code into it.

```js
setTimeout(function(){var ban=false;var div=document.createElement("div");if(typeof window.Proxy==="undefined")ban=true;else if(typeof[].findLast==="undefined")ban=true;else if(typeof div.style.contentVisibility==="undefined")ban=true;if(!ban)return;var lang="en";try{var sAgent=navigator.userAgent;if(sAgent.indexOf("Trident")>0)lang=window.navigator.browserLanguage;else lang=window.navigator.language}catch(e){}function startsWith(search,rawPos){var pos=rawPos>0?rawPos|0:0;return search.substring(pos,pos+search.length)===search}var isApple=/iPhone|iPad|iPod|Macintosh/.test(navigator.userAgent);var isMobile=/iPhone|iPad|iPod|Android/.test(navigator.userAgent);var isDesktop=false;try{isDesktop=!isMobile;isDesktop=!isMobile&&document.body.offsetWidth>=768&&document.body.offsetWidth>=document.body.offsetHeight}catch(error){}var s="";if(startsWith(lang,"zh")){if(isApple&&isMobile){s="此应用正常工作需要系统版本为 iOS 18.0 设备的支持<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}else if(isApple&&isDesktop){s="此应用正常工作需要系统版本为 Safari 18.0 或者 macOS Sequoia 的支持<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}else if(!isApple&&isMobile){s="此应用正常工作需要最新系统版本的支持<br />如果您的系统已经是最新的，可能是这款设备我们尚未适配，真的非常对不起！<br />我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}else if(!isApple&&isDesktop){s="此应用正常工作需要最新浏览器的支持<br />可以使用 Edge 浏览器并更新到最新<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}}else if(startsWith(lang,"ja")){if(isApple&&isMobile){s="このアプリは iOS 18.0 以上のシステムバージョンが必要です<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}else if(isApple&&isDesktop){s="このアプリは Safari 18.0 または macOS Sequoia 以上のシステムバージョンが必要です<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}else if(!isApple&&isMobile){s="このアプリは最新のシステムバージョンが必要です<br />すでに最新のシステムをご利用中の場合は、当該デバイスにまだ対応していない可能性がございます。本当に申し訳ございません！<br />現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}else if(!isApple&&isDesktop){s="このアプリは最新のブラウザが必要です<br />Edge ブラウザを最新版に更新してご利用ください<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}}else if(startsWith(lang,"ko")){if(isApple&&isMobile){s="이 앱은 iOS 18.0 이상의 시스템 버전이 필요합니다<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}else if(isApple&&isDesktop){s="이 앱은 Safari 18.0 또는 macOS Sequoia 이상의 시스템 버전이 필요합니다<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}else if(!isApple&&isMobile){s="이 앱은 최신 시스템 버전이 필요합니다<br />이미 최신 시스템을 사용 중이라면 아직该기기를 지원하지 않는 것일 수 있습니다. 정말 죄송합니다!<br />저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}else if(!isApple&&isDesktop){s="이 앱은 최신 브라우저가 필요합니다<br />Edge 브라우저를 최신 버전으로 업데이트하여 사용해 주세요<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}}else{if(isApple&&isMobile){s="This app requires a device with iOS 18.0 or later<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}else if(isApple&&isDesktop){s="This app requires Safari 18.0 or macOS Sequoia or later<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}else if(!isApple&&isMobile){s="This app requires the latest system version<br />If your system is already up to date, it might be that we haven't adapted to this device yet. We're really sorry!<br />We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}else if(!isApple&&isDesktop){s="This app requires the latest browser version<br />You can use Edge browser and update to the latest version<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}}var div0=document.createElement("div");div0.innerHTML='<div style="background-color:#ffffff;z-index:2147483647;position:fixed;left:0;top:0;width:100%;height:100%;"><div style="width:100%;height:100%;z-index:2147483647;display:flex;justify-content:center;align-items:center;flex-direction:column;color:#3288f5;font-size:14px;line-height:1.6;padding:32px;box-sizing:border-box">'+s+'</div></div>';document.body.appendChild(div0)});
```

If you use nuxt:

```js
useHead({
  script: [
    {
      type: 'text/javascript',
      innerHTML: `setTimeout(function(){var ban=false;var div=document.createElement("div");if(typeof window.Proxy==="undefined")ban=true;else if(typeof[].findLast==="undefined")ban=true;else if(typeof div.style.contentVisibility==="undefined")ban=true;if(!ban)return;var lang="en";try{var sAgent=navigator.userAgent;if(sAgent.indexOf("Trident")>0)lang=window.navigator.browserLanguage;else lang=window.navigator.language}catch(e){}function startsWith(search,rawPos){var pos=rawPos>0?rawPos|0:0;return search.substring(pos,pos+search.length)===search}var isApple=/iPhone|iPad|iPod|Macintosh/.test(navigator.userAgent);var isMobile=/iPhone|iPad|iPod|Android/.test(navigator.userAgent);var isDesktop=false;try{isDesktop=!isMobile;isDesktop=!isMobile&&document.body.offsetWidth>=768&&document.body.offsetWidth>=document.body.offsetHeight}catch(error){}var s="";if(startsWith(lang,"zh")){if(isApple&&isMobile){s="此应用正常工作需要系统版本为 iOS 18.0 设备的支持<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}else if(isApple&&isDesktop){s="此应用正常工作需要系统版本为 Safari 18.0 或者 macOS Sequoia 的支持<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}else if(!isApple&&isMobile){s="此应用正常工作需要最新系统版本的支持<br />如果您的系统已经是最新的，可能是这款设备我们尚未适配，真的非常对不起！<br />我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}else if(!isApple&&isDesktop){s="此应用正常工作需要最新浏览器的支持<br />可以使用 Edge 浏览器并更新到最新<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨"}}else if(startsWith(lang,"ja")){if(isApple&&isMobile){s="このアプリは iOS 18.0 以上のシステムバージョンが必要です<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}else if(isApple&&isDesktop){s="このアプリは Safari 18.0 または macOS Sequoia 以上のシステムバージョンが必要です<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}else if(!isApple&&isMobile){s="このアプリは最新のシステムバージョンが必要です<br />すでに最新のシステムをご利用中の場合は、当該デバイスにまだ対応していない可能性がございます。本当に申し訳ございません！<br />現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}else if(!isApple&&isDesktop){s="このアプリは最新のブラウザが必要です<br />Edge ブラウザを最新版に更新してご利用ください<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨"}}else if(startsWith(lang,"ko")){if(isApple&&isMobile){s="이 앱은 iOS 18.0 이상의 시스템 버전이 필요합니다<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}else if(isApple&&isDesktop){s="이 앱은 Safari 18.0 또는 macOS Sequoia 이상의 시스템 버전이 필요합니다<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}else if(!isApple&&isMobile){s="이 앱은 최신 시스템 버전이 필요합니다<br />이미 최신 시스템을 사용 중이라면 아직该기기를 지원하지 않는 것일 수 있습니다. 정말 죄송합니다!<br />저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}else if(!isApple&&isDesktop){s="이 앱은 최신 브라우저가 필요합니다<br />Edge 브라우저를 최신 버전으로 업데이트하여 사용해 주세요<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨"}}else{if(isApple&&isMobile){s="This app requires a device with iOS 18.0 or later<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}else if(isApple&&isDesktop){s="This app requires Safari 18.0 or macOS Sequoia or later<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}else if(!isApple&&isMobile){s="This app requires the latest system version<br />If your system is already up to date, it might be that we haven't adapted to this device yet. We're really sorry!<br />We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}else if(!isApple&&isDesktop){s="This app requires the latest browser version<br />You can use Edge browser and update to the latest version<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨"}}var div0=document.createElement("div");div0.innerHTML='<div style="background-color:#ffffff;z-index:2147483647;position:fixed;left:0;top:0;width:100%;height:100%;"><div style="width:100%;height:100%;z-index:2147483647;display:flex;justify-content:center;align-items:center;flex-direction:column;color:#3288f5;font-size:14px;line-height:1.6;padding:32px;box-sizing:border-box">'+s+'</div></div>';document.body.appendChild(div0)});`
    },
  ],
});
```

Perhaps you may want to customize some of your own logic. Then here is an uncompressed version.

Firstly, this piece of code will first determine whether there are some browser methods that are only available in higher versions to ensure that the user's browser version is new enough. This requires Chrome to be at least version 108, Firefox to be at least version 125. For the Safari browser, the version requirement has been raised to 18, because there were many strange issues with DOM and CSS in version 15.x, although the relevant issues with Safari have been decreasing since version 16.

Through `setTimeout`, it is ensured that the code can support Internet Explorer while not blocking your main code logic. Meanwhile, it is also ensured that even if there are errors in the execution of your subsequent code, the prompt for upgrading the browser can still be displayed normally. 

```js
setTimeout(function() {
    var ban = false;
    var div = document.createElement("div");
    if (typeof window.Proxy === "undefined") ban = true;
    else if (typeof [].findLast === "undefined") ban = true;
    else if (typeof div.style.contentVisibility === "undefined") ban = true;
    if (!ban) return;
    
    var lang = "en";
    try {
        var sAgent = navigator.userAgent;
        if (sAgent.indexOf("Trident") > 0) lang = window.navigator.browserLanguage;
        else lang = window.navigator.language;
    } catch (e) {}
    
    function startsWith(search, rawPos) {
        var pos = rawPos > 0 ? rawPos | 0 : 0;
        return search.substring(pos, pos + search.length) === search;
    }
    
    var isApple = /iPhone|iPad|iPod|Macintosh/.test(navigator.userAgent);
    var isMobile = /iPhone|iPad|iPod|Android/.test(navigator.userAgent);
    var isDesktop = false;
    try {
        isDesktop = !isMobile;
        isDesktop = !isMobile && document.body.offsetWidth >= 768 && document.body.offsetWidth >= document.body.offsetHeight;
    } catch (error) { }
    var s = "";
    
    if (startsWith(lang, "zh")) {
        if (isApple && isMobile) {
            s = "此应用正常工作需要系统版本为 iOS 18.0 设备的支持<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨";
        } else if (isApple && isDesktop) {
            s = "此应用正常工作需要系统版本为 Safari 18.0 或者 macOS Sequoia 的支持<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨";
        } else if (!isApple && isMobile) {
            s = "此应用正常工作需要最新系统版本的支持<br />如果您的系统已经是最新的，可能是这款设备我们尚未适配，真的非常对不起！<br />我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨";
        } else if (!isApple && isDesktop) {
            s = "此应用正常工作需要最新浏览器的支持<br />可以使用 Edge 浏览器并更新到最新<br />真的非常对不起，我们现在也在超努力地优化应用兼容性，未来一定会尽力覆盖更多设备，让更多小伙伴都能顺顺利利用上它的✨";
        }
    } else if (startsWith(lang, "ja")) {
        if (isApple && isMobile) {
            s = "このアプリは iOS 18.0 以上のシステムバージョンが必要です<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨";
        } else if (isApple && isDesktop) {
            s = "このアプリは Safari 18.0 または macOS Sequoia 以上のシステムバージョンが必要です<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨";
        } else if (!isApple && isMobile) {
            s = "このアプリは最新のシステムバージョンが必要です<br />すでに最新のシステムをご利用中の場合は、当該デバイスにまだ対応していない可能性がございます。本当に申し訳ございません！<br />現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨";
        } else if (!isApple && isDesktop) {
            s = "このアプリは最新のブラウザが必要です<br />Edge ブラウザを最新版に更新してご利用ください<br />本当に申し訳ございません、現在も互換性の向上に全力で取り組んでおります。今後より多くのデバイスに対応し、より多くのユーザーがスムーズに利用できるよう尽力してまいります✨";
        }
    } else if (startsWith(lang, "ko")) {
        if (isApple && isMobile) {
            s = "이 앱은 iOS 18.0 이상의 시스템 버전이 필요합니다<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨";
        } else if (isApple && isDesktop) {
            s = "이 앱은 Safari 18.0 또는 macOS Sequoia 이상의 시스템 버전이 필요합니다<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨";
        } else if (!isApple && isMobile) {
            s = "이 앱은 최신 시스템 버전이 필요합니다<br />이미 최신 시스템을 사용 중이라면 아직该기기를 지원하지 않는 것일 수 있습니다. 정말 죄송합니다!<br />저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨";
        } else if (!isApple && isDesktop) {
            s = "이 앱은 최신 브라우저가 필요합니다<br />Edge 브라우저를 최신 버전으로 업데이트하여 사용해 주세요<br />정말 죄송합니다. 저희도 호환성 개선을 위해 열심히努力하고 있습니다. 앞으로 더 많은 기기를 지원하여 더 많은 분들이顺顺利用할 수 있도록尽力하겠습니다✨";
        }
    } else {
        if (isApple && isMobile) {
            s = "This app requires a device with iOS 18.0 or later<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨";
        } else if (isApple && isDesktop) {
            s = "This app requires Safari 18.0 or macOS Sequoia or later<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨";
        } else if (!isApple && isMobile) {
            s = "This app requires the latest system version<br />If your system is already up to date, it might be that we haven't adapted to this device yet. We're really sorry!<br />We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨";
        } else if (!isApple && isDesktop) {
            s = "This app requires the latest browser version<br />You can use Edge browser and update to the latest version<br />We're really sorry for the inconvenience. We're working super hard to improve app compatibility and will definitely try our best to support more devices in the future, so that more friends can use it smoothly✨";
        }
    }
    
    var div0 = document.createElement("div");
    div0.innerHTML = '<div style="background-color:#ffffff;z-index:2147483647;position:fixed;left:0;top:0;width:100%;height:100%;"><div style="width:100%;height:100%;z-index:2147483647;display:flex;justify-content:center;align-items:center;flex-direction:column;color:#3288f5;font-size:14px;line-height:1.6;padding:32px;box-sizing:border-box">' + s + '</div></div>';
    document.body.appendChild(div0);
});
```
