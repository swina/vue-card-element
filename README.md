# | vue-card-element

vue-card-element is a Vue component to create a multipurpose card. vue-card-element has many options and can be used in different situations like:
- dashboard statistic information
- business card
- product card

See demo for details.

## Features
- default size works on desktop, laptop, mobile (max width 320px), but each canvas can be set with custom width and height (px,%,em,rem accepted)
- 3 actions slots ($emit(...))
- custom options for visual impact (colors, icons, images, etc.)
- flip effect available (onclick) with a new configurable canvas
- HTML injection available for almost all elements

## Demo

[Demo](https://jzoq53ovxw.codesandbox.io/)

For full demo examples code
[SandBox](https://codesandbox.io/s/jzoq53ovxw)

## Installation

```
npm install vue-card-element
```

## Usage
Import component
```
import VCardElement from 'vue-card-element'
```

In template (for options and configuration see Docs below)
```
...
  <v-card-element
    title="your title"
    label="your label"
    ....
  />
...
```

# Docs
```vue-card-element``` has many options that you can control in order to fit with your template/layout/app.

We designed the component in order to make compatible with a clean project so we decided to not include any dependency. For this reason you can add to any Vue project as is, without depending on third libraries, or simply using yours.

For any issue please open an issue on github repository.

[GitHub](https://github.com/swina/vue-card-element)


## Props
| Prop | Required | Description | Type | Default | Notes
| :--- | :--- | :--- | :--- | :---  | :---
| name | YES | name or ID of canvas | String | | Used to assign $emit events
| width | NO | canvas width | String | 320px | standard CSS values (px,%, rem, ecc,)
| height | NO | canvas width | String | 10.5rem | standard CSS value
| title | NO | canvas title | String | Title | HTML injection available
| label | NO | canvas label | String | Label | HTML injection available
| content | NO | canvas content | String | abstract | HTML injection available
| color | NO | background color/image | String | #FFF | CSS or url(image_url) or image_uri
| text_color | NO | color for all text elements | String | #555 | standard CSS value |
| icon_box | NO | background color of icon box | String | #fff | standard CSS value |
| icon_color | NO | color of icon box icon | String | #555 | standard CSS value|
| icon | NO | icon | String | | HTML injection available |
| image | NO | image to set in the icon box | String | | url(your image) or image uri |
| elevation | NO | box shadow setting | String | '0' | 1 thru 3 elevations available
| divider | NO | set a divider line between content and footer | String | '0' | set the px border height as divider |
| flip | NO | enable/disable flipping canvas | Boolean | false | |
| flip_text | NO | help text to click for flip | String | 'more' | |
| back_color | NO | background color of the flipped canvas | String | #fff | standard CSS value
| back_content | NO | content of the flipped canvas | String | | any HTML code |
| slot_1 | NO | left button slot of the footer | String | | HTML injection available |
| slot_2 | NO | center button slot of the footer | String | | HTML injection available |
| slot_3 | NO | right button slot of the footer | String | | HTML injection available |


## Events
vue-card-element emits 1 event (this.$emit(...)) in order to get the following user actions:
- click on the footer left button/link
- click on the footer center button/link
- click on the footer right button/link

Since there are 3 clickable area available in the canvas footer that you can customize with your HTML code a click on each of this area emits one event with the following info:
- function ( name , slot )
where name is the canvas name and slot the slot clicked
You  need at least 1 slot option set in order to use the emit event.

| Event | Required | Description | Type |  Return
| :--- | :---: | :--- | :--- | :---  |
| @slotClick | NO | click on one of the three clickable area | Function | -name of canvas(String)<br>-slot clicked(Number) |

In your template you have to set a function that get the emitted event.
Example
```
<template>
  ...
  <v-card-element
    name="box3"
    color="#e91e63"
    label="New orders"
    title="<h1>+110</h1>"
    content=""
    ...
    slot_2="<button class='btn'>Click to get info</button>"
    @slotClick="myFunction"
  />
  ...
</template>
<script>
export default {
  ...
  methods:{
    myFunction(card,slot){
      //@card: card name
      //@slot: slot clicked (1,2 or 3)
      //set your logic here
    }
  }
  ...
}
</script>
```

### Notes
Development or demo Component uses Google Material Design icons. If you don't have any icons library you can add to your index.html

```
<link href="https://fonts.googleapis.com/css?family=Roboto:100,300,400,500,700,900|Material+Icons" rel="stylesheet">

```

### License
Released under MIT license.
