In the Assets manager you can add custom css to impact how everything is rendered
You can get here using the import and Export window

```css
/* Enter your custom CSS here */

/* accent color */
:root {
    --system-accent-color: #096cdc;
}

.ͼu .cm-url, .ͼu .cm-link, .ͼu .cm-code-mark, .ͼu .cm-zkn-link {
    color: #096cdc;
}

.ͼu .cm-scroller {
    color: var(--grey-7);
    font-family: "Ubuntu";
    font-size: 0.875em;
}

.main-editor-wrapper .cm-editor .code {
    color: #586e75;
    font-family: monospace;
    font-size: 0.875em;
}

.ͼu .cm-monospace {
    font-family: monospace;
    /* font-size: 0.875em; */
}

/* ToC settings */
body #sidebar div.toc-entry-container div.toc-entry {
    font-size: 0.8em;
}

body #sidebar div.toc-entry-container div.toc-level {
    flex-shrink: 1;
    padding: 0px 5px;
    font-size: 0.8em;
    font-weight: normal;
    color: var(--system-accent-color, --c-primary);
}


/* dark scrollbar in dark mode */
body.dark {
  scrollbar-color: #666 #000;
}

/* tags */
.ͼu .cm-zkn-tag{
  color: #096cdc;
  background-color: #e6f0fb;
  font-weight: normal;
  font-size: 0.8em;
  border-radius: 7px;
  padding: 3px;
}


/* underline links */
.cm-link:hover {
  text-decoration: underline;
}

/* /* space out bulleted list items more */ */
/* .cm-line:has(.cm-list.cm-content-span.cm-code-mark.cm-meta, .rendered-bullet) { */
/*   padding-top: 10px; */
/* } */
/**/
/* /* indent lists further than the default of ~1 character */ */
/* .cm-line > span.cm-list:first-of-type:not(.cm-meta):not(.cm-code-mark) { */
/*   letter-spacing: 10px; */
/* } */

/* remove indentation of headings */
.size-header-1, .size-header-2, .size-header-3, .size-header-4, .size-header-5, .size-header-6 {
  position: relative;
  padding: 0 !important;
}

/* move heading level marker to the right */ 
.heading-tag {
  position: absolute;
  /* left: 0; */
  padding: 0 !important;
}

/* alter hover behavior */
.heading-tag:hover {
  background: none !important;
}

/* reveal heading level when you hover over the right side */
.heading-tag:hover span {
  color: #ccc !important;
}

/* but hide it by default */
.heading-tag span {
  color: transparent !important;
}

/* better heading font-sizes and aesthetics */
.size-header-1 {
  font-size: 1.8em !important;
  border-bottom: 1px #ddd solid;
}
.dark .size-header-1 {
  border-bottom: 1px #555 solid;
}
.size-header-2 {
  font-size: 1.5em !important;
  border-bottom: 1px #ddd solid;
}
.dark .size-header-2 {
  border-bottom: 1px #555 solid;
}
.size-header-3 {
  font-size: 1.5em !important;
}
.size-header-4 {
  font-size: 1.3em !important;
}
.size-header-5 {
  font-size: 1.175em !important;
}
.size-header-6 {
  font-size: 1em !important;
}

/* prevent "dancing" bulleted lists */
.cm-line > * {
  vertical-align: top;
}

/* prevent "dancing" bulleted lists */
/* .cm-list.cm-content-span.cm-code-mark.cm-meta, .rendered-bullet { */
/*   display: inline-block; */
/*   text-indent: 0; */
/*   width: 10px; */
/* } */

/* more beautiful code blocks */

/* inline code blocks */
span.code {
  vertical-align: baseline;
  background-color: #f3f4f4;
  padding: 2px;
}
.dark span.code {
  vertical-align: baseline;
  background-color: #333;
  color: #eee !important;
  padding: 2px;
}

/* add support for horizontal rules */
.cm-hr {
  display: inline-block;
  font-family: monospace;
  width: 100%;
  line-height: 0.25;
  color: transparent !important;
  border-bottom: 2px #e7e7e7 solid;
}
.dark .cm-hr {
  border-bottom: 2px #666 solid;
}
