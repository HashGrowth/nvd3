## addEvents in NVD3

This repository is extended from [novus/nvd3](https://github.com/novus/nvd3).

It has one additional functionality `addEvents` for showing events by adding a vertical line, which on hover event displays a popup showing event's description on graph.

## Requirements
* d3.js (NVD3 is dependent on d3.js)
* jQuery (addEvents feature requires jQuery)

## Usage 

```
    nv.utils.addEvents(divId, eventsList, chart);

```

## Example 

```
var events = {
    "x1": "event details for x1",
    "x2": "event details for x2",
    "x3": "event details for x3",
    "x4": "event details for x4"
};

nv.addGraph(function() {
    var chart = nv.models.lineChart()
        .useInteractiveGuideline(true);

    chart.xAxis
        .axisLabel('Time (ms)')
        .tickFormat(d3.format(',r'));

    chart.yAxis
        .axisLabel('Voltage (v)')
        .tickFormat(d3.format('.02f'));

    d3.select('#chart svg')
        .datum(data())
        .transition().duration(500)
        .call(chart);

    nv.utils.windowResize(chart.update);

    // Add events by providing list of events
    nv.utils.addEvents('#chart', events, chart);
    return chart;
});

```

## To Do:
* Remove the jQuery dependency, such that the only library required is d3.js. (Enhancement)

## Frequently Asked Questions:
* **How to learn NVD3?**

  Checkout [NVD3](http://nvd3.org/) [examples](http://nvd3.org/examples/index.html) for coding your first chart. 

* **Why did you not create a PR for extended feature?**

  [Robin Hu](https://github.com/robinfhu) (core contibuter of NVD3) [commented](https://github.com/novus/nvd3/issues/1063#issuecomment-110208894) on the issue([#1063](https://github.com/novus/nvd3/issues/1063)) created for extending NVD3 that extending basically involves forking the NVD3 repo and just adding the functionality you need into the code directly. We don't have that many 'hooks' into the rendering logic unfortunately. It's a good chance to learn how NVD3 works too! 
