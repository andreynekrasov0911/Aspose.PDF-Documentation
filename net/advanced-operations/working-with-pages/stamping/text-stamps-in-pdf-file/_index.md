---
title:  Text stamps in the PDF File
type: docs
weight: 20
url: /net/text-stamps-in-the-pdf-file/
---
# Text stamps in the PDF File

## Adding Text Stamp
You can use TextStamp class to add a text stamp in a PDF file. TextStamp class provides properties necessary to create a text based stamp like font size, font style, and font color etc. In order to add text stamp, you need to create a Document object and a TextStamp object using required properties. After that, you can call AddStamp method of the Page to add the stamp in the PDF. The following code snippet shows you how to add text stamp in the PDF file.
```
// For complete examples and data files, please go to https://github.com/aspose-pdf/Aspose.PDF-for-.NET
// The path to the documents directory.
string dataDir = RunExamples.GetDataDir_AsposePdf_StampsWatermarks();

// Open document
Document pdfDocument = new Document(dataDir+ "AddTextStamp.pdf");

// Create text stamp
TextStamp textStamp = new TextStamp("Sample Stamp");
// Set whether stamp is background
textStamp.Background = true;
// Set origin
textStamp.XIndent = 100;
textStamp.YIndent = 100;
// Rotate stamp
textStamp.Rotate = Rotation.on90;
// Set text properties
textStamp.TextState.Font = FontRepository.FindFont("Arial");
textStamp.TextState.FontSize = 14.0F;
textStamp.TextState.FontStyle = FontStyles.Bold;
textStamp.TextState.FontStyle = FontStyles.Italic;
textStamp.TextState.ForegroundColor = Aspose.Pdf.Color.FromRgb(System.Drawing.Color.Aqua);
// Add stamp to particular page
pdfDocument.Pages[1].AddStamp(textStamp);

dataDir = dataDir + "AddTextStamp_out.pdf";
// Save output document
pdfDocument.Save(dataDir);
```
## Define alignment for TextStamp object
Adding watermarks to PDF documents is one of the frequent demanded features and Aspose.PDF for .NET is fully capable of adding Image as well as Text watermarks. We have a class named [TextStamp](https://apireference.aspose.com/pdf/net/aspose.pdf/textstamp) which provides the feature to add text stamps over the PDF file. Recently there has been a requirement to support the feature to specify the alignment of text when using TextStamp object. So in order to fulfill this requirement, we have introduced TextAlignment property in TextStamp class. Using this property, we can specify the Horizontal text alignment.

The following code snippets shows an example on how to load an existing PDF document and add TextStamp over it.
```
// For complete examples and data files, please go to https://github.com/aspose-pdf/Aspose.PDF-for-.NET
// The path to the documents directory.
string dataDir = RunExamples.GetDataDir_AsposePdf_StampsWatermarks();

// Instantiate Document object with input file
Document doc = new Document(dataDir+ "DefineAlignment.pdf");
// Instantiate FormattedText object with sample string
FormattedText text = new FormattedText("This");
// Add new text line to FormattedText
text.AddNewLineText("is sample");
text.AddNewLineText("Center Aligned");
text.AddNewLineText("TextStamp");
text.AddNewLineText("Object");
// Create TextStamp object using FormattedText
TextStamp stamp = new TextStamp(text);
// Specify the Horizontal Alignment of text stamp as Center aligned
stamp.HorizontalAlignment = HorizontalAlignment.Center;
// Specify the Vertical Alignment of text stamp as Center aligned
stamp.VerticalAlignment = VerticalAlignment.Center;
// Specify the Text Horizontal Alignment of TextStamp as Center aligned
stamp.TextAlignment = HorizontalAlignment.Center;
// Set top margin for stamp object
stamp.TopMargin = 20;
// Add the stamp object over first page of document
doc.Pages[1].AddStamp(stamp);

dataDir = dataDir + "StampedPDF_out.pdf";
// Save the udpated document
doc.Save(dataDir);
```
## Fill Stroke Text as Stamp in PDF File
We have implemented setting of rendering mode for text adding and editing scenarios. To render stroke text please create TextState object and set RenderingMode to TextRenderingMode.StrokeText and also select color for StrokingColor property. Later, bind TextState to the stamp using BindTextState() method.

Following code snippet demonstrates adding Fill Stroke Text:
```
// For complete examples and data files, please go to https://github.com/aspose-pdf/Aspose.PDF-for-.NET
// The path to the documents directory.
string dataDir = RunExamples.GetDataDir_AsposePdf_StampsWatermarks();
// Create TextState object to transfer advanced properties
TextState ts = new TextState();
// Set color for stroke
ts.StrokingColor = Color.Gray;
// Set text rendering mode
ts.RenderingMode = TextRenderingMode.StrokeText;
// Load an input PDF document
Facades.PdfFileStamp fileStamp = new Facades.PdfFileStamp(new Aspose.Pdf.Document(dataDir + "input.pdf"));

Aspose.Pdf.Facades.Stamp stamp = new Aspose.Pdf.Facades.Stamp();
stamp.BindLogo(new Facades.FormattedText("PAID IN FULL", System.Drawing.Color.Gray, "Arial", Facades.EncodingType.Winansi, true, 78));

// Bind TextState
stamp.BindTextState(ts);
// Set X,Y origin
stamp.SetOrigin(100, 100);
stamp.Opacity = 5;
stamp.BlendingSpace = Facades.BlendingColorSpace.DeviceRGB;
stamp.Rotation = 45.0F;
stamp.IsBackground = false;
// Add Stamp
fileStamp.AddStamp(stamp);
fileStamp.Save(dataDir + "ouput_out.pdf");
fileStamp.Close();
```
