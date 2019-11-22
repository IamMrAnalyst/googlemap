//googlemap
In <!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Street View containers</title>
    <style>
      html, body, #map-canvas {
        height: 100%;
        margin: 0px;
        padding: 0px
      }
    </style>
    <script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyDw3Mu5bwFIBbUgI1nh-JIZBj4AGHgrGFU"></script>
    <script>
function initialize() {
  var params = getQueryParams();
  var bryantPark = new google.maps.LatLng(params.lat, params.lon);
  var panoramaOptions = {
    position: bryantPark,
    pov: {
      heading: 165,
      pitch: 0
    },
    zoom: 1
  };
  var myPano = new google.maps.StreetViewPanorama(
      document.getElementById('map-canvas'),
      panoramaOptions);
  myPano.setVisible(true);
}
function getQueryParams(){
    var params = {};
    var query = window.location.search.substring(1);
    var vars = query.split("&");
    for (var i=0;i<vars.length;i++) {
        var pair = vars[i].split("=");
        if(pair.length == 2)
        {
            params[pair[0]] = pair[1];
        }
     }
     return params;
}
google.maps.event.addDomListener(window, 'load', initialize);
    </script>
  </head>
  <body>
    <div id="map-canvas"></div>
  </body>
</html>
