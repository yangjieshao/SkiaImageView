# SkiaImageView

![SkiaImageView](Images/SkiaImageView.100.png)

[![Project Status: Active – The project has reached a stable, usable state and is being actively developed.](https://www.repostatus.org/badges/latest/active.svg)](https://www.repostatus.org/#active)

## NuGet

|Package|NuGet|
|:--|:--|
|SkiaImageView.Wpf|[![NuGet SkiaImageView.Wpf](https://img.shields.io/nuget/v/SkiaImageView.Wpf.svg?style=flat)](https://www.nuget.org/packages/SkiaImageView.Wpf)|
|SkiaImageView.Xamarin.Forms|[![NuGet SkiaImageView.Xamarin.Forms](https://img.shields.io/nuget/v/SkiaImageView.Xamarin.Forms.svg?style=flat)](https://www.nuget.org/packages/SkiaImageView.Xamarin.Forms)|
|SkiaImageView.Avalonia|[![NuGet SkiaImageView.Avalonia](https://img.shields.io/nuget/v/SkiaImageView.Avalonia.svg?style=flat)](https://www.nuget.org/packages/SkiaImageView.Avalonia)|

----

## What is this?

Easy way showing [SkiaSharp](https://github.com/mono/SkiaSharp)-based image objects onto UI applications.
You can simply bind a SkiaSharp image object to `Source` property.

`SKImageView` is a control of SkiaSharp image drawing.
You can manipulate same as with [WPF's `System.Windows.Controls.Image`](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.image?view=windowsdesktop-6.0).

Supported SkiaSharp types are: `SKBitmap`, `SKImage`, `SKPicture`, `SKDrawable` and `SKSurface`.

XAML example:

```xml
<Window xmlns:siv="https://github.com/kekyo/SkiaImageView">
    <siv:SKImageView
        Stretch="Uniform"
        Source="{Binding PreviewImage}" />
</Window>
```

Fully sample code is here:

* [SkiaImageView.Wpf.Sample](https://github.com/kekyo/SkiaImageView/tree/main/samples/SkiaImageView.Wpf.Sample)
* [SkiaImageView.Xamarin.Forms.Sample](https://github.com/kekyo/SkiaImageView/tree/main/samples/SkiaImageView.Xamarin.Forms.Sample)
* [SkiaImageView.Avalonia.Sample](https://github.com/kekyo/SkiaImageView/tree/main/samples/SkiaImageView.Avalonia.Sample)

----

## Supported platform

* SkiaSharp: 2.80.0 or upper.

### WPF

* .NET 6.0, 5.0 (`net6.0-windows`, `net5.0-windows`)
* .NET Core 3.1, 3.0 (`netcoreapp3.1`, `netcoreapp3.0`)
* .NET Framework 4.8, 4.6.2 (`net48`, `net462`)

### Xamarin Forms

* .NET Standard 2.0 (`netstandard2.0`)
* Xamarin Forms 5.0.0.1874 or upper

### Avalonia

* .NET 6.0, 5.0 (`net6.0-windows`, `net5.0-windows`)
* .NET Core 3.1, 3.0, (`netcoreapp3.1`, `netcoreapp3.0`)
* .NET Core 2.2, 2.1, 2.0 (`netcoreapp2.2`, `netcoreapp2.1`, `netcoreapp2.0`)
* .NET Framework 4.8, 4.6.2 (`net48`, `net462`)
* Avalonia 0.10.0 or upper

----

## Available properties

|Name|Detail|
|:----|:----|
|`Source`|SkiaSharp image related objects. See listed below.|
|`Stretch`|[Stretch enum value](https://docs.microsoft.com/en-us/dotnet/api/system.windows.media.stretch?view=windowsdesktop-6.0)|
|`StretchDirection`|[StretchDirection enum value](https://docs.microsoft.com/en-us/dotnet/api/system.windows.controls.stretchdirection?view=windowsdesktop-6.0)|
|`RenderMode`|Rendering into back buffer by synchronous or asynchronous.|

### Source property

The `Source` property accepts the following SkiaSharp types:

|Supported Type|Aspect ratio from|Note|
|:----|:----|:----|
|`SKBitmap`|Origin| |
|`SKImage`|Origin| |
|`SKPicture`|Measured `RenderSize`| |
|`SKDrawable`|Measured `RenderSize`| |
|`SKSurface`|Measured `RenderSize`| |
|`string`|Origin|URL string for downloading content|
|`Uri`|Origin|URL for downloading content|

Some types are drawn with aspect ratio corresponding to the current measured `RenderSize` area.
Therefore, to maintain the aspect ratio, the size must be explicitly controlled in XAML.

Note: If you specify a URL to display, the URL does NOT accept the WPF resource format.
(`application:` and `pack:` protocol based.)

### RenderMode property

Choose rendering into back buffer by synchronous or asynchronous:

|RenderMode|Note|
|:----|:----|
|`Synchronously`|All rendering process is synchronously.|
|`AsynchronouslyForFetching`|Defaulted, Will operate asynchronously when giving URL in `Source` property (`string` or `Uri`).|
|`Asynchronously`|All rendering process is asynchronously.|

`AsynchronouslyForFetching` is defaulted.
Because, when set to `Asynchronously`, all instances given to `Source` must not be implicitly modified.
Maybe, this constraint can be difficult to achieve on your project.

----

## License

Apache-v2.

----

## History

* 1.3.0:
  * Supported Avalonia platform (>= 0.10.0).
  * Downgraded Xamarin Forms package version (>= 5.0.0.1874).
* 1.2.0:
  * Fixed misconfigured bitfield of RGBA on Xamarin Forms.
  * Added ProjectionQuality property for Xamarin Forms (You can adjust final image quality when need to make better performance.)
* 1.1.0:
  * Supported Xamarin Forms.
* 1.0.1:
  * Downgraded SkiaSharp to 2.80.0 (Because known bug related.)
* 1.0.0:
  * Reached 1.0.0 🎉
  * Fixed updating new image instance.
* 0.4.0:
  * Added RenderMode features and supported StretchDirection.
  * Added sample code.
* 0.3.0:
  * Fixed XAML namespace.
* 0.2.0:
  * Fixed some problems, add WIP feature.
* 0.1.0:
  * Initial release.
