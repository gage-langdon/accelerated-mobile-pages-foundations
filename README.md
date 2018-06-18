# AMPle Introduction

## Run server

We first need to run a local server at the root of our app to serve our pages.

### If Python version returned above is 3.X

`python -m http.server`

### If Python version returned above is 2.X

`python -m SimpleHTTPServer`

## Open browser

http://localhost:8000/article.html

## Create our test page

Copy contents of `article.html` into a new file named `article.amp.html`. Once completed, navigate to [localhost:8000/article.amp.html](localhost:8000/article.amp.html)

## Add import script tag for AMP library to bottom of HEAD

`async`

```html
<script async src="https://cdn.ampproject.org/v0.js"></script>
```

## Move page into 'development' mode

Append `#development=1` to any valid AMP page and open your Chrome DevTools.

## Add charset meta tag to top of HEAD

This is a requirement by AMP to avoid reinterpreting content that was before this tag.

```html
<meta charset="utf-8" />
```

## Add `link="canonical"`

This points towards our non-amp version and is required by AMP. If decide to use AMP for desktop as well then you can have this point to itself.

```html
<link rel="canonical" href="/article.html">
```

## Add viewport meta tag

This allow our width to change with the viewport size and is a common tag for responsive sites.

```html
<meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
```

## Remove any inline 3rd party Javascript

Currently we have only one script tag that is invalid. Remove the script tag below from our HTML.

```html
<script type="text/javascript" src="base.js"></script>
```

## Add required AMP Boilerplate CSS

Every AMP page is required to ship with minified boilerplate CSS. This is defined inline styling and must not be any other format than minified. This CSS initially hides the content of the page until the AMP library is loaded. Add the following HTML at the bottom of our HEAD tag.

```html
<style amp-boilerplate>body{-webkit-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-moz-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-ms-animation:-amp-start 8s steps(1,end) 0s 1 normal both;animation:-amp-start 8s steps(1,end) 0s 1 normal both}@-webkit-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-moz-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-ms-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-o-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}</style><noscript><style amp-boilerplate>body{-webkit-animation:none;-moz-animation:none;-ms-animation:none;animation:none}</style></noscript>
```

## Change our `<img/>` to an AMP Web Component

Regular ```<img/>``` tags are not performant so AMP has implemented their own.

```html
<amp-img src="mountains.jpg" layout="responsive" width="266" height="150"></amp-img>
```

![html-layout](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "")
