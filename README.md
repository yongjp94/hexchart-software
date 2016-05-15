# Hexchart

The hexchart software takes in a parsed data format of arrays of arrays containing x and y coordinates.
It then, analyzes the population of data points on the canvas and creates a heatmap in a hexagonal format.

First, instantiate a hexchart and pass in your tag selection for where you want to visualization to appear in.
```javascript
var chart = hexChart(selection);
```

```javascript
// This generates a random set of 2000 points on the canvas for demonstration.
    var randomX = d3.random.normal(hexChart.width() / 4, 80),
        randomY = d3.random.normal(hexChart.height() / 2, 80),
        points = d3.range(2000).map(function() { return [randomX(), randomY()]; });
    
    // Use this to observe your dataset in the console.
    console.log(points);
```

The data set of points looks something like this:
[ [x1,y1] , [x2,y2], [x3,y4], ... [x2000,y2000] ]

Because the 'datum' or one set of data is already included in an array,
you must pass the data in without surrounding it in another array when binding the data to the chart.
```javascript
  // CORRECT!
  var chartWrapper = d3.select('#my-div')
      .datum(points)
      .call(hexChart);
  
  // INCORRECT :(
  var chartWrapper = d3.select('#my-div')
      .datum([points])
      .call(hexChart);
```

Your finished product should look something like this!
![alt tag](http://i.imgur.com/KAsJNaH.png?1)

You also have an option to change the width and height of the canvas
```javascript
// returns current height
chart.height()

// changes height to val and returns chart function
chart.height(val)

// returns current width
chart.width()

// changes width to val and returns chart function
chart.width()
```
