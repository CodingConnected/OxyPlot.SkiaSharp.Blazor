# OxyPlot.SkiaSharp.Blazor

The cross-platform plotting library - [OxyPlot](https://github.com/oxyplot/oxyplot) - is now available for Webassembly using Blazor and [SkiaSharp](https://github.com/mono/SkiaSharp). This project is based on [the original source by JensKrumsieck](https://github.com/JensKrumsieck/OxyPlot.SkiaSharp.Blazor).

<img src="https://github.com/CodingConnected/OxyPlot.SkiaSharp.Blazor/raw/main/.github/screen.png" alt="Screenshot" width="600" />


### [LIVE DEMO](https://blazor-playground.vercel.app/plot/)

### Installation
```
dotnet add package OxyPlot.SkiaSharp.Blazor
```

### Usage
```razor
<PlotView Model=model style="height: 30vh"/>
@code{
    private PlotModel model = new PlotModel();
    ...
    protected override async Task OnInitializedAsync()
    {
        var data = GetSomeDataPoints(); //get datapoint array from somewhere
        var spc = new LineSeries()
        {
            ItemsSource = data,                
            Title = "UV/Vis Data",
            TrackerFormatString = "{0}<br/>{1}: {2:0.00} - {3}: {4:0.00}"
        };
        model.Series.Add(spc);
    }
}

A note on fonts: in order to use a non-default font in WebAssembly, you need to embed it in your app as an embedded resource. Otherwise, OxyPlot.SkiaSharp will not be able to load it. Include all variants you need, like regular, bold, italic, etc.

Requirements:
* .NET 9.0
* SkiaSharp.Views.Blazor v3.116.1
* OxyPlot.SkiaSharp v2.2.0
