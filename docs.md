# Documentation

### Installation

Clone this component.

```bash
git clone https://github.com/XPCMasterX/option-menu.git
```

Copy the folder to your project so your `src` looks something like this:

```
src/
    └───App.svelte
    └───index.js
    └───lib/
        └───OptionMenu.svelte
```

Then import it in your `App.svelte` file.

```js
import OptionMenu from 'lib/OptionMenu.svelte';
```

### How to use OptionMenu.svelte

You need to bind a data object to the component like this:

```html
<OptionMenu bind:data="{config}"></OptionMenu>
```

See below for how the data object should look like.

### Config

Example data object.

```js
let data = {
  options: [],
};
```

`options` is an array containing objects. An example is shown below.

```js
{
    /*
     @required
     Possible values so far: [range]
    */
    type: "range"
    /*
     @required for `type: range`
     Must be smaller than `max`
    */
    min: "0",
    /*
     @required for `type: range`
     Has to be bigger than `min`
    */
    max: "100",
    /*
     @required for `type: range`
     Must be in between `min` -> `max`
    */
    start: "50",
    /*
     @required for `type: range`
    */
    label: "Slider",
    /*
     @required
     Must be unique or it won't work
    */
    id: "slider-one"
}
```

So overall, the data object would look like this:

```html
<script>
  import OptionMenu from 'path/to/file/called/OptionMenu.svelte";

  let data = {
    options: [{
      type: "range",
      min: "0",
      max: "100",
      start: "50",
      label: "Slider",
      id: "slider-one"
    }],
  };
</script>
<OptionMenu bind:data="{config}"></OptionMenu>
```
