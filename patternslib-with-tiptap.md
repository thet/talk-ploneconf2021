<!-- .slide: data-background="lime" -->
# $ whoami


<!-- .slide: data-background="lime" -->
- Johannes Raggam
- Graz / Austria


<!-- .slide: data-background="lime" -->
<img alt="Syslab Logo" title="Syslab.com" style="width: 60%; height: auto" src="./resources/logos/Logo_SYSLAB_ohneClaim_white_1c.svg" />


<!-- .slide: data-background="lime" -->
- Plone Foundation Member
- Former Plone Framework Team Member
- BlueDynamics Alliance Member
- Buschenschanksprint Organizer


<!-- .slide: data-background="lime" -->
- https://github.com/thet
- https://twitter.com/thetetet


<!-- .slide: data-background="lime" -->
- https://thet.github.io/talk-ploneconf2021
- https://github.com/thet/talk-ploneconf2021




<!-- .slide: data-background="yellow" -->
# Overview


<!-- .slide: data-background="yellow" -->

- For Designers <!-- .element: class="fragment" -->

- For Integrators <!-- .element: class="fragment" -->

- For Developers <!-- .element: class="fragment" -->


<!-- .slide: data-background="yellow" -->

- About Patternslib <!-- .element: class="fragment" -->
- The tiptap editor <!-- .element: class="fragment" -->
- pat-tiptap Patternslib pattern <!-- .element: class="fragment" -->
- <span>How to get this into Plone?<br><small>Webpack module federation</small></span> <!-- .element: class="fragment" -->




<!-- .slide: data-background="Cyan" -->
# What is the Patternslib?


<!-- .slide: data-background="Cyan" -->

> Patternslib is a library of reusable patterns which let you create rich, dynamic and interactive prototypes or websites, without having to know or care about Javascript.

https://patternslib.com/documentation/what-is-patternslib <!-- .element: class="caption" -->


<!-- .slide: data-background="Cyan" -->
- Library for user interaction patterns
- Concept by Cornelis Kolbach
- Since 2011, first concepts since 2005


<!-- .slide: data-background="Cyan" -->
## Download
https://patternslib.com/download


<!-- .slide: data-background="Cyan" -->
## Integrate
```html
<script
    src="./patternslib/bundle.min.js">
</script>
```


<!-- .slide: data-background="Cyan" -->
## Use
```html
<input
    type="date"
    class="pat-date-picker"
    />
```


<!-- .slide: data-background="Cyan" class="full" -->
## System Overview
<img alt="Patternslib System Overview" style="width: 60%; height: auto" src="./resources/patternslib-system-overview.svg" />


<!-- .slide: data-background="Cyan" -->
## Benefits


<!-- .slide: data-background="Cyan" -->
- Designed for Non-JavaScript People <!-- .element: class="fragment" -->
- Semantic HTML <!-- .element: class="fragment" -->
- Developer friendly <!-- .element: class="fragment" -->
- Easy way to initialize JavaScript and to pass Options <!-- .element: class="fragment" -->
- Reinitializes JavaScript when needed <!-- .element: class="fragment" -->


<!-- .slide: data-background="Cyan" -->
- Mockup uses the Patternslib.


<!-- .slide: data-background="Cyan" -->
## Patternslib showcase


<!-- .slide: data-background="Cyan" class="full" -->
<iframe src="https://patternslib.com/demos"></iframe>


<!-- .slide: data-background="Cyan" class="full" -->
<iframe src="https://quaive.cornelis.amsterdam"></iframe>


<!-- .slide: data-background="Cyan" class="full" -->
<iframe src="https://oira.cornelis.amsterdam"></iframe>




<!-- .slide: data-background="Blue" -->
# The tiptap editor


<!-- .slide: data-background="Blue" -->
- A modern text editor <!-- .element: class="fragment" -->
- Headless, no default UI <!-- .element: class="fragment" -->
- HTML, Markdown, whatever. <!-- .element: class="fragment" -->
- Based on Prosemirror <!-- .element: class="fragment" -->
- Strict data model <!-- .element: class="fragment" -->
- Awesome features (Collaboration, Mentions, Checkboxes, ...) <!-- .element: class="fragment" -->


<!-- .slide: data-background="Blue" -->
- https://tiptap.dev/


<!-- .slide: data-background="Blue" -->
## Patternslib integration
- https://github.com/Patternslib/pat-tiptap/pull/2


<!-- .slide: data-background="Blue" -->
http://localhost:3010/src/


<!-- .slide: data-background="Blue" -->
https://quaive.cornelis.amsterdam/workspaces/asian-steering-committee/minutes/minutes-of-2014-06-09




<!-- .slide: data-background="Blue" -->
# Building a UI around tiptap

A Patternslib tutorial




<!-- .slide: data-background="Blue" -->
```html
<textarea
    name="text"
    class="pat-tiptap">
  <h1>hello</h1>
  <p>I am some text content</p>
</textarea>
```




<!-- .slide: data-background="Blue" -->
## Add a toolbar


<!-- .slide: data-background="Blue" -->
```html
<div id="tiptap-external-toolbar">
  <button type="button" class="button-heading-level-1">H1</button>
  <button type="button" class="button-heading-level-2">H2</button>
  <button type="button" class="button-paragraph">Paragraph</button>
  <button type="button" class="button-bold">Bold</button>
  <button type="button" class="button-italic">Italic</button>
</div>
```

```html [4-5]
<textarea
    name="text"
    class="pat-tiptap"
    data-pat-tiptap="
        toolbar-external: #tiptap-external-toolbar
    ">
</textarea>
```




<!-- .slide: data-background="Blue" -->
## Add a link overlay


<!-- .slide: data-background="Blue" -->
```html[|3-6]
<div id="tiptap-external-toolbar">
  <!-- other buttons -->
  <a
      href="#modal-link"
      class="button-link pat-modal"
      >Link</a>
</div>
```


<!-- .slide: data-background="Blue" -->
```html [|2,5,9,14,17,19]
<template
    id="modal-link"
    hidden>
  <form
      class="link-panel">
    <label>Link URL:
      <input
          type="text"
          name="tiptap-href" />
    </label>
    <label>Link Text:
      <input
          type="text"
          name="tiptap-text" />
    </label>
    <button
        class="close-panel"
        type="button"
        name="tiptap-confirm"
      >submit</button>
  </form>
</template>
```


<!-- .slide: data-background="Blue" -->
```html[|6]
<textarea
    name="text"
    class="pat-tiptap"
    data-pat-tiptap="
        toolbar-external: #tiptap-external-toolbar;
        link-panel: #pat-modal .link-panel;
    ">
```




<!-- .slide: data-background="Blue" -->
## Add a link context menu


<!-- .slide: data-background="Blue" -->
```html [|2,4,6,12,16]
<template
    id="context-menu-link">
  <nav
      class="tiptap-link-context-menu">
    <a
      class="close-panel tiptap-open-new-link"
      target="_blank"
      href=""
    >Visit</a>
    <button
      type="button"
      class="close-panel tiptap-edit-link"
    >Edit link</button>
    <button
      type="button"
      class="close-panel tiptap-unlink"
    >Unlink</button>
  </nav>
</template>
```


<!-- .slide: data-background="Blue" -->
```html[|7]
<textarea
    name="text"
    class="pat-tiptap"
    data-pat-tiptap="
        toolbar-external: #tiptap-external-toolbar;
        link-panel: #pat-modal .link-panel;
        context-menu-link: #context-menu-link;
    ">
```




<!-- .slide: data-background="Blue" -->
## Add a image overlay


<!-- .slide: data-background="Blue" -->
```html
<a
    class="button-image pat-modal"
    href="#modal-image">Image</a>
```


<!-- .slide: data-background="Blue" -->
```html [|6-8,11-13]
<template id="modal-image">
  <h2>Add Image</h2>
  <div>
    <nav>
      <a
          href="#image-panel-external"
          class="pat-inject"
          data-pat-inject="target: .image-panel"
      >External</a>
      <a
          href="#image-panel-selection"
          class="pat-inject"
          data-pat-inject="target: .image-panel"
      >Selection</a>
    </nav>

    <div class="image-panel">
    </div>

    <button class="close-panel" type="button" name="tiptap-confirm">submit</button>
    <button class="close-panel" type="button">cancel</button>
  </div>
</template>
```


<!-- .slide: data-background="Blue" -->
```html [|1,6,10,14]
<template id="image-panel-external">
  <h3>External Image</h3>
  <form>
    <label>
      Image URL:
      <input type="text" name="tiptap-src"/>
    </label>
    <label>
      Title:
      <input type="text" name="tiptap-title"/>
    </label>
    <label>
      Alternative text:
      <input type="text" name="tiptap-alt"/>
    </label>
  </form>
</template>
```


<!-- .slide: data-background="Blue" -->
```html [|8,9,15,16]
<template id="image-panel-selection">
  <h3>Image Selection</h3>
  <form>
    <label>
      <img src="PREVIEW-URL" />
      <input
          type="radio"
          name="tiptap-src"
          value="IMAGE-URL" />
    </label>
    <label>
      <img src="PREVIEW-URL" />
      <input
          type="radio"
          name="tiptap-src"
          value="IMAGE-URL" />
    </label>
  </form>
</template>
```


<!-- .slide: data-background="Blue" -->
```html [|8]
<textarea
    name="text"
    class="pat-tiptap"
    data-pat-tiptap="
        toolbar-external: #tiptap-external-toolbar;
        link-panel: #pat-modal .link-panel;
        context-menu-link: #context-menu-link;
        image-panel: #pat-modal .image-panel;
    ">
```




<!-- .slide: data-background="Blue" -->
## Small improvements to the image overlay


<!-- .slide: data-background="Blue" -->
```html [13]
<template id="modal-image">
  <h2>Add Image</h2>
  <div>
    <nav>
      <a
          href="#image-panel-external"
          class="pat-inject"
          data-pat-inject="target: .image-panel"
      >External</a>
      <a
          href="#image-panel-selection"
          class="pat-inject"
          data-pat-inject="target: .image-panel; trigger: autoload"
      >Selection</a>
    </nav>

    <div class="image-panel">
    </div>

    <button class="close-panel" type="button" name="tiptap-confirm">submit</button>
    <button class="close-panel" type="button">cancel</button>
  </div>
</template>
```


<!-- .slide: data-background="Blue" -->
```html [|10,11,20,21]
<template id="image-panel-selection">
  <h3>Image Selection</h3>
  <form>
    <label>
      <img src="PREVIEW-URL" />
      <input
          type="radio"
          name="tiptap-src"
          value="IMAGE-URL"
          class="pat-forward"
          data-pat-forward="selector: button[name=tiptap-confirm]"
          />
    </label>
    <label>
      <img src="PREVIEW-URL" />
      <input
          type="radio"
          name="tiptap-src"
          value="IMAGE-URL"
          class="pat-forward"
          data-pat-forward="selector: button[name=tiptap-confirm]"
          />
    </label>
  </form>
</template>
```




<!-- .slide: data-background="Blue" -->
## Adding a source overlay


<!-- .slide: data-background="Blue" -->
```html
      <a
          class="button-source pat-modal"
          href="#modal-source">Source</a>
```


<!-- .slide: data-background="Blue" -->
```html[|1,3,6]
<template id="modal-source">
  <h1>Edit Source</h1>
  <form class="source-panel">
    <label>
      Source:
      <textarea name="tiptap-source"></textarea>
    </label>
    <button class="close-panel" type="button" name="tiptap-confirm">submit</button>
    <button class="close-panel" type="button">cancel</button>
  </form>
</template>
```


<!-- .slide: data-background="Blue" -->
```html[9]
<textarea
    name="text"
    class="pat-tiptap"
    data-pat-tiptap="
        toolbar-external: #tiptap-external-toolbar;
        link-panel: #pat-modal .link-panel;
        context-menu-link: #context-menu-link;
        image-panel: #pat-modal .image-panel;
        source-panel: #pat-modal .source-panel;
    ">
```




<!-- .slide: data-background="Blue" -->
## Add mentions and tags context menus


<!-- .slide: data-background="Blue" -->
```html[10-13]
<textarea
  name="text"
  class="pat-tiptap"
  data-pat-tiptap="
      toolbar-external: #tiptap-external-toolbar;
      link-panel: #pat-modal .link-panel;
      context-menu-link: #context-menu-link;
      image-panel: #pat-modal .image-panel;
      source-panel: #pat-modal .source-panel;
      context-menu-mentions: #context-menu-mentions;
      url-scheme-mentions: https://quaive.cornelis.amsterdam/users/{USER};
      context-menu-tags: #context-menu-tags;
      url-scheme-tags: https://quaive.cornelis.amsterdam/tags/{TAG};
  ">
```


<!-- .slide: data-background="Blue" -->
```html[|1,3,7-8,13-14,19-20]
<template id="context-menu-mentions">
  <form
      class="pat-checklist pat-autosubmit tiptap-mentions-context-menu">
    <label>
      <input
          type="checkbox"
          name="mention"
          value="hans"
    />hans</label><br/>
    <label>
      <input
          type="checkbox"
          name="mention"
          value="franz"
    />franz</label><br/>
    <label>
      <input
          type="checkbox"
          name="mention"
          value="sepp"
    />sepp</label><br/>
  </form>
</template>
```


<!-- .slide: data-background="Blue" -->
```html[|1,3,7-8,13-14,19-20]
<template id="context-menu-tags">
  <form
      class="pat-checklist pat-autosubmit tiptap-tags-context-menu">
    <label>
      <input
          type="checkbox"
          name="tag"
          value="I ♥ UTF-8"
      />I ♥ UTF-8</label><br/>
    <label>
      <input
          type="checkbox"
          name="tag"
          value="music"
      />music</label><br/>
    <label>
      <input
          type="checkbox"
          name="tag"
          value="books"
      />books</label><br/>
  </form>
</template>
```




## Finally: autofocus and placeholder
```html [15,16]
<textarea
    name="text"
    class="pat-tiptap"
    data-pat-tiptap="
        toolbar-external: #tiptap-external-toolbar;
        link-panel: #pat-modal .link-panel;
        context-menu-link: #context-menu-link;
        image-panel: #pat-modal .image-panel;
        source-panel: #pat-modal .source-panel;
        context-menu-mentions: #context-menu-mentions;
        url-scheme-mentions: https://quaive.cornelis.amsterdam/users/{USER};
        context-menu-tags: #context-menu-tags;
        url-scheme-tags: https://quaive.cornelis.amsterdam/tags/{TAG};
    "
    autofocus
    placeholder="Your poem goes here...">
```




<!-- .slide: data-background="Cyan" class="full" -->
<iframe src="./tutorial/tiptap.html" loading="lazy"></iframe>




<!-- .slide: data-background="Yellow" -->
## Webpack Module Federation


<!-- .slide: data-background="Yellow" class="full" -->
<img alt="Webpack Module Federation" style="width: 60%; height: auto" src="./resources/module-federation.svg" />




<!-- .slide: data-background="Black" -->
# This is the end.

