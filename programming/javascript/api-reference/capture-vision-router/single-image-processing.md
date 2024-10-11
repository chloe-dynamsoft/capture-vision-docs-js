---
layout: default-layout
title: CaptureVisionRouter Single Process - Dynamsoft Capture Vision JavaScript Edition API
description: This page introduces APIs related to Single Process with Dynamsoft Capture Vision JavaScript Edition.
keywords: capture vision, caputre, image processing, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
breadcrumbText: CVR JavaScript CaptureVisionRouter
---

# CaptureVisionRouter Single Image Processing

| Name                  | Description                                                                                   |
| --------------------- | --------------------------------------------------------------------------------------------- |
| [capture()](#capture) | Processes a single image or a file containing a single image to derive important information. |

## capture

Processes a single image or a file containing a single image to derive important information.

**Syntax**

```typescript
capture(imageOrFile: Blob | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement | DSImageData | string, templateName?: string): Promise<CapturedResult>;
```

**Parameters**

`imageOrFile`: specifies the image or file to be processed. The following data types are accepted: `Blob`, `HTMLImageElement`, `HTMLCanvasElement`, `HTMLVideoElement`, `DSImageData`, `string`.

`templateName`: specifies a "CaptureVisionTemplate" to use. If not specified, the preset template named 'Default' will be used.

There are two types of CaptureVisionTemplates: the [preset ones](./preset-templates.md) which come with the SDK and the custom ones that get initialized when the user calls [initSettings](./settings.md#initsettings). 

Please be aware that the [preset CaptureVisionTemplates](./preset-templates.md) will be overwritten should the user calls [initSettings](./settings.md#initsettings) and pass his own settings.

**Return value**

A promise that resolves with a [CapturedResult]({{ site.dcv_js_api }}core/basic-structures/captured-result.html) object which contains the derived information from the image processed.

**Code snippet**

```javascript
let router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let results = await router.capture("blob:https://demo.dynamsoft.com/afb84bd2-e8cb-4b96-92b6-36dc89783692", "ReadSingleBarcode");
let count = results.items.length;
for(let i = 0; i < count; i++) {
    //...
}
```
