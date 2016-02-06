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
