# `addEvents` in NVD3

[![Gitter](https://badges.gitter.im/HashGrowth/nvd3.svg)](https://gitter.im/HashGrowth/nvd3?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge)

[![Join the chat at https://gitter.im/HashGrowth/nvd3](https://badges.gitter.im/HashGrowth/nvd3.svg)](https://gitter.im/HashGrowth/nvd3?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This repository is extended from [novus/nvd3](https://github.com/novus/nvd3). Before moving ahead,
it is highly recommended to go through [README.md](https://github.com/novus/nvd3/#nvd3---a-reusable-d3-charting-library) of [novus/nvd3](https://github.com/novus/nvd3) to learn about NVD3.

We added `addEvents` functionality to HashGrowth/nvd3. `addEvents` is used for showing events by adding a vertical line on vanilla NVD3 graph, which on hover event displays a popup showing event's description. 

### Customized NVD3 Line Chart with `addEvents`
![customized vanilla nvd3 chart](https://user-images.githubusercontent.com/6450219/28491876-dfada7bc-6f15-11e7-8b3d-798a4d21c93f.png)

You can read more about why we built this function on our [blog]().

### Dependencies

* [d3.js](https://d3js.org/) (NVD3 is dependent on d3.js version 3.5.3 and later but less than v4.x)
* [jQuery](https://jquery.com/) (jQuery is required for `addEvents` feature)

### Usage

1. Add NVD3 assets to your project.
2. Include them to HTML files (make sure to include `nvd3.js` after `d3.js` and `jquery.js`).
3. Plot NVD3 chart.
4. Add `addEvents` function to `nv.addGraph()` function

```
    nv.utils.addEvents(divId, eventsList, chart);
```

### Supported Browsers for `addEvents`

* Google Chrome: latest version
* Safari: latest version
* Firefox: latest version
* Internet Explorer: 10+
* Microsoft Edge: latest version

### Example 

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

## Frequently Asked Questions:

* **How to learn NVD3?**

  Checkout [NVD3](http://nvd3.org/) [examples](http://nvd3.org/examples/index.html) for coding your first chart. 

* **Why did you not send a PR for extended feature to novus/nvd3?**

  [Robin Hu](https://github.com/robinfhu) (Frontend Software Engineer at Novus Partners) [commented](https://github.com/novus/nvd3/issues/1063#issuecomment-110208894) on issue [#1063](https://github.com/novus/nvd3/issues/1063) (titled _"Extending charts?"_) that the officially recommended way to extend NVD3 is by forking the NVD3 repo and just adding the functionality we need into the code directly.
  
* **I need a certain feature. How do I get that?**

  If you want some feature, feel free to create a GitHub issue. You can also upvote any existing issue, so we know it's important to you. While the focus is on building the features that HashGrowth needs, we'll do our best to add a feature for you. And of course, we always appreciate Pull Requests.
 
* **Who is maintaining the repository and whom to contact?**

  [HashGrowth.com](http://hashgrowth.com) is maintaining the repository. Feel free to contact [Adisha Porwal](https://github.com/adishap/) in case of any query.

* **How to contribute?**
  1. Check for [open issues](https://github.com/HashGrowth/nvd3/issues) or open a [new issue](https://github.com/HashGrowth/nvd3/issues/new) to start a discussion around a feature idea or a bug.
  2. Fork the repository on GitHub to start making your changes to the master branch.
  3. Send a pull request and tag the maintainer until it gets merged and published.
