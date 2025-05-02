→ First install wget if it's not installed 

```shell
brew install wget
```

→ Then in the console tab of the browser paste the following code: 

```js
const links = Array.from(document.images).map(img => img.src).join('\n');
const blob = new Blob([links], { type: 'text/plain' });
const url = URL.createObjectURL(blob);
const a = document.createElement('a');
a.href = url;
a.download = 'image-urls.txt';
a.click();
URL.revokeObjectURL(url);
```

👉 This will **create a file called image-urls.txt and auto-download it** for you!

→ Once you have urls.txt, you can simply:

```shell
wget -i urls.txt
```

