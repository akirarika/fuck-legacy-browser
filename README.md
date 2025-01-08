# fuck-legacy-browser
🌍 When legacy browsers visit your modern website, a full-screen prompt will be obtained.

We may want to give some hints to legacy browsers, informing them that they must upgrade their browsers in order to continue accessing our website.

We may hope that:

- It is non-intrusive, not a Vue or React component, and has no impact on our existing code at all.

- We also don't want it to redirect to third-party pages, have no advertisements, and won't provide any browser download links.

- It will cover the entire page to prevent users from seeing incorrect styles or using invalid functions. 

## Install

Create a `<script>` tag at the beginning of the `<head>` tag in your HTML and paste the code into it.

```js
setTimeout(function(){var ban=false;if(typeof window.Proxy==="undefined")ban=true;else if(typeof[].at==="undefined")ban=true;else if(typeof[].findLast==="undefined")ban=true;else if(navigator.userAgent.includes("Safari")&&typeof[].toSorted==="undefined")ban=true;var zh="您的浏览器或系统较旧，不支持本网站<br />请尝试升级您的浏览器或系统";var en="Your browser or system is outdated and does not support this website < br/> Please try to upgrade your browser or system";if(!ban)return;var div0=document.createElement("div");div0.style.backgroundColor="#ffffff";div0.style.zIndex="2147483647";div0.style.position="fixed";div0.style.left="0px";div0.style.top="0px";div0.style.width="100%";div0.style.height="100%";var div1=document.createElement("div");div1.style.width="100%";div1.style.height="100%";div1.style.zIndex="2147483647";div1.style.verticalAlign="middle";div1.style.textAlign="center";div1.style.fontSize="16px";div1.style.color="#3288f5";div1.style.lineHeight="1.6";div1.style.padding="32px";div1.style.boxSizing="border-box";div1.style.fontFamily="sans-serif";var sAgent=window.navigator.userAgent;var lang="en";try{if(!String.prototype.startsWith){Object.defineProperty(String.prototype,'startsWith',{value:function(search,rawPos){var pos=rawPos>0?rawPos|0:0;return this.substring(pos,pos+search.length)===search}})}if(sAgent.indexOf("Trident")>0)lang=window.navigator.browserLanguage;else lang=window.navigator.language}catch(e){}function startsWith(search,rawPos){var pos=rawPos>0?rawPos|0:0;return search.substring(pos,pos+search.length)===search}if(startsWith(lang,"zh"))div1.innerHTML=zh;else div1.innerHTML=en;div0.appendChild(div1);document.body.appendChild(div0);document.body.style.pointerEvents="none"});
```

Perhaps you may want to customize some of your own logic. Then here is an uncompressed version.

Firstly, this piece of code will first determine whether there are some browser methods that are only available in higher versions to ensure that the user's browser version is new enough. This requires Chrome to be at least version 97, Firefox to be at least version 104. For the Safari browser, the version requirement has been raised to 16, because there were many strange issues with DOM and CSS in version 15.x.

Through `setTimeout`, it is ensured that the code can support Internet Explorer while not blocking your main code logic. Meanwhile, it is also ensured that even if there are errors in the execution of your subsequent code, the prompt for upgrading the browser can still be displayed normally. 

```js
setTimeout(function() {
    var ban = false;
    if (typeof window.Proxy === "undefined") ban = true;
    else if (typeof [].at === "undefined") ban = true;
    else if (typeof [].findLast === "undefined") ban = true;
    else if (navigator.userAgent.includes("Safari") && typeof [].toSorted === "undefined") ban = true;
    var zh = "您的浏览器或系统较旧，不支持本网站<br />请尝试升级您的浏览器或系统";
    var en = "Your browser or system is outdated and does not support this website < br/> Please try to upgrade your browser or system";
    if (!ban) return;
    var div0 = document.createElement("div");
    div0.style.backgroundColor = "#ffffff";
    div0.style.zIndex = "2147483647";
    div0.style.position = "fixed";
    div0.style.left = "0px";
    div0.style.top = "0px";
    div0.style.width = "100%";
    div0.style.height = "100%";
    var div1 = document.createElement("div");
    div1.style.width = "100%";
    div1.style.height = "100%";
    div1.style.zIndex = "2147483647";
    div1.style.verticalAlign = "middle";
    div1.style.textAlign = "center";
    div1.style.fontSize = "16px";
    div1.style.color = "#3288f5";
    div1.style.lineHeight = "1.6";
    div1.style.padding = "32px";
    div1.style.boxSizing = "border-box";
    div1.style.fontFamily = "sans-serif";
    var sAgent = window.navigator.userAgent;
    var lang = "en";
    try {
        if (!String.prototype.startsWith) {
            Object.defineProperty(String.prototype, 'startsWith', {
                value: function(search, rawPos) {
                    var pos = rawPos > 0 ? rawPos | 0 : 0;
                    return this.substring(pos, pos + search.length) === search;
                }
            });
        }
        if (sAgent.indexOf("Trident") > 0) lang = window.navigator.browserLanguage;
        else lang = window.navigator.language;
    } catch (e) {}

    function startsWith(search, rawPos) {
        var pos = rawPos > 0 ? rawPos | 0 : 0;
        return search.substring(pos, pos + search.length) === search;
    }
    if (startsWith(lang, "zh")) div1.innerHTML = zh;
    else div1.innerHTML = en;
    div0.appendChild(div1);
    document.body.appendChild(div0);
    document.body.style.pointerEvents = "none";
});
```
