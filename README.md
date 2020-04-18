## Vue Theming Bootstrap

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

## Demo
https://rehmatfalcon.github.io/vue-bootstrap-theming/

## Screenshot

![dark_light](https://user-images.githubusercontent.com/28915667/79636634-f3971b80-8198-11ea-809b-ca14809cac66.png)

## Motivation

1. To integrate bootstrap with vue and make theming possible.
1. To adapt bootstrap according to project requirement by changing its variables.

## Procedures followed:
1. Add bootstrap to project
```bash
npm i bootstrap jquery popper
// Jquery and popper were added because 
// bootstrap relies on them for some of its functionality 
```

2. Create a styles file and import bootstrap scss there.
```scss
@import '~bootstrap/scss/boostrap';
// add any new styles / overrides
```

3. Import the styles file in our app.
> App.vue
```js
<style>
import './styles';
</style>
```

Once we have done the above, we can use bootstrap classes in our application.

Blog.vue (For example)
```js
<template>
    <div class="row">
        <div class="col">
            <button class="btn btn-primary">
                Primary
            </button>
        </div>
    </div>
</template>
```

## Theming

Bootstrap exposes its configuration as SASS variables. So, in order to have multiple theme, its just a matter of generating different classes with adjusted variable values.

```scss
.theme-dark {
    $card-color : #d8d5d5;
    $card-bg: rgb(65, 65, 65);
    $card-cap-color: #ebebeb;
    $card-cap-bg: darken($card-bg, 5%);
}
```
This sets the background color and text of the card component.


Currently two themes are supported : light and dark.

~~When the theme is light, a `theme-light` class is added to the body element.~~

~~When dark theme is chosen, a `theme-dark` class is added to the body element.~~

In order to allow for multiple themes for multiple component, now the classes `theme-light` and `theme-dark` are applied to the root element of the component.

The allows us to render different parts of the app with different theme.

#### Js counterpart
In the js, we check the current theme and apply correct class to the body element.

We also add a `temp-transitional` class to the ~~body~~ component element for one second. This is done to ensure that the transition from light to dark theme and vice versa does not feel abrupt.

```scss
.temp-transitional {
  &, & *, & *:before, & *:after {
    transition: all .3s;
  }
}
```
temp-transitional is defined as above.

We also save the selected theme in localstorage, so that the user choice is persisted across request.
