# <img src="/src/icon.png" height="30px"> Verify.ImageMagick

[![Build status](https://ci.appveyor.com/api/projects/status/ersj3ag6pitygha5?svg=true)](https://ci.appveyor.com/project/SimonCropp/Verify-ImageMagick)
[![NuGet Status](https://img.shields.io/nuget/v/Verify.ImageMagick.svg)](https://www.nuget.org/packages/Verify.ImageMagick/)

Extends [Verify](https://github.com/VerifyTests/Verify) to allow verification of documents via [Magick.NET](https://github.com/dlemstra/Magick.NET).

Converts documents pdfs to png for verification.

Contains [comparers](https://github.com/VerifyTests/Verify/blob/master/docs/comparer.md) for png, jpg, bmp, and tiff.



## NuGet package

https://nuget.org/packages/Verify.ImageMagick/


## Usage

<!-- snippet: enable -->
<a id='snippet-enable'></a>
```cs
[ModuleInitializer]
public static void Init()
{
    VerifyImageMagick.Initialize();
    VerifyImageMagick.RegisterComparers(0.05);
}
```
<sup><a href='/src/Tests/ModuleInitializer.cs#L3-L12' title='Snippet source file'>snippet source</a> | <a href='#snippet-enable' title='Start of snippet'>anchor</a></sup>
<!-- endSnippet -->

`Initialize` registers the pdf to png converter and all comparers.


### PDF converter

To register only the pdf to png converter:

```
VerifyImageMagick.RegisterPdfToPngConverter();
```


#### Verify a file

<!-- snippet: VerifyPdf -->
<a id='snippet-verifypdf'></a>
```cs
[Test]
public Task VerifyPdf() =>
    VerifyFile("sample.pdf");
```
<sup><a href='/src/Tests/Samples.cs#L12-L18' title='Snippet source file'>snippet source</a> | <a href='#snippet-verifypdf' title='Start of snippet'>anchor</a></sup>
<!-- endSnippet -->


#### Verify a Stream

<!-- snippet: VerifyPdfStream -->
<a id='snippet-verifypdfstream'></a>
```cs
[Test]
public Task VerifyPdfStream()
{
    var stream = new MemoryStream(File.ReadAllBytes("sample.pdf"));
    return Verify(stream, "pdf");
}
```
<sup><a href='/src/Tests/Samples.cs#L20-L29' title='Snippet source file'>snippet source</a> | <a href='#snippet-verifypdfstream' title='Start of snippet'>anchor</a></sup>
<!-- endSnippet -->


#### Result

[Samples.VerifyPdf#00.verified.png](/src/Tests/Samples.VerifyPdf#00.verified.png):

<img src="/src/Tests/Samples.VerifyPdf%2300.verified.png" width="200px">


### Image Comparers

The following will use ImageMagick to compare the images instead of the default binary comparison.

<!-- snippet: CompareImage -->
<a id='snippet-compareimage'></a>
```cs
[Test]
public Task CompareImage() =>
    VerifyFile("sample.jpg");
```
<sup><a href='/src/Tests/Samples.cs#L4-L10' title='Snippet source file'>snippet source</a> | <a href='#snippet-compareimage' title='Start of snippet'>anchor</a></sup>
<!-- endSnippet -->


### Register all comparers

All comparers can be regietered:

```
VerifyImageMagick.RegisterComparers();
```


## Icon

[Swirl](https://thenounproject.com/term/wizard/2744075/) designed by [Philipp Petzka](https://thenounproject.com/masteroficon) from [The Noun Project](https://thenounproject.com/).
