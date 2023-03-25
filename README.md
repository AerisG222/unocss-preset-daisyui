# unocss-preset-daisy

> [UnoCSS](https://github.com/unocss/unocss) preset for [daisyUI](https://github.com/saadeghi/daisyui)

[Checkout the demo!](https://unocss-preset-daisy.vercel.app/)

## Installation

```sh
npm install unocss daisyui unocss-preset-daisy
```

## Usage

### Vite

```js
import {defineConfig} from 'vite'
import unocss from 'unocss/vite'
import {presetUno} from 'unocss'
import {presetDaisy} from 'unocss-preset-daisy'

export default defineConfig({
	plugins: [
		unocss({
			presets: [presetUno(), presetDaisy()],
		}),
	],
})
```

### Astro

```js
import {defineConfig} from 'astro/config'
import unocss from 'unocss/vite'
import {presetUno} from 'unocss'
import {presetDaisy} from 'unocss-preset-daisy'

export default defineConfig({
	vite: {
		plugins: [
			unocss({
				presets: [presetUno(), presetDaisy()],
			}),
		],
	}
})
```

### Nuxt

To use UnoCSS with Nuxt, `@unocss/nuxt` must be installed as well.

```js
import {defineNuxtConfig} from 'nuxt'
import {presetUno} from 'unocss'
import {presetDaisy} from 'unocss-preset-daisy'

export default defineNuxtConfig({
	modules: ['@unocss/nuxt'],
	unocss: {
		presets: [presetUno(), presetDaisy()],
	},
})
```

### Entrypoint

After configuring the framework, add these imports to your entrypoint:

```js
// `@unocss/reset` comes with `unocss`
// If you are using pnpm, install it separately unless you enable hoisting
import '@unocss/reset/tailwind.css'
import 'uno.css'
```

## Config

This preset accepts [the same config as daisyUI](https://daisyui.com/docs/config/) (except for `logs`, `prefix` and `darkTheme`).

```js
{
	presets: [
		presetUno(),
		presetDaisy({
			styled: false,
			themes: ['light', 'dark'],
		}),
	],
}
```

### Custom themes

Use [UnoCSS's theming system](https://github.com/unocss/unocss#extend-theme) to customize the theme.

```js
{
	presets: [presetUno(), presetDaisy()],
	theme: {
		colors: {
			// Refer to https://daisyui.com/docs/colors/ for colors
			neutral: 'red',
			// Use camelCase instead of kebab-case (e.g. `neutral-focus`)
			neutralFocus: 'green',
			// Use object instead of hyphen for color grades/numbers (e.g. `base-100`)
			base: {
				100: 'blue',
			},
		},
	},
}
```

For details, please read [issue #9](https://github.com/kidonng/unocss-preset-daisy/issues/9#issuecomment-1452292840).

## Limitations

**This is not a full daisyUI port.** All daisyUI components/utilities should work but they may not work with some UnoCSS features:

- [#14](https://github.com/kidonng/unocss-preset-daisy/issues/14): [variants](https://windicss.org/utilities/general/variants.html) do not work

**Unused styles may be imported.** This is both due to lots of hacks being used and how UnoCSS works. However, the preset try to figure out the minimum styles needed, thus the cost is trivial most of the time.
