Snowshoe jQuery
============
Front-end client to submit Snowshoe stamp point data to your backend.

## Current Version
- 0.3.0

## Dependencies
- jQuery (>= 1.8.x)

## Usage
### Stamp screen
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

### Progress Bar Animation
This module comes with the ability to trigger a loading animation as soon as a stamp is touched to the screen.  To use this feature,

1\. Include `snowshoe-sample.css`.  The loading animation is CSS-based and optimized for quick load times.

```html
<!-- Snowshoe loader CSS -->
<link rel="stylesheet" href="snowshoe-sample.css">

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

### Help Messages
If a user is having trouble with their stamp, displaying help messages to them can be useful.

1\. Include `snowshoe-sample.css`.  This includes default styling to display the messages. Feel free (and you should) customize this css as needed.

```html
<!-- Snowshoe messages CSS -->
<link rel="stylesheet" href="snowshoe-sample.css">

```

2\. Create a div with the id of `#snowshoe-messages`.

```html
<!-- Snowshoe messages -->
<div id="snowshoe-messages"></div>
```

3\. To add helpful messaging for when a user isn't touching the stamp to the screen fully, insert an html block in the initialization data.

```javascript
<script>
var stampScreenInitData = {
  "postUrl": "http://mydomain.com/stampscreen",
  "stampScreenElmId": "stamp-screen",
  "progressBarOn": true,
  "messages": {
    "insufficientPoints" : "<h3>Try again!</h3>"
  }
}
</script>
<script src="jquery.snowshoe.js"></script>
```

4\. If you are using ajax to send stamp data to your backend, you can likewise append a helpful error messaging html block in the error callback to let your users know that a stamp wasn't recognized.

```javascript
<script>
var stampScreenInitData = {
  "postUrl": "http://mydomain.com/stampscreen",
  "stampScreenElmId": "stamp-screen",
  "progressBarOn": true,
  "messages": {
    "insufficientPoints" : "<h3>Try again!</h3>"
  },
  "postViaAjax": true,
  "success": function(response){
    // handle success
    console.log("Success!");
    // clear screen
    $('#snowshoe-progress-bar').removeClass("snowshoe-progress-bar");
    $("#snowshoe-messages").empty();
  },
  "error": function(response){
    // handle failure
    console.log(" :-( ");
    // clear screen
    $('#snowshoe-progress-bar').removeClass("snowshoe-progress-bar");
    $("#snowshoe-messages").empty();
    // show failure message
    $("#snowshoe-messages").append("<h3>That stamp was not found. Please try again!</h3>");
  }
}
</script>
<script src="jquery.snowshoe.js"></script>
```

Again, feel free to override any of snowshoe-sample.css with your own, just be sure to keep the element id `#snowshoe-messages` on the div you want to append your help message html blocks to.

## Contribute
Join us in improving this client by making a pull request.

Be sure to, as necessary:
- Increment jquery.snowshoe.js version (in comment header)
- Update the CHANGELOG
- Update this README
- Include jquery.snowshoe.js version in your commit message

## License
MIT (see LICENSE file)
