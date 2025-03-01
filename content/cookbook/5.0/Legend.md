---
Title: Configuring Legends - ScottPlot 5.0 Cookbook
Description: A legend is a key typically displayed in the corner of a plot
URL: /cookbook/5.0/Legend/
BreadcrumbNames: ["ScottPlot 5.0 Cookbook", "Configuring Legends"]
BreadcrumbUrls: ["/cookbook/5.0/", "/cookbook/5.0/Legend"]
Date: 2024-04-23
Version: ScottPlot 5.0.27
Version: ScottPlot 5.0.27
SearchUrl: "/cookbook/5.0/search/"
ShowEditLink: false
---

# Configuring Legends


<h2><a href='/cookbook/5.0/Legend/LegendQuickstart'>Legend Quickstart</a></h2>

Many plottables have a Label property that can be set so they appear in the legend.

[![](/cookbook/5.0/images/LegendQuickstart.png?240423091821)](/cookbook/5.0/images/LegendQuickstart.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

var sig1 = myPlot.Add.Signal(Generate.Sin(51));
sig1.LegendText = "Sin";

var sig2 = myPlot.Add.Signal(Generate.Cos(51));
sig2.LegendText = "Cos";

myPlot.ShowLegend();

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>


<h2><a href='/cookbook/5.0/Legend/ManualLegend'>Manual Legend Items</a></h2>

Legends may be constructed manually.

[![](/cookbook/5.0/images/ManualLegend.png?240423091821)](/cookbook/5.0/images/ManualLegend.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

myPlot.Add.Signal(Generate.Sin(51));
myPlot.Add.Signal(Generate.Cos(51));
myPlot.Legend.IsVisible = true;

LegendItem item1 = new()
{
    LineColor = Colors.Magenta,
    MarkerFillColor = Colors.Magenta,
    MarkerLineColor = Colors.Magenta,
    LineWidth = 2,
    LabelText = "Alpha"
};

LegendItem item2 = new()
{
    LineColor = Colors.Green,
    MarkerFillColor = Colors.Green,
    MarkerLineColor = Colors.Green,
    LineWidth = 4,
    LabelText = "Beta"
};

LegendItem[] items = { item1, item2 };
myPlot.ShowLegend(items);

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>


<h2><a href='/cookbook/5.0/Legend/LegendStyle'>Legend Customization</a></h2>

Access the Legend object directly for advanced customization options.

[![](/cookbook/5.0/images/LegendStyle.png?240423091821)](/cookbook/5.0/images/LegendStyle.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

var sig1 = myPlot.Add.Signal(Generate.Sin(51));
sig1.LegendText = "Sin";

var sig2 = myPlot.Add.Signal(Generate.Cos(51));
sig2.LegendText = "Cos";

myPlot.Legend.IsVisible = true;
myPlot.Legend.Alignment = Alignment.UpperCenter;

myPlot.Legend.OutlineColor = Colors.Navy;
myPlot.Legend.OutlineWidth = 5;
myPlot.Legend.BackgroundColor = Colors.LightBlue;

myPlot.Legend.ShadowColor = Colors.Blue.WithOpacity(.2);
myPlot.Legend.ShadowOffset = new(10, 10);

myPlot.Legend.FontSize = 32;
myPlot.Legend.FontName = Fonts.Serif;

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>


<h2><a href='/cookbook/5.0/Legend/LegendOrientation'>Legend Orientation</a></h2>

Legend items may be arranged horizontally instead of vertically

[![](/cookbook/5.0/images/LegendOrientation.png?240423091821)](/cookbook/5.0/images/LegendOrientation.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

var sig1 = myPlot.Add.Signal(Generate.Sin(51, phase: .2));
var sig2 = myPlot.Add.Signal(Generate.Sin(51, phase: .4));
var sig3 = myPlot.Add.Signal(Generate.Sin(51, phase: .6));

sig1.LegendText = "Signal 1";
sig2.LegendText = "Signal 2";
sig3.LegendText = "Signal 3";

myPlot.ShowLegend(Alignment.UpperLeft, Orientation.Horizontal);

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>


<h2><a href='/cookbook/5.0/Legend/LegendWrapping'>Legend Wrapping</a></h2>

Legend items may wrap to improve display for a large number of items

[![](/cookbook/5.0/images/LegendWrapping.png?240423091821)](/cookbook/5.0/images/LegendWrapping.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

for (int i = 1; i <= 10; i++)
{
    double[] data = Generate.Sin(51, phase: .02 * i);
    var sig = myPlot.Add.Signal(data);
    sig.LegendText = $"#{i}";
}

myPlot.Legend.IsVisible = true;
myPlot.Legend.Orientation = Orientation.Horizontal;

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>


<h2><a href='/cookbook/5.0/Legend/LegendMultiple'>Multiple Legends</a></h2>

Multiple legends may be added to a plot

[![](/cookbook/5.0/images/LegendMultiple.png?240423091821)](/cookbook/5.0/images/LegendMultiple.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

for (int i = 1; i <= 5; i++)
{
    double[] data = Generate.Sin(51, phase: .02 * i);
    var sig = myPlot.Add.Signal(data);
    sig.LegendText = $"Signal #{i}";
    sig.LineWidth = 2;
}

// default legend
var leg1 = myPlot.ShowLegend();
leg1.Alignment = Alignment.LowerRight;
leg1.Orientation = Orientation.Vertical;

// additional legend
var leg2 = myPlot.Add.Legend();
leg2.Alignment = Alignment.UpperCenter;
leg2.Orientation = Orientation.Horizontal;

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>


<h2><a href='/cookbook/5.0/Legend/LegendOutside'>Legend Outside the Plot</a></h2>

The default legend can be hidden so that it may be added into a legend panel and displayed outside the data area.

[![](/cookbook/5.0/images/LegendOutside.png?240423091821)](/cookbook/5.0/images/LegendOutside.png?240423091821)

{{< code-sp5 >}}

```cs
ScottPlot.Plot myPlot = new();

var sig1 = myPlot.Add.Signal(Generate.Sin());
var sig2 = myPlot.Add.Signal(Generate.Cos());

sig1.LegendText = "Sine";
sig2.LegendText = "Cosine";

// hide the default legend
myPlot.HideLegend();

// display the legend in a LegendPanel outside the plot
ScottPlot.Panels.LegendPanel pan = new(myPlot.Legend)
{
    Edge = Edge.Right,
    Alignment = Alignment.UpperCenter,
};

myPlot.Axes.AddPanel(pan);

myPlot.SavePng("demo.png", 400, 300);

```

{{< /code-sp5 >}}

<hr class='my-5 invisible'>

