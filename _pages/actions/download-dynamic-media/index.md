---
layout: component-page
title: Download Modal (Dynamic Media)
component-group: modals
initial-version: 1.5.0

---

> For this component to work, AEM **must** be started with Dynamic Media enabled. All Image Presets used via this action must be published to AEM Publish.

Displays the modal used to download one or more assets for use when AEM Assets Dynamic Media is enabled.

* The left portion of the modal displays the list (one or more) assets that will be downloaded as part of this operation.
    * Multiple assets can be downloaded via the [Cart](../cart/). 
* The original assets is included in the download zip via the **Exclude Original Assets from ZIP File** dialog configuration.
* Users can select to include up to one Dynamic Media rendition (defined via Image Presets).
* Users can select to include all renditions.
* Users can select to include all (any) sub-assets.

The resulting download is a zip file (the zip file name can be authored via the dialog).

## Authoring

The Download Modal is authored by opening up the download action page (of Action Template type) via AEM's Site admin. 

*Each download page should have exactly one Download Modal component.*

This Download Modal action page must referenced from the [Search page's Page Properties](../search/#page-properties). 

The modal displays the placeholder image when being authored.

### Dialog / Labels

#### Modal Title

The modal's title.

#### Asset List Title

The title text to display above the list of assets to download.

#### Download Form Title

The title text to display above the download option check-boxes.

#### Image Presets Drop-down Text

The text to display in the Image Presets dropdown when no Image Preset has been selected.

#### Cancel Button Label

The text for the button that closes the modal.

#### Download Button Label

The text for the button that lets users download the assets.

### Dialog / File

#### Exclude Original Assets from ZIP File
 
Check to exclude original assets from the downloaded zip file. This applies for all uses of this Download modal.

#### ZIP File Name
 
The name of the zip file to download.

#### Allow Download of Static Renditions

Select to allow the downloading of any static renditions auto-generated by AEM. If left unchecked, the option to download static renditions will not be displayed.

#### Image Presets

Select the image presets to be shown to the user.


## Technical details

* **Component**: `/apps/asset-share-commons/components/modals/download-dynamic-media`
* **Sling Model**: `com.adobe.aem.commons.assetshare.components.actions.dmdownload.DynamicMediaDownload`

The download functionality leverages AEM Assets `assetdownload.zip` servlet. To ensure this servlet is
available, the following request path must be open (ie. not blocked via AEM Dispatcher filters).

    HTTP POST /content/dam.assetdownload.zip/<ZIP File Name>.zip?licenseCheck=true&flatStructure=true&downloadSubassets=<true|false>&downloadRenditions=<true|false>&s7exportsettings=...