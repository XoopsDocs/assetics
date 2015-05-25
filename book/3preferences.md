# 3.0 The Functions

XOOPS has historically provided two methods in the XoopsTheme class to deal with assets:

```
addScript($url)

addStylesheet($url)
```

Note that these methods expect URLs, not filesystem paths.

**New Assets Functions**

The XoopsTheme class has been expanded to better manage assets. The following methods are available:

```
addScriptAssets($assets, $filters)
addStylesheetAssets($assets, $filters)
addBaseScriptAssets($assets)
addBaseStylesheetAssets($assets)
setNamedAsset($name, $assets, $filters)
```

Let's review now these functinos individually:

**addScriptAssets & addStylesheetAssets**

Accept an array of one or more asset file  specifications
Optionally accept a string of comma separated filter names
Result in combining and filtering the assets, then adding the URL for the created static asset file to the same lists used by **addScript()** and **addStylesheet()**

**addBaseScriptAssets & addBaseStylesheetAssets**

Accept an array of one or more asset file  specifications

Accumulate asset files in separate lists, similar to addScript() and addStylesheet()

Assets are processed using default filters and the resulting static file URL is added to the top of respective list in the page headers:
```
<{$xoops_module_header}>
```

**Base Assets**

XOOPS Core uses the base assets for common system wide assets, such as jQuery, jQueryUI, locale and Bootstrap assets

Themes can add to the base assets using theme_onload.php

Modules may want to add their common assets to the base asset

Browser cache use is improved if the same base asset definition is used for many pages

**setNamedAsset**

Accepts a unique asset name
Accepts an array of one or more asset file  specifications
Optionally accepts a string of comma separated filter names
Results in creating an asset **reference** that can be specified in asset arrays in place of a file specification

**Name Assets**

Named assets allow symbolic reference to commonly used assets (i.e. “jquery”)
Named assets can be given additional filters

Using setNamedAsset does not create the asset, it just records the name and definition

To use an asset named “jquery” include an asset name of “@jquery” in an asset list

#### Smarty Assets Tag

The Smarty block plugin allows assets to be defined in templates. Full syntax:

![logoModule.png](assets/logoModule.png)

