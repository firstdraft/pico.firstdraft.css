# pico.firstdraft.css

## Overview and how to update

The stylesheet contains our modifications to [Pico CSS](https://picocss.com/), along with some modifications to [Pagy's](https://github.com/ddnexus/pagy) default styles.

The stylesheet can be linked by:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/firstdraft/pico.firstdraft.css@0.0.1/pico.firstdraft.css">
```

Where `@0.0.1` is the version number from the `package.json` file. Anytime an edit is made to `pico.firstdraft.css`, the SemVer version in `package.json` should be bumped. Bumping the version afer an edit will run the `release.yml` GitHub action workflow to generate a new release tag, automatically making the new stylesheet version available via [jsDeliver](https://www.jsdelivr.com/github).

You can also just use the updated `@latest` version:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/firstdraft/pico.firstdraft.css@latest/pico.firstdraft.css">
```

The following external CDN links must also be included alongside ours:

```html
<!-- The official Pico CSS stylesheet -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.conditional.css">

<!-- The official Bootstrap utilities stylesheet -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/twbs/bootstrap@main/dist/css/bootstrap-utilities.css">
```


## pico.firstdraft.css Full Documentation

### Overview

`pico.firstdraft.css` provides enhancements to Pico CSS that add common UI patterns without compromising Pico's semantic HTML approach. All styles are scoped with the `.pico` class to ensure compatibility.

### Usage

1. Include :

    ```html
    <!-- The official Pico CSS stylesheet -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.conditional.css">

    <!-- The official Bootstrap utilities stylesheet -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/twbs/bootstrap@main/dist/css/bootstrap-utilities.css">

    <!-- Our modifications to default Pico CSS styles -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/firstdraft/pico.firstdraft.css@latest/pico.firstdraft.css">
    ```

2. Add the `.pico` class to your `<body>` tag:

    ```html
    <body class="pico">
    ```

### Page Structure

Implements a flexbox-based layout such that the footer stays at the bottom of the viewport even when there isn't much content.

Usage: the document _must_ have this structure:

```html
<body>
  <header></header>
  <main></main>
  <footer></footer>
</body>
```

### Styled Header & Footer

- **Header**: `body>header` gets a light grey background (`--pico-color-grey-50`), intended to set apart a navbar.
- **Footer**: `body>footer` gets grey background (`--pico-color-grey-150`) with generous padding.

### Custom Container Variants

Additional, narrower, repsonsive containers:

#### `.container-half`

A container that's 50% of Pico's default container width at each breakpoint.

#### `.container-two-thirds`

A container that's 66.67% of Pico's default container width at each breakpoint.

### Typography Enhancements

#### Improved List Spacing

Removes bottom margin from the last child of any list item to prevent excessive spacing in nested lists.

#### Description Lists

Bootstrap-style description lists with:

- No top margin.
- Bold `<dt>` elements.
- Reduced spacing between `<dd>` elements.

### Card Components

#### Enhanced Article Headers

Removes bottom margin from the last element in article headers for tighter spacing.

#### List Group Flush

Creates Bootstrap-style flush list groups within cards. Usage: if an `article` has an immediate `ul` child, it will pick up flush list group styling. (If you want a regular `ul`, wrap it in a `div`.)

- Full-width list items that extend to card edges.
- Subtle borders between items.
- No bullets or default list styling.

```html
<article>
  <header>
    <h3>Card Title</h3>
  </header>
  <ul>
    <li>List item 1</li>
    <li>List item 2</li>
  </ul>
</article>
```

#### List Group Action Items

If a list group flush contains only one child which is an `<a>`, it will pick up action item styling:

- Entire list item becomes clickable.
- Chevron indicator on the right.
- Hover state with primary color background.
- Active state support using `aria-current="page"`.

```html
<article>
  <ul>
    <li><a href="/page1">Action Item 1</a></li>
    <li><a href="/page2" aria-current="page">Active Item</a></li>
    <li>Regular item with <a href="/page3">partial link</a></li>
  </ul>
</article>
```

#### Table Flush

Usage: if an `article` has an immediate `table` child, or a `table` within a `div.overflow-auto`, it will pick up flush list group styling. (If you want a regular `table`, wrap it in any other `div`.)

Automatically removes borders and margins from tables that are direct children (or wrapped in a single div) of article elements:

- Extends tables to full width of card.
- Removes default borders.
- Uses negative margins to align with article edges.

```html
<article>
  <table>
    <!-- Full-width flush table -->
  </table>
</article>

<!-- Also works with overflow wrapper -->
<article>
  <div class="overflow-auto">
    <table>
      <!-- Full-width flush table with scroll -->
    </table>
  </div>
</article>
```

### Compatibility with Bootstrap Utilities

The stylesheet works fine alongside `bootstrap-utilities.css`, providing:

- All Bootstrap utility classes (spacing, flexbox, display, etc.).
- No conflicts with Pico's base styles.
- Consistent variable usage.

For when Pico just isn't enough.
