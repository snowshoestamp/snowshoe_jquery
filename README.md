Snowshoe jQuery
============
Front-end client to submit Snowshoe stamp point data to your backend.

## Dependencies
- jQuery (>= 1.8.x)

## Usage
Stamp screen
--
At the bottom of any page you want to make "stampable", create an object with initialization data and include the Snowshoe jQuery module. ``$.snowshoe`` will construct the necessary touch event listener and client to submit stamp data to your backend.

```javascript
<script>
  var stampScreenInitData = {
    "postUrl": "http://mydomain.com/stampscreen",
    // element id of what you want to be stampable
    // this can be on a canvas, div or the body
    "stampScreenElmId": "stamp-screen"
  }
</script>
<script src="jquery.snowshoe.js"></script>
```

Optionally, post via AJAX and handle success/failure in the client.
```javascript
<script>
var stampScreenInitData = {
  "postUrl": "http://mydomain.com/stampscreen",
  "stampScreenElmId": "stamp-screen",
  "postViaAjax": true, // post via Ajax  
  "success": function(response){
    // handle success
    console.log("Success!");
  },
  "error": function(response){
    // handle failure
    console.log(" :-( ");
  }
}
</script>
<script src="jquery.snowshoe.js"></script>
```

Progress Bar Animation
--
This module comes with the ability to trigger a loading animation as soon as a stamp is touched to the screen.  It comes prebaked with a simple CSS animation of loading dots courtesy of [Ken Lauguico](http://codepen.io/kenlauguico/).  To use this feature,

1\. Include `snowshoe.min.css`.  The loading animations are CSS-based and optimized for quick load times.

```html
<!-- Snowshoe loader CSS -->
<link rel="stylesheet" href="snowshoe.min.css">

```

2\. Create a div with the id of `#snowshoe-progress-bar`.

```html
<!-- Snowshoe loader -->
<div id="snowshoe-progress-bar"></div>
```

3\. Add the `progressBarOn` key to the initialization data object at the bottom of the page and set its value to `true`.  The plugin will now handle the load animation by dynamically adding the class `.snowshoe-progress-bar` to the element that wears the id `#snowshoe-progress-bar`.

```javascript
<script>
var stampScreenInitData = {
  "postUrl": "http://mydomain.com/stampscreen",
  "stampScreenElmId": "stamp-screen",
  "progressBarOn": true,
  "postViaAjax": true, // post via Ajax  
  "success": function(response){
    // handle success
    console.log("Success!");
  },
  "error": function(response){
    // handle failure
    console.log(" :-( ");
  }
}
</script>
<script src="jquery.snowshoe.js"></script>
```

The Snowshoe jQuery module dynamically adds the load animation class whenever 5 simultaneous touch events occur (i.e. a user touches a stamp to a screen).

Feel free to override any of the CSS with your own. Also, if you’d like to implement your own loader, simply remove the `progressBarOn` key from your initialization data object or set it to `false`.

## Contribute
Join us in improving this client by making a pull request.

## License
MIT (see LICENSE file)
