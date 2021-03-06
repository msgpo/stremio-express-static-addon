# Stremio Express Add-on Example

This example add-on uses files from [Stremio Static Add-on Example](https://github.com/Stremio/stremio-static-addon-example)

## Running Express Example

```
npm install
npm start
```

Then use the URL that is printed as the [Add-on Repository URL](https://github.com/Stremio/stremio-express-addon-example#dont-know-where-to-add-the-add-on-repository-url)

## Understanding Express Add-on

**index.js** file contents:

```javascript
const express = require('express')

const app = express()

const opts = {
  setHeaders: (res, path, stat) => {
    res.set('Access-Control-Allow-Origin', '*')
    res.set('Access-Control-Allow-Headers', '*')
  }
}
 
app.use('/', express.static('./', opts))

app.listen(7000)

console.log('Add-on started on: http://127.0.0.1:7000/manifest.json')
```

That's it, this add-on simply serves the files from [Stremio Static Add-on Example](https://github.com/Stremio/stremio-static-addon-example) through a local web server, it also sets CORS in the response headers.

## Using this Add-on with Localtunnel

`localtunnel` allows you to publish a local add-on to a remote address.

Usage:

```
npm install -g localtunnel
lt --port 7000
```

This will typically bring a response such as:
```
your url is: https://perfect-bird-96.localtunnel.me
```

In which case you should use `https://perfect-bird-96.localtunnel.me/manifest.json` as your [Add-on Repository URL](https://github.com/Stremio/stremio-express-addon-example#dont-know-where-to-add-the-add-on-repository-url)

### Don't know where to add the Add-on Repository URL?

![add-on-repository-url](https://user-images.githubusercontent.com/1777923/43146711-65a33ccc-8f6a-11e8-978e-4c69640e63e3.png)
