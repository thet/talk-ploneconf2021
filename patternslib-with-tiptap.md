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

- Part 1: For Designers <!-- .element: class="fragment" -->

- Part 2: For Integrators <!-- .element: class="fragment" -->

- Part 3: For Developers <!-- .element: class="fragment" -->


<!-- .slide: data-background="yellow" -->
## Part 1: For Designers

- What is the Patternslib? <!-- .element: class="fragment" -->
- How to use the Patternslib <!-- .element: class="fragment" -->
- Patternslib Showcase <!-- .element: class="fragment" -->
- What is the tiptap editor? <!-- .element: class="fragment" -->


<!-- .slide: data-background="yellow" -->
## Part 2: For Integrators &<br>Part 3: For Developers

- This is pat-tiptap <!-- .element: class="fragment" -->
- <span>How to get this into Plone?<br><small>Webpack module federation</small></span> <!-- .element: class="fragment" -->
- collective.tiptap <!-- .element: class="fragment" -->




<!-- .slide: data-background="Cyan" -->
# What is the Patternslib?


<!-- .slide: data-background="Cyan" -->

> Patternslib is a library of reusable patterns which let you create rich, dynamic and interactive prototypes or websites, without having to know or care about Javascript.

https://patternslib.com/documentation/what-is-patternslib <!-- .element: class="caption" -->


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
- Designed for Non-JavaScript People
- Use semantic HTML
- Developer friendly
- Easy way to initialize JavaScript and to pass Options


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
- A modern text editor
- Headless
- HTML, Markdown, whatever.
- Based on Prosemirror
- Awesome features (Collaboration, Mentions, Checkboxes, ...)


<!-- .slide: data-background="Blue" -->
- https://tiptap.dev/


<!-- .slide: data-background="Blue" -->
## Patternslib integration
- https://github.com/Patternslib/pat-tiptap/pull/2


<!-- .slide: data-background="Blue" -->
http://localhost:3010/src/


<!-- .slide: data-background="Blue" -->
https://quaive.cornelis.amsterdam/workspaces/asian-steering-committee/minutes/minutes-of-2014-06-09


<!-- .slide: data-background="Blue" class="full" -->
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


<!-- .slide: data-background="Blue" class="full" -->
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


<!-- .slide: data-background="Blue" class="full" -->
```html[|3-6]
<div id="tiptap-external-toolbar">
  <!-- other buttons -->
  <a
      href="#modal-link"
      class="button-link pat-modal"
      >Link</a>
</div>
```


<!-- .slide: data-background="Blue" class="full" -->
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


<!-- .slide: data-background="Blue" class="full" -->
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


<!-- .slide: data-background="Blue" class="full" -->
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


<!-- .slide: data-background="Blue" class="full" -->
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




<!-- .slide: data-background="Cyan" class="full" -->
<iframe src="./tutorial/tiptap.html"></iframe>



















<!-- .slide: data-background="Yellow" -->
## Webpack Module Federation


<!-- .slide: data-background="Yellow" class="full" -->
<img alt="Webpack Module Federation" style="width: 60%; height: auto" src="./resources/module-federation.svg" />














<!-- .slide: data-background="Cyan" class="full" -->



<!-- .slide: data-background="Cyan" class="full" -->







<!-- .slide: data-background="Cyan" -->
<!-- .slide: data-background="Cyan" -->
<!-- .slide: data-background="Cyan" -->
<!-- .slide: data-background="Cyan" -->
<!-- .slide: data-background="Cyan" -->
<!-- .slide: data-background="Cyan" -->









<!-- .slide: data-background="Black" -->
# This is the end.

