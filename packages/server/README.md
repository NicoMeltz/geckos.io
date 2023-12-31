<a href="http://geckos.io">
<img src="https://github.com/geckosio/geckos.io/raw/master/readme/logo-256.png" alt="logo" width="128">
</a>

# @geckos.io/server

[![NPM version](https://img.shields.io/npm/v/@geckos.io/server.svg?style=flat-square)](https://www.npmjs.com/package/@geckos.io/server)
[![Downloads](https://img.shields.io/npm/dm/@geckos.io/server.svg?style=flat-square)](https://www.npmjs.com/package/@geckos.io/server)
![Node version](https://img.shields.io/node/v/@geckos.io/server.svg?style=flat-square)
![Snyk Vulnerabilities for GitHub Repo (Specific Manifest)](https://img.shields.io/snyk/vulnerabilities/github/geckosio/geckos.io/packages/server/package.json.svg?style=flat-square)
![NPM](https://img.shields.io/npm/l/@geckos.io/server.svg?style=flat-square)
[![Codecov](https://img.shields.io/codecov/c/github/geckosio/geckos.io?logo=codecov&style=flat-square)](https://codecov.io/gh/geckosio/geckos.io)
[![ES Modules Badge](https://img.shields.io/badge/Node.js-ES%20Modules-F7DF1E?style=flat-square)](https://github.com/yandeu/yandeu/blob/main/posts/2020-05-28-esm-for-nodejs.md)

Real-time client/server communication over UDP using **WebRTC** and **Node.js**.

This framework fits perfectly with your next **HTML5 real-time multiplayer games** or chat app.

Read the [documentation](https://github.com/geckosio/geckos.io) for more information.

## Install

```console
npm install @geckos.io/server
```

## How to use

```js
import geckos from '@geckos.io/server'

const io = geckos()

io.listen()

io.onConnection(channel => {
  channel.onDisconnect(() => {
    console.log(`${channel.id} got disconnected`)
  })

  channel.on('chat message', data => {
    console.log(`got ${data} from "chat message"`)
    // emit the "chat message" data to all channels in the same room
    io.room(channel.roomId).emit('chat message', data)
  })
})
```
