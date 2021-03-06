![react-times](./intro_src/react_times.png)

[![npm version](https://badge.fury.io/js/react-times.svg)](https://badge.fury.io/js/react-times)
[![Build Status](https://travis-ci.org/ecmadao/react-times.svg?branch=master)](https://travis-ci.org/ecmadao/react-times) [![Coverage Status](https://coveralls.io/repos/github/ecmadao/react-times/badge.svg?branch=master)](https://coveralls.io/github/ecmadao/react-times?branch=master) [![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg)](http://standardjs.com) [![react-times](http://img.shields.io/npm/dm/react-times.svg)](https://www.npmjs.com/package/react-times) [![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/ecmadao/react-times/master/LICENSE)

[![NPM](https://nodei.co/npm/react-times.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/react-times)

README：[English Version](./README.md)

> 一个 React 时间选择器组件，使用 ES6 标准语法编写，没有 jQuery 依赖

![react-times](./intro_src/react-times.gif)

## 本地玩起来

```bash
$ git clone https://github.com/ecmadao/react-times.git

$ npm install

$ npm run storybook
```

## 安装说明

单独使用插件时所需的依赖：

- [`moment`](https://github.com/moment/moment/)
- [`react`](https://github.com/facebook/react)
- [`react-dom`](https://github.com/facebook/react)

> No jQuery 😤😤😤

使用的时候，需要你的项目里已经安装了`react`和`react-dom`。如果没有的话：

```bash
$ npm install react react-dom --save-dev
# and
$ npm install react-times --save-dev
```

## 使用方式

目前组件总共有两种主题：Material 主题和经典主题

> 在使用组件的时候，记得要引入对应主题的 CSS 文件

```javascript
// 基本使用方式
// 假设要在某个组件里使用该插件 (SomeComponent)
import React from 'react';
import TimePicker from 'react-times';

// 使用 Material 主题的话引入：
import 'react-times/css/material/default.css';
// 否则经典主题的话则引入：
import 'react-times/css/classic/default.css';

export default class SomeComponent extends React.Component {
  // do some work
  onHourChange(hour) {
    // do something
  }

  onMinuteChange(minute) {
    // do something
  }

  onTimeChange(time) {
    // do something
  }

  onFocusChange(focusStatue) {
    // do something
  }

  render() {
    <TimePicker
      onFocusChange={this.onFocusChange.bind(this)}
      onHourChange={this.onHourChange.bind(this)}
      onMinuteChange={this.onMinuteChange.bind(this)}
      onTimeChange={this.onTimeChange.bind(this)}
      // 确定主题，不填该 props 则默认为 material
      theme="material"
  	  // or
  	  // theme="classic"
    />
  }
}
```

关于配置的栗子：

```javascript
render() {
  <TimePicker 
  	colorPalette="dark" // main color, default "light"
  	focused={true} // whether to show timepicker modal after rendered. default false
  	withoutIcon={true} // whether to has time icon on button, default false
  	defaultTime="13:05" // initial time, default current time
  	theme="material"
  	// or
  	// theme="classic"
  />
}
```

> 你可以戳 [这里](https://github.com/ecmadao/react-times/tree/master/examples) 查看更多栗子

## 秀一下

- 24 小时制，亮色调的 Material 主题（默认）

```javascript
<TimePicker />
```

![24HoursMode](./intro_src/24HoursMode.png)

- 12 小时制，亮色调的 Material 主题

```javascript
<TimePicker timeMode="12"/>
```

![12HoursMode](./intro_src/12HoursMode.png)

- 24 小时制，暗色调的 Material 主题

```javascript
<TimePicker colorPalette="dark"/>
```

![DarkColor](./intro_src/DarkColor.png)

- 24 小时制，亮色调的经典主题

```javascript
<TimePicker theme="classic"/>
```

![24HoursMode-ClassicTheme](./intro_src/24HoursMode-ClassicTheme.png)

- 24 小时制，暗色调的经典主题

```javascript
<TimePicker colorPalette="dark" theme="classic"/>
```

![24HoursMode-ClassicTheme-dark](./intro_src/24HoursMode-ClassicTheme-dark.png)

## APIs

### Props

- `defaultTime`

> 初始化时的时间，格式是 `${hour}:${minute}`，不传则默认使用当前时间（通过`moment()`）

```javascript
// React.PropTypes.string
defaultTime="11:11"
defaultTime="11:01"
defaultTime="1:01"
defaultTime="1:1"
```

- `focused`

> 初始化时时间选择器的 modal 是否打开，默认为`false`

```javascript
// React.PropTypes.bool
focused={false}
focused={true}
```

- `withoutIcon`

> 时间选择器的按钮上是否不需要 svg icon，默认为`false`

```javascript
// React.PropTypes.bool
withoutIcon={true}
```

- `colorPalette`

> 配色方案，默认为`light`

```javascript
// React.PropTypes.string
colorPalette="dark"
colorPalette="light"
```

- `timeMode`

> 12 或 24 小时制，默认为 24

```javascript
// React.PropTypes.string or React.PropTypes.number
timeMode="24"
timeMode=24
timeMode="12"
timeMode=12
```

### 回调

- `onFocusChange`

`React.PropTypes.func`

> 当组件`focused`属性改变，也就是选择器 modal 被打开或关闭时调用

- `onHourChange`

`React.PropTypes.func`

> 小时`hour`改变时的回调

```javascript
onHourChange(hour) {
  // ...
}
```

- `onMinuteChange`

`React.PropTypes.func`

> 分钟`minute`被改变时的回调

```javascript
onMinuteChange(minute) {
  // ...
}
```

- `onTimeChange`

`React.PropTypes.func`

> 小时`hour`或者分钟`minute`被改变时的回调

```javascript
onTimeChange(time) {
  // ...
}
```

## 相关文章

- [一言不合造轮子--撸一个ReactTimePicker](https://github.com/ecmadao/Coding-Guide/blob/master/Notes/React/ReactJS/Write%20a%20React%20Timepicker%20Component%20hand%20by%20hand.md)

## Todos

- 测试

  - [x] TimePicker Component
  - [x] PickerDragHandler Component
  - [x] PickerPointGenerator Component
  - [x] MaterialTheme Component
  - [x] TwelveHoursTheme Component
  - [x] PickerPoint Component
  - [ ] OutsideClickHandler Component

  - [x] utils test

- 配色

  - [x] light
  - [x] dark
  - [ ] colorful

- 主题

  - [x] Material Theme
  - [x] Classical Theme

- 小时制

  - [x] 12h mode
  - [x] 24h mode

- 动画

## 致谢

感谢 Airbnb 的 [react-dates](https://github.com/airbnb/react-dates) 组件，没有它我也不会想着写一个小时选择组件

## 版权

[MIT License](./LICENSE)