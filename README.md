# ember-component-css [![Build Status](https://travis-ci.org/ebryn/ember-component-css.svg?branch=master)](https://travis-ci.org/ebryn/ember-component-css)

An Ember CLI addon which allows you to specify CSS inside of component pod directories

[The announcement from EmberConf 2015](https://youtu.be/T1zxaEKeq3E)
[![CSS is hard - EmberConf 2015](http://f.cl.ly/items/1a3a3r1C1y0D060D3j3u/EmberConf%202015%20-%20CSS%20Is%20Hard%20-%20YouTube%202015-03-22%2018-33-41.jpg)](https://youtu.be/T1zxaEKeq3E)

## Installation

`ember install ember-component-css`

## Usage

This addon allows you to specify a `styles.css` file inside of your component's pod folder (`app/my-component/styles.css`) (the component must also provide a `component.js` returning a valid instance of `Ember.Component`).

Rules defined inside of these `styles.css` files will automatically be namespaced with an autogenerated class. That autogenerated class will also be injected into your component's `classNames` property. This enables you to worry less about rules clashing across component styles.

For example, given this `app/my-component/styles.css` file:

```css
& {
  padding: 2px;
}
.urgent {
  color: red;
}
```

Your generated CSS output will look something like: 

```css
.my-component-a34fba {
  padding: 2px;
}
.my-component-a34fba .urgent {
  color: red;
}
```

A typical component invocation that looks like this:

`{{my-component}}`

will generated markup like:

`<div class="my-component-a34fba"></div>`

### With Preprocessors

To use this addon with a CSS pre-processor, import `pod-styles` into your base stylesheet. (see your pre-processor docs)

```scss
// app/styles/app.scss
@import "pod-styles";
```

And that is it! The `pod-styles` file is generated during the build and will then be pulled into your other stylesheet to be processed like normal.

**Approved preprocessors:**

 - [`ember-cli-sass`](https://github.com/aexmachina/ember-cli-sass)
 - [`ember-cli-less`](https://github.com/gdub22/ember-cli-less)
 - [`ember-cli-stylus`](https://github.com/drewcovi/ember-cli-stylus)
