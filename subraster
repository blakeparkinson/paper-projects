// Create a raster item using the URL
var raster = new Raster("http://paperjs.org/tutorials/images/working-with-rasters/mona.jpg");

// Move the raster to the center of the view
raster.position = view.center;

var imageWidth = 320;
var imageHeight = 491;
imageWidth = raster.size.width;
imageHeight = raster.size.height;
var startDrag, endDrag;

// this is the value needed to adjust the coordinates
// not the image size.
var lt = raster.bounds.topLeft;

console.log('lt', lt, 'rs', raster.size);

function onMouseDown(event) {
    startDrag = new Point(event.point);   
}

function onMouseDrag(event) {
    var show = new Path.Rectangle({
        from: startDrag,
        to: event.point,
        strokeColor: 'red',
        strokeWidth: 1
    })
    // stop showing the selected area on drag (new one
    // is created) and up because we're done
    show.removeOn({
        drag: true,
        up: true
    })
}

function onMouseUp(event) {
    endDrag = new Point(event.point);
    var bounds = new Rectangle({
        from: startDrag - lt,
        to: endDrag - lt
    })
    console.log(bounds);
    
    // // Whiteout area beneath selection
    // var whitedOutSelection = new Shape.Rectangle(bounds);
    // whitedOutSelection.fillColor = 'white';
    // whitedOutSelection.position = bounds.center + new Point(lt.x, lt.y);
        
    var subRaster = raster.getSubRaster(bounds);
    subRaster.position = paper.view.center;
}
