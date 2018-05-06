<h1 align="left">larkplayer</h1>

<p align="left">
  <a href="https://www.npmjs.com/package/larkplayer"><img src="https://img.shields.io/npm/v/larkplayer.svg?style=flat-square" alt="NPM version"></a>
  <a href="https://www.npmjs.com/package/larkplayer"><img src="https://img.shields.io/npm/dm/larkplayer.svg?style=flat-square" alt="Downloads"></a>
  <a href="https://www.npmjs.com/package/larkplayer"><img src="https://img.shields.io/github/license/dblate/larkplayer.svg?style=flat-square" alt="License"></a>
</p>

中文｜[English](./readme-en.md)

## 简介

larkplayer 以插件化的思想编写，对于整个视频业务而言，它本身是一个精巧的核心，许多复杂或定制化的功能均由插件实现。

它本身有如下特点：

* 解决大部分兼容性问题，如全屏、移动端内联播放等
* 提供事件机制，支持自定义事件
* 提供插件机制，支持多种插件类型
* 原生 javascript 编写，无特定框架依赖

通过插件可以：

* 支持 hls vr 等其他类型
* 拥有自定义的样式
* ...

更多插件请访问[插件列表](./docs/plugin/plugin-list) ，同时你也可以[编写自定义插件](./docs/plugin)

[在线示例](https://s.codepen.io/dblate/debug/qojzZZ/ZoMBajEzGyDk)

## 下载

NPM
```
npm install larkplayer
```

CDN
```
<script src="https://unpkg.com/larkplayer@latest/dist/larkplayer.js"></script>
```

## 快速上手

#### 通过 script 的方式

```html
<!DOCTYPE html>
<html>
<head>
    <title>larkplayer quick start</title>
</head>
<body>
    <video id="my-video" src="https://baikebcs.bdimg.com/baike-other/big-buck-bunny.mp4" width="400" height="300" controls>
        请升级浏览器以支持 html5 video
    </video>
 
    <script type="text/javascript" src="https://unpkg.com/larkplayer@latest/dist/larkplayer.js"></script>
    <script type="text/javascript">
        // js 文件以 umd 的形式包装，以 script 的形式引用时，larkplayer 会直接挂载在 window 上
        var player = larkplayer('my-video', {
            width: 640,
            height: 360
        }, function () {
            console.log('player is ready');
        });

        player.on('firstplay', function () {
            console.log('firstplay');
        });

        // 支持所有的 html5 标准事件
        player.on('play', function () {
            console.log('play');
        });
        player.on('ended', function () {
            console.log('ended');
            player.src('http://www.w3school.com.cn/i/movie.ogg');
            player.play();
        });
    </script>
</body>
</html>
```

#### 通过 npm + es6 的方式


```javascript
import larkplayer from 'larkplayer';

const player = larkplayer('video-el');

```

## 文档

* [设计文档](./docs/design.md)
* [插件编写](./docs/plugin)

__API__

* [Player](./docs/api/player.md)
* [Events](./docs/api/events.md)
* [DOM](./docs/api/dom.md)


## 如何贡献代码

* fork 或 clone 代码到本地
* 修改代码
* 使用 [fecs](http://fecs.baidu.com/api) 检查 js 代码规范，并修复对应问题
    * 在项目根目录下执行 fecs src/js （更多选项可参考 [fecs_eslint_wiki](https://github.com/ecomfe/fecs/wiki/ESLint)）
    * 修复所有级别为 ERROR 的提示
    * 建议修复所有级别为 WARN 的提示
* 提交 pull request


## 后续规划

~~2018/3/7 前增加以下功能~~
* ~~支持 vr 视频~~ √（[larkplayer-vr](https://github.com/dblate/larkplayer-vr)）
* ~~支持 hls(m3u8) 格式~~ √（[larkplayer-hls](https://github.com/dblate/larkplayer-hls)）
* 支持 flv 格式
* ~~同步支持 pc 与移动端的使用~~ √
* ~~添加测试代码~~ √

## Change Log
[CHANGELOG](./CHANGELOG.md)

## License
larkplayer is [MIT licensed](./LICENSE)
