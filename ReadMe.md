# vue-zendesk

This repo is a fork of [@dansmaculotte/vue-zendesk](https://github.com/dansmaculotte/vue-zendesk). Please visit the original repo to be up to date.

[Zendesk Web Widget Documentation](https://developer.zendesk.com/embeddables/docs/widget/introduction)

## Setup

1. Add the `@dansmaculotte/vue-zendesk` dependency with `yarn` or `npm` to your project
2. Configure it:

```js
import Vue from 'vue'
import Zendesk from '@dansmaculotte/vue-zendesk'

Vue.use(Zendesk, {
  key: 'YOUR_ZENDESK_KEY',
  disabled: true,
  hideOnLoad: true,
  settings: {
    webWidget: {
      color: {
        theme: '#78a300'
      }
    }
  }
})
```

### Options

#### `disabled`

`disabled` option allows you to prevent automatic script loading, to comply with GDPR.

You can manually load it by calling `this.$zendesk.load(YOUR_ZENDESK_KEY)`.

#### `hideOnLoad`

When Zendesk Web Widget is initialized it automatically shows the widget, to prevent this you can set to `true` this option so you can manually show it after.

#### `settings`

You can view Zendesk Web Widget available settings [here](https://developer.zendesk.com/embeddables/docs/widget/settings).

## Usage

You can use any method coming from the official documentation.
Every methods are accessible from `$zendesk` object.

For example:
```js
Vue.$zendesk.hide()
// In a vue component
this.$zendesk.show()
```

You can also listen to `loaded` event emitted on script load, `open` on widget open and `close` on widget close.

For example:
```js
this.$zendesk.$on('loaded', (event) => {
  this.$zendesk.identify({
    name: 'John'
  })
})

this.$zendesk.$on('open', () => {
  console.log('Widget is open')
})

this.$zendesk.$on('close', () => {
  console.log('Widget is closed')
})
```

You can access to Zendesk Web Widget instance through `this.$zendesk.zE` or `window.zE` objects.

For example:
```js
this.$zendesk.zE('webWidget', 'hide')
window.zE('webWidget', 'hide')
```

## Development

1. Clone this repository
2. Install dependencies using `yarn install` or `npm install`
3. Start development server using `npm run dev`

## License

[MIT License](./LICENSE.md)

<!-- Badges -->
[npm-version-src]: https://img.shields.io/npm/dt/@dansmaculotte/vue-zendesk.svg?style=flat-square
[npm-version-href]: https://npmjs.com/package/@dansmaculotte/vue-zendesk

[npm-downloads-src]: https://img.shields.io/npm/v/@dansmaculotte/vue-zendesk/latest.svg?style=flat-square
[npm-downloads-href]: https://npmjs.com/package/@dansmaculotte/vue-zendesk

[david-dm-src]: https://david-dm.org/dansmaculotte/vue-zendesk/status.svg?style=flat-square
[david-dm-href]: https://david-dm.org/dansmaculotte/vue-zendesk

[standard-js-src]: https://img.shields.io/badge/code_style-standard-brightgreen.svg?style=flat-square
[standard-js-href]: https://standardjs.com
