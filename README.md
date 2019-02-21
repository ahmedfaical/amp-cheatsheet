# AMP Cheatsheet
Simple and brief instructions for implementing AMP to any projet


## Important ‼
#### Define AMP page location on Desktop or No-AMP page
    <link rel="amphtml" href="http://example.com/amp" />
#### Link back to Desktop or No-AMP page from AMP
    <link rel="canonical" href="http://example.com" />
#### Keep in mind!
- Don't use !important CSS
- Sized images
- Minify HTML and CSS
- https:// highly recommended
- No custom .JS files
- Only 50Kb inline style allowed in <style amp-custom> </style>
#### Common attributes
fallback, heights, layout, media, noloading, on, placeholder, sizes, width and height
#### Validate AMP Pages
Simply add #development=1 to an AMP URL. Validation errors will be printed in the Javascript console.


## Images
    <amp-img src="/m/picture.jpg" alt="Cheat Sheet" layout="responsive" height="200" width="300"></amp-img>
#### Responsiveness
    <amp-img src="/narrow.jpg srcset="/wide.jpg 640w, /narrow.jpg 320w" width="1200" height="800" layout="responsive" alt="demo image"></amp-img>
#### Layout types
- nodisplay – works like display: none style.
- fixed – fixed width & height
- responsive – fills container automatically to aspect ratio
- fixed-height – keeps the specified height unchanged
- fill – fills available height & width
- container – lets its children define its size, like a normal div
- flex-item – works like display:flex style
- intrinsic – responsive until it reaches its height and width
#### CSS media queries
    @media screen and (max-width: 720px) {
      p { font-size: 0.9em; }
    }
#### Element media queries:
    <amp-img
      media="(min-width: 720px)"
      src="demo.jpg"
      width=300
      height=200
      layout="responsive">
    </amp-img>
#### Allowed rules
@font-face, @keyframes, @media, @page, @supports.
#### Placeholder
Shows a placeholder while the element is being loaded:
    <amp-anim src="animation.gif"
       layout="responsive"
       width="300"
       height="200">
       <amp-img placeholder
          src="demo.jpg"
          layout="fill">
       </amp-img>
    </amp-anim>


## Allowed & Disallowed HTML Tags
**script :** Prohibited unless the type is application/ld+json or text/plain. (Other non-executable values may be added as needed.)

**noscript :** Allowed. Can be used anywhere in the document.

**base :** Prohibited.

**img :** Replaced with amp-img.
Please note: <img> is a Void Element according to HTML5, so it does not have an end tag. However, <amp-img> does have an end tag </amp-img>.

**video :** Replaced with amp-video.

**audio :** Replaced with amp-audio.

**iframe :**	Replaced with amp-iframe.

**frame, frameset, object, param, applet, embed :** Prohibited.

**Attribute names starting with on such as onclick, onmouseover :** Disallowed

**form :**	Allowed. Require including amp-form extension.

**input elements :**	Mostly allowed with exception of some input types, namely, **<input[type=image]>**, **<input[type=button]>**, **<input[type=password]>**, **<input[type=file]>** are invalid. Related tags are also allowed: **fieldset** and **label**

**button :** Allowed.

**style :** Required style tag for amp-boilerplate. One additional style tag is allowed and must have the attribute amp-custom. 🔗

**link :** rel values registered on microformats.org are allowed. If a rel value is missing from our white list, please submit an issue. stylesheet and other values like preconnect, prerender and prefetch that have side effects in the browser are disallowed. There is a special case for fetching stylesheets from white listed font providers.

**meta :** The http-equiv attribute may be used for specific allowable values; see the AMP validator specification for details.

**a :**	The href attribute value must not begin with javascript: (javascript: schema is disallowed.). If set, the target attribute value must be _blank. Otherwise allowed. 🔗

**Calsses and IDs prefixed with -amp- and i-amp- :** Disallowed

**svg :** Most SVG elements are allowed.
  
  
## AMP and CSS
#### Keyframes stylesheet
In addition to the **<style amp-custom>**, authors may also add the **<style amp-keyframes>** tag, which is allowed specifically for keyframes animations.
- May only be placed as the last child of the document's <body> element.
- May only contain @keyframes, @media, @supports rules and their combination.
- May not be larger than 500,000 bytes.

#### Custom fonts
    <link rel="stylesheet" href="https://fonts.googleapis.com/css?family=Tangerine">


#### Input mode classes
- amp-mode-touch: This class is set when AMP detects touch input.
- amp-mode-mouse: This class is set when AMP detects mouse input.
- amp-mode-keyboard-active: This class is set when AMP detects that the keyboard is active.

## Google Analytics
Include <script async custom-element="amp-analytics" src="https://cdn.ampproject.org/v0/amp-analytics-0.1.js"></script>
    <amp-analytics type="googleanalytics">
    <script type="application/json">
    {
      "vars": {
        "account": "UA-XXXXXXXX-1"
      },
      "triggers": {
        "trackPageview": {
        "on": "visible",
        "request": "pageview"
        }
      }
    }
    </script>
  
## Actions, events
#### Syntax
    eventName:targetId[.methodName[(arg1=value, arg2=value)]]
#### Example
    on="submit-success:lightbox1;submit-error:lightbox2"
    <div id="cookie-consent">The site is using Cookies!</div>
    <button on="tap:cookie-consent.hide">OK, I understand!</button>
#### Events
- **show, hide** – shows/hides the target element
- **toggleVisibility, toggleClass**
- **scrollTo(duration=INTEGER, position=STRING)**
- **focus** – make the target element gain focus
- **open** – opens the amp-image-lightbox with the source image being the one that triggered the action
- **close** – closes the lightbox
- **change** – on input & select
- **input-debounced** – 300ms passed since an input value change
- i**nput-throttled** – change event fired maximum once every 100ms
- **tap** – click or tap
- **slideChange** – amp-carousel[type="slides"]
- **toggleAutoplay** – amp-carousel[type="slides"]
- **goToSlide(index=INTEGER)** – advance the carousel to the index
- **lightboxOpen** – amp-lightbox fully visible
- **lightboxClose** – amp-lightbox fully closed
- **sidebarOpen** – amp-sidebar fully open
- **sidebarClose** – amp-sidebar fully closed
- **play, pause, mute, unmute, fullscreen** – video controls
- **firstPlay** – first user interaction with video
- **timeUpdate** – video playing position changed
- **submit** – form is submitted
- **clear** – clears values in the inputs
- **submit-error** – form submission response is an error
- **play, pause** – controls amp-audio
- **refresh** – refreshes data from the src and re-renders the amp-list
- **selectUp(delta=INTEGER), selectDown(delta)** – moves the amp-selector up/down by a value
- **open, close, toggle** – amp-sidebar controls
- **navigateTo(url)**
- **goBack** – go back in history
- **print** – Opens the Print Dialog


