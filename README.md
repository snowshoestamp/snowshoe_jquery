Snowshoe jQuery
============
Front-end client to submit Snowshoe stamp point data to your backend.

## Dependencies
- jQuery (>= 1.8.x)

## Usage
At the bottom of any page you want to make "stampable", create an object with initialization data and include the Snowshoe jQuery module. <code>$.snowshoe</code> will construct the necessary touch event listener and client to submit stamp data to your backend.

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

## Contribute
Join us in improving this client by making a pull request.

## License
MIT (see LICENSE file)
