&lt;imported-template&gt;
==============

`<imported-template>` is a custom element that let's you load template from external file into your document, and take full control over loaded `<script>`s and `<link rel="import">`s. Thanks to HTML Imports - caching, script execution, etc. is completely native.

### Small sample

If you have **/path/to/file.html**:
```html
<template>
	<h1>Hello {{username}}</h1>
</template>
```
```javascript
var model = {
  appdata: {
    username: "World"
  },
  html: "/path/to/file.html"
}
```
You can put it on screen with
```html
<template is="imported-template" content="{{ html }}" bind="{{ appdata }}"></template>
```
To produce
```html
<h1>Hello World</h1>
```

## Demo/Examples

[Check it live!](http://juicy.github.io/imported-template/examples/index.html)

## Features

 - Applies two-way databinding, even for nested asynchronously loaded `<polymer-element>`s,
 - Multiple (concatenated) templates per partial, 
 - Polymer's `<template>` features (binding, repeat, if, etc.),
 - HTML Imports features: 
  - Sends request for template only once (HTML Import's caching),
  - Supports `<script>, <link>, <style>` tags to be executed once,
  - Supports `<script>, <style>` tags per template instance.

### Partial limitations

 - It should be W3C compliant Document body,
 - It should contain at least one `<template>` tag in root node.

### Rationale

`imported-template` evolved out of [x-html](https://github.com/PuppetJs/x-html) (now [`juicy-html`](https://github.com/Juicy/juicy-html) ) due to need for better control of `<scripts>` and HTML Imports execution. See ongoing discussion [here](https://github.com/Juicy/juicy-html/issues/8)


## Install

Install the component using [Bower](http://bower.io/):

```sh
$ bower install imported-template --save
```

Or [download as ZIP](https://github.com/Juicy/imported-template/archive/gh-pages.zip).

## Usage

1. Import Web Components' polyfill:

    ```html
    <script src="bower_components/webcomponentsjs/webcomponents.js">
    ```

2. Import Custom Element:

    ```html
    <link rel="import" href="bower_components/imported-template/imported-template.html">
    ```

3. Start using it!

    ```html
    <template is="imported-template" content="./your/partial.html"></template>
    ```

## Options/Attributes
We [plan](https://github.com/Juicy/imported-template/issues/1) to support other `<template>` attributes given by [TemplateBinding](http://www.polymer-project.org/docs/polymer/template.html)

Attribute    | Options       | Default          | Description
---          | ---           | ---              | ---
`content`    | *string*		 | `""`				| Safe HTML code, or path (starts with `/` or `./`) to partial to be loaded.
`iframe`     | *boolean*	 | `false`			| Indicate misbehaved partial to be loaded in `<iframe>`.


### Dependencies

`<imported-template>` is dependent on [Polymer](http://www.polymer-project.org/) as a polyfill for Web Components APIs. It also relies on [TemplateBinding](http://www.polymer-project.org/docs/polymer/template.html)

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request :D

## History

For detailed changelog, check [Releases](https://github.com/Juicy/imported-template/releases).

## License

[MIT License](http://opensource.org/licenses/MIT)
