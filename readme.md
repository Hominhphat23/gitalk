# Gitalk

[![NPM][npm-version-image]][npm-version-url] 
[![CDNJS][cdnjs-version-image]][cdnjs-version-url] 
[![jsdelivr](https://data.jsdelivr.com/v1/package/npm/gitalk/badge)](https://www.jsdelivr.com/package/npm/gitalk)
[![david-dm][david-dm-image]][david-dm-url] 
[![travis][travis-image]][travis-url] 
[![coveralls][coveralls-image]][coveralls-url] 
[![gzip-size][gzip-size]][gzip-url]

Gitalk is a modern comment component based on GitHub Issue and Preact.

## Features

- Authentication with github account
- Serverless, all comments will be stored as github issues
- Both personal and organization github projects can be used to store comments
- Localization, support multiple languages [en, zh-CN, zh-TW, es-ES, fr, ru, de, pl, ko, fa, ja]
- Facebook-like distraction free mode (Can be enabled via the `distractionFreeMode` option)
- Hotkey submit comment (cmd|ctrl + enter)

[中文说明](https://github.com/gitalk/gitalk/blob/master/readme-cn.md)
[Demo](https://gitalk.github.io)

## Install

Two ways.

- links

```html
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.css">
  <script src="https://cdn.jsdelivr.net/npm/gitalk@1/dist/gitalk.min.js"></script>

  <!-- or -->

  <link rel="stylesheet" href="https://unpkg.com/gitalk/dist/gitalk.css">
  <script src="https://unpkg.com/gitalk/dist/gitalk.min.js"></script>
```

- npm install

```sh
npm i --save gitalk
```

```js
import 'gitalk/dist/gitalk.css'
import Gitalk from 'gitalk'
```

## Usage
Firstly, you need choose a public github repository (existed or create a new one) for store comments,

Then create A **GitHub Application** if you don't have one, [Click here to register](https://github.com/settings/applications/new) a new one. 
**Note:** You must specify the website domain url in the `Authorization callback URL` field.

Lastly, you can choose how to apply to the page as below:

### Method One
Add a container to your page:

```html
<div id="gitalk-container"></div>
```

Then use the Javascript code below to generate the gitalk plugin:

```js
const gitalk = new Gitalk({
  clientID: 'GitHub Application Client ID',
  clientSecret: 'GitHub Application Client Secret',
  repo: 'GitHub repo',      // The repository of store comments,
  owner: 'GitHub repo owner',
  admin: ['GitHub repo owner and collaborators, only these guys can initialize github issues'],
  id: location.pathname,      // Ensure uniqueness and length less than 50
  distractionFreeMode: false  // Facebook-like distraction free mode
})

gitalk.render('gitalk-container')
```

### Method Two: Use in React

Import the Gitalk with

```jsx
import GitalkComponent from "gitalk/dist/gitalk-component";
```

And use the component like

```jsx
<GitalkComponent options={{
  clientID: "...",
  // ...
  // options below
}} />
```

## Options

- **clientID** `String`

  **Required**. GitHub Application Client ID.

- **clientSecret** `String`

  **Required**. GitHub Application Client Secret.

- **repo** `String`

  **Required**. GitHub repository.

- **owner** `String`

  **Required**. GitHub repository owner. Can be personal user or organizations 
