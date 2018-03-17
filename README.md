[![Build Status](https://travis-ci.org/onaluf/fate.svg?branch=master)](https://travis-ci.org/onaluf/fate) [![NPM version](https://img.shields.io/npm/v/fate-editor.svg)](https://www.npmjs.com/package/fate-editor) [![MIT license](http://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

# Flexible Angular Text Editor

Fate is a rich text editor (wysiwyg) natively written for angular (>= v2) in typescript with footprint and flexibility in mind. Its goal is to be very easy to customize and be as small as it can thanks to tree shaking. Bootstrap and Google Material styled version are included to fit in forms using those styles. To use the material one you will need to include [Angular Material]("https://material.angular.io) in your project.

Be warned that it's very early in the development of this module so many thing will change.

For a live demo of the editor you can go to [the project's site](https://onaluf.github.io/fate).

# Installation and usage

Use npm to download the module: `npm install --save fate-editor`. Then import the `FateModule` in your app:
```typescript
import { FateModule } from 'fate-editor';
// ...

@NgModule({
  // ...
  imports: [
    // ...
    FateModule
  ]
  // ...
}) // ...
```

# Available Component

## fate-input
This is the rich text input, it's a low level component that basically looks like a textbox. On it's own it doesn't have any UI to control the text but will respond to you system keyboard shortcut.
### Properties
#### uiId
This is the id of the UI component that should target this input box. By default all inputs respond to all UIs which is normally not what you want. By specifying the uiIds you can choose which one to pair together.
#### row
This the number of row of text the input should show by default. This mimics the behaviour of the same property on textarea. Note that by default `fate-input` is resizable vertically so this only specifies the default height.
#### placeholder
This is the placeholder text that will show when the input is empty and nothing is selected.
#### ngModel
You can use `ngModel` like you would on any other input element and it will behave the same. The value that will be read and exported is dependent of the parser you've decided to inject, by default it's HTML.

## fate-ui
This is the default UI for your input. It shows a bunch of buttons on a toolbar-like block. You can choose which buttons are available through the `buttons` property.
### Properties
#### uiId
This allow you to choose which `fate-input` is targeted by this UI. For example you could do:
```html
<fate-ui uiId="foo"></fate-ui>
<fate-input uiId="foo" [(ngModel)]="someHtml"></fate-input>
```
#### buttons
This is an array of strings that define which buttons should be shown in which order, you can add `"separator"` at any position to add a separator between two buttons. Under the hood it's just using the two previously described components and styling them. You don't need to specify any `uiId` because they are generated automatically.

## fate-bootstrap
This is a all-in-one component that includes a UI and an input. It's mean to be a drop-in replacement to textarea in Bootstrap forms
### Properties
#### row
This the number of row of text the input should show by default. This mimics the behaviour of the same property on textarea. Note that by default `fate-input` is resizable vertically so this only specifies the default height.
#### placeholder
This is the placeholder text that will show when the input is empty and nothing is selected.
#### ngModel
You can use `ngModel` like you would on any other input element and it will behave the same. The value that will be read and exported is dependent of the parser you've decided to inject, by default it's HTML.

## fate-material
This is a all-in-one component that includes a UI and an input. It's mean to be a drop-in replacement to textarea in Material forms
### Properties
#### row
This the number of row of text the input should show by default. This mimics the behaviour of the same property on textarea. Note that by default `fate-input` is resizable vertically so this only specifies the default height.
#### placeholder
This is the placeholder text that will show when the input is empty and nothing is selected.
#### ngModel
You can use `ngModel` like you would on any other input element and it will behave the same. The value that will be read and exported is dependent of the parser you've decided to inject, by default it's HTML.
