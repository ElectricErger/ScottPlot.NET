---
Title: Callout - ScottPlot 5.0 Cookbook
Description: Callouts display a label and are connected with an arrow that marks a point on the plot.
URL: /cookbook/5.0/Callout/
BreadcrumbNames: ["ScottPlot 5.0 Cookbook", "Callout"]
BreadcrumbUrls: ["/cookbook/5.0/", "/cookbook/5.0/Callout"]
Date: 2024-04-23
Version: ScottPlot 5.0.27
Version: ScottPlot 5.0.27
SearchUrl: "/cookbook/5.0/search/"
ShowEditLink: false
---

# Callout


<h2><a href='/cookbook/5.0/Callout/CalloutQuickstart'>Callout Quickstart</a></h2>

Callouts display a label and are connected with an arrow that marks a point on the plot.

[![](/cookbook/5.0/images/CalloutQuickstart.png?240423091821)](/cookbook/5.0/images/CalloutQuickstart.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

double[] xs = Generate.Consecutive(15);
double[] ys = Generate.Sin(15);
myPlot.Add.Scatter(xs, ys);

myPlot.Add.Callout("Hello",
    textLocation: new(7.5, .8),
    tipLocation: new(xs[6], ys[6]));

myPlot.Add.Callout("World",
    textLocation: new(10, 0),
    tipLocation: new(xs[13], ys[13]));

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>

