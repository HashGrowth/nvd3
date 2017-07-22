## `addEvents` in NVD3

[![Join the chat at https://gitter.im/HashGrowth/nvd3](https://badges.gitter.im/HashGrowth/nvd3.svg)](https://gitter.im/HashGrowth/nvd3?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This repository is extended from [novus/nvd3](https://github.com/novus/nvd3). Before moving ahead,
we highly recommend to go through [README.md](https://github.com/novus/nvd3/#nvd3---a-reusable-d3-charting-library) of [novus/nvd3](https://github.com/novus/nvd3) for usage and learning NVD3.

It has one additional functionality `addEvents` for showing events by adding a vertical line, which on hover event displays a popup showing event's description on graph. You can read more about why we built this function on our [blog]().

## Requirements
* [d3.js](https://d3js.org/) (NVD3 is dependent on d3.js)
* [jQuery](https://jquery.com/) (addEvents feature requires jQuery)

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
Checkout the [examples/lineChart.html](https://github.com/HashGrowth/nvd3/blob/master/examples/lineChart.html) for complete code.

## To Do:
* Remove the jQuery dependency, such that the only library required is d3.js.
* options to change look and feel of vertical line and popups

## Frequently Asked Questions:
* **How to learn NVD3?**

  Checkout [NVD3](http://nvd3.org/) [examples](http://nvd3.org/examples/index.html) for coding your first chart. 

* **Why did you not send a PR for extended feature to novus/nvd3?**

  [Robin Hu](https://github.com/robinfhu) (Frontend Software Engineer at Novus Partners) [commented](https://github.com/novus/nvd3/issues/1063#issuecomment-110208894) on issue [#1063](https://github.com/novus/nvd3/issues/1063) (titled _"Extending charts?"_) that the officially recommended way to extend NVD3 is by forking the NVD3 repo and just adding the functionality we need into the code directly.