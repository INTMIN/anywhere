Anywhere 随启随用的静态文件服务器
==============================

Running static file server anywhere. 随时随地将你的当前目录变成一个静态文件服务器的根目录。

## Installation

Install it as a command line tool via `npm -g`.

```sh
npm install intmin-server -g
```

## Execution

```sh
$ minserver
// or with port
$ minserver -p 8000
// or start it but silent(don't open browser)
$ minserver -s
// or with hostname
$ minserver -h localhost -p 8888
// or with folder
$ minserver -d ~/git/minserver
// or enable html5 history
$ minserver -f /index.html
```

## Help

```sh
$ minserver --help
Usage:
  minserver --help // print help information
  minserver // 8000 as default port, current folder as root
  minserver 8888 // 8888 as port
  minserver -p 8989 // 8989 as port
  minserver -s // don't open browser
  minserver -h localhost // localhost as hostname
  minserver -d /home // /home as root
  minserver -f /index.html  // Enable html5 history,the index is /index.html
  minserver --proxy http://localhost:7000/api // Support shorthand URL, webpack.config.js or customize config file
```

#### Proxy argvs

**Shorthand URL**
```
minserver --proxy http://localhost:7000/api
                 \___________________/\___/
                              |         |
                           target    context
```
More about the [shorthand configuration](https://github.com/chimurai/http-proxy-middleware#shorthand).

**Webpack config**
```javascript
// webpack.config.js
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://localhost:7000',
        changeOrigin: true
      }
    }
  }
}
```

**Customize config**
```javascript
// proxy.config.js
module.exports = {
  '/api': {
    target: 'http://localhost:7000',
    changeOrigin: true
  }
}
```
More proxy [http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware#context-matching) help.

## Visit

```
http://localhost:8000
```
Automatically open default browser. 执行命令后，默认浏览器将为您自动打开主页。

## License
The MIT license.
