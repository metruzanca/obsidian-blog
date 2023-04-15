Downloading a file from url in Nodejs

```js
const fs = require('fs');
const request = require('request')

function download(url, path, callback) {
  request.head(url, (err, res, body) => {
    request(url)
      .pipe(fs.createWriteStream(path))
      .on('close', callback)
  })
}

// if filename is included as last param of url.pathname
function getFilename(url) {
  return (new URL(url)).pathname.split('/').pop()
}
```