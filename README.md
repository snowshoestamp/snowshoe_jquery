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

Load Animation
--
**Note:** This feature currently works only when stamp data is sent via AJAX. This module comes with the ability to trigger a loading animation as soon as a stamp is touched to the screen.  It comes prebaked with pure CSS animations by [Connor Atherton](http://connoratherton.com/loaders).  To use this feature,

1\. Include `snowshoe.min.css`.  The loading animations are CSS-based and optimized for quick load times.  
2\. Create a set of divs with the following structure and place the id’s `#snowshoe-progress-bar` and `#loader` appropriately.

```html
<!-- Snowshoe loader -->
<div id="snowshoe-progress-bar">
  <div id="loader" class="loader-inner ball-scale-multiple loader-hidden">
    <div></div>
    <div></div>
    <div></div>
  </div>
</div>
```

3\. Change the first two classes on the div with the id `#loader` to reference the load animation of your choice.  Animation options can be found [here](http://connoratherton.com/loaders).

4\. Add the `progressBarOn` key to the initialization data object at the bottom of the page and set its value to `true`.  The plugin will now handle the load animation by dynamically adding/removing the class `.snowshoe-progress-bar` from the element that wears the id `#snowshoe-progress-bar`.

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

The Snowshoe jQuery module dynamically adds the load animation whenever 5 simultaneous touch events occur (i.e. a user touches a stamp to a screen).  It also removes the load animation after the request has completed and the user is redirected to the success screen.

The standard stamp screen and load animation come with the following CSS styles and are used in [this demo](http://wfdemo.herokuapp.com/).  Feel free to override any of them with your own CSS. **Note:** For the stamp screen, please ensure that the width and height are large enough to accomodate the full physical dimensions of your SnowShoe stamp.  We suggest keeping the whole page stampable.

```css
/*STAMP SCREEN*/
#stamp-screen {
  height:100%;
  width:100%;
  position:absolute;
  min-height:480px;
  top:0;
  left:0;
  overflow:hidden;
  text-align:center;
  -webkit-user-select:none;
  -moz-user-select:none;
  -ms-user-select:none;
  user-select:none;
  -webkit-touch-callout:none;
  -webkit-user-drag:none;
  -webkit-tap-highlight-color:rgba(0,0,0,0);
  -webkit-background-size:cover;
  -moz-background-size:cover;
  -o-background-size:cover;
  background-size:cover;
}

/* LOADING ANIMATION CONTAINER */
.snowshoe-progress-bar {
  background:black;
  background:rgba(0,0,0,.75);
  position:absolute;
  top:0;
  left:0;
  height:100%;
  width:100%;
  min-height:480px;
  text-align:center;
  -webkit-user-select:none;
  -moz-user-select:none;
  -ms-user-select:none;
  user-select:none;
  -webkit-touch-callout:none;
  -webkit-user-drag:none;
  -webkit-tap-highlight-color:rgba(0,0,0,0);
  -webkit-background-size:cover;
  -moz-background-size:cover;
  -o-background-size:cover;
  background-size:cover
}

/* Positions the load animation */
#loader {
  position:absolute;
  top:50%;
  left:49%
}
```
Also, if you’d like to implement your own loader, simply remove the `progressBarOn` key from your initialization data object or set it to `false`.

If you have any questions, we’re just a click away -  [support@snow.sh](mailto:support@snow.sh).

## Contribute
Join us in improving this client by making a pull request.

## License
MIT (see LICENSE file)