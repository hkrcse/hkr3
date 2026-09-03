# hkr-main converted to the academic CV layout

The Bootstrap portfolio template (`hkr-main`) has been rebuilt in the layout of the
reference site you pasted: a two-column CV with a name header, social buttons, a
round profile photo, and section blocks where dates sit on the left and detail on
the right.

## What's in here

```
hkr-cv/
    index.html          the whole page, all content inline
    assets/main.css     one stylesheet, hand-written for this layout
    images/
        profile.png     your portrait (was images/bg_2.png)
        project-*.png   project screenshots, kept in case you want them back
        blockchain.png
    README.md
```

That is the entire site. There is no build step, no `npm install`, no Jekyll. Open
`index.html` in a browser and it works; drop the folder on GitHub Pages, Netlify,
or any static host and it works there too.

## What was dropped from hkr-main, and why

The original template shipped 175 files, most of which were never used by the page:

| Dropped | Reason |
| --- | --- |
| jQuery, Popper, Bootstrap JS, Owl Carousel, AOS, Stellar, Waypoints, Magnific Popup, animateNumber, easing, google-map.js | The new layout is static. Nothing on the page needs JavaScript, so there is none. |
| `css/style.css` (255 KB), Bootstrap CSS, animate.css, aos.css, owl carousel CSS | Replaced by one 7 KB stylesheet. |
| Flaticon, Icomoon, Ionicons, Open Iconic fonts (about 2 MB) | Icons are now inline SVG in the HTML. Nothing to download, works offline. |
| Google Fonts (Poppins) | Uses the system font stack, so no external request and no layout shift. |

Content that was placeholder text in the original is gone rather than carried
over. Specifically: the three lorem-ipsum blog posts, the "Awards / Complete
Projects / Happy Customers / Cups of coffee" counters, the "I'm available for
freelancing" and "Hire me" calls to action, the "Web Design / App Development"
services list, the duplicated Notre Dame education entry, the two "Cambridge
University" entries, and every paragraph beginning "A small river named Duden" or
"Far far away, behind the word mountains".

The skill percentage bars (Solidity 85%, Java 85%, and so on) were also dropped.
Self-assigned percentages don't carry meaning on an academic page, and the target
layout has no place for them. The skills themselves are listed under Technical
Skills, grouped by kind.

## Content that needs your attention

Two places need real information that the original template did not contain:

1. **Paper authors.** The Research Papers entry currently lists only your name.
   The original template never listed the full author list. Search `EDIT:` in
   `index.html` and replace it with the full list, in the order it appears on the
   paper.
2. **Canonical URL.** The two `EDIT:` lines in `<head>` point at
   `https://hkrcse.github.io/`. Change them to wherever you actually deploy.

Everything else is taken from the original template: the ICCA 2024 paper and its
DOI, both lecturer positions, the KUET/NDC/RHS education entries, the Dean's Award
and scholarships, the six projects with their live links, and your contact details.

The reference site has an "A Little More About Me" section. There is no
equivalent content in `hkr-main` to convert, so nothing was written for it rather
than inventing hobbies for you. To add it, copy any `text-container` block in
`index.html` and change the heading.

## Editing

Everything is plain HTML with commented section markers, so you edit content by
editing the page.

**Add an entry to Experience, Education, Papers, or Projects** — copy one block:

```html
<div class="row clearfix layout layout-left">
  <div class="col-xs-12 col-sm-4 col-md-3 col-print-12 details">
    <h4>Title</h4>
    <p>Dates</p>
    <a href="https://example.org" target="_blank" rel="noopener" class="link">example.org</a>
  </div>
  <div class="col-xs-12 col-sm-8 col-md-9 col-print-12 content">
    <p>Detail line</p>
  </div>
</div>
```

**Add a whole section** — copy a `container text-container` block for prose or a
list, or a `container list-container` block for dated entries, and paste it
between two existing sections.

**Change a social link** — edit the `href` in the `icons` list. To remove one,
delete its `<li>`. To add one, copy an `<li>` and swap the SVG path.

**Change colours** — the palette is six CSS variables at the top of
`assets/main.css`. `--link` controls every link on the page.

**Replace the photo** — overwrite `images/profile.png`. A square image works best;
it is cropped to a circle.

## Printing

The stylesheet has an A4 print block, so browser print (Ctrl+P) gives a clean
four-page CV: the social buttons and photo are hidden, the two-column rows become
full width, and links print as plain black text. `class="no-print"` hides anything
else you don't want on paper.

## Browser support

Modern Chrome, Firefox, Safari, and Edge. The layout uses flexbox, CSS custom
properties, and `aspect-ratio`. If you need to support a browser without
`aspect-ratio`, give `.profile-img` a fixed `height: 190px`.
