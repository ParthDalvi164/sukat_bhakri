# (EXP9)PWA_creation

1. Get proper .html and .css files, add them to a folder.
2. Convert an image to a favicon from [FAVICON](https://favicon.io/favicon-converter/).
3. Extract it the the parent folder.
4. Content of "site.webmanifest" : 
```javascript
{
    "name":"TempConv",
    "short_name":"TV",
    "icons":[{"src":"/android-chrome-192x192.png",
    "sizes":"192x192","type":"image/png"},
    {"src":"/android-chrome-512x512.png","sizes":"512x512","type":"image/png"}],
    "theme_color":"#ffffff",
    "background_color":"#ffffff",
    "display":"standalone",
    "start_url":"/"
}
```
5. Create a file sw.js and add code :
```js
if('serviceWorker' in navigator) {
    window.addEventListener('load', function() {
        this.navigator.serviceWorker.register('/sw.js', {scope: "/"}).then(function(registeration) {
            console.log('service work reg succeess with scope:', registeration.scope);

        }, function(err) {
            console.error('serviceW reg failed:', err);
        });
    })
}
```
6. Modifications in HTML file : <br>(inside head)
  ```html
  <link rel="manifest" href="/site.webmanifest">
  <link rel="service" href="/sw.js">
  ```
7. inside body : 
  ```html
  <script src="sw.js"></script>
  ```
