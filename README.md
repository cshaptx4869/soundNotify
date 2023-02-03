# SoundNotify 组件

## 简介

消息通知组件。

支持文字转语音、音频播报、桌面通知。

## 效果

在线体验地址：

- [JQ22](https://www.jq22.com/yanshi24513)
- [GitHub](https://cshaptx4869.github.io/mypage/soundNotify/soundNotify.html)（优先更新!）

![](https://foruda.gitee.com/images/1673592532170882402/b58c7ac9_5507348.jpeg)

## 示例

```html
<!doctype html>
<html lang="zh">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>消息通知</title>
    <!-- 引入 layui.css -->
    <link rel="stylesheet" type="text/css" href="./layui/css/layui.css"/>
</head>
<body>

<div style="height:100vh;display: flex;align-items: center;justify-content: center;">
    <button class="layui-btn layui-btn-primary" id="sound">文字转语音</button>
    <button class="layui-btn layui-btn-warm" id="audio">音频播报</button>
    <button class="layui-btn layui-btn-normal" id="notify">桌面通知</button>
</div>

<!-- 引入 layui.js -->
<script src="./layui/layui.js"></script>
<script>
    layui.config({
        base: './lay-module/', // 设定扩展的 layui 模块的所在目录，一般用于外部模块扩展
    }).use(['soundNotify', 'jquery'], function () {
        var soundNotify = layui.soundNotify, $ = layui.jquery;
        var actionMap = {
            sound() {
                soundNotify.sound('人间烟火');
            },
            audio() {
                soundNotify.audio('http://music.163.com/song/media/outer/url?id=1929363849.mp3');
            },
            notify() {
                //参数对应 https://developer.mozilla.org/zh-CN/docs/Web/API/notification/Notification
                soundNotify.notify('人间烟火', {
                    body: '人间一场烟火 你曾盛开过\n' +
                        '刻几人在心窝 从此孤独活\n' +
                        '江南花已凋落 怎堪再斟酌\n' +
                        '可怜良辰无多 竟似无人说\n' +
                        '你撑纸伞回头望 千年乌衣巷\n' +
                        '问君青丝有几丈 能把风月量\n' +
                        '谁言杯酒醉他乡 红尘皆可忘\n' +
                        '凭栏数尽孤帆 泪两行',
                    sound: 'http://music.163.com/song/media/outer/url?id=1929363849.mp3'
                })
            }
        };

        Object.keys(actionMap).forEach((item) => $(`#${item}`).click(actionMap[item]));
    });
</script>
</body>
</html>
```

