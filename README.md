# pico.firstdraft.css

The stylesheet contains our modifications to [Pico CSS](https://picocss.com/), along with some modifications to [Pagy's](https://github.com/ddnexus/pagy) default styles.

The stylesheet can be linked by:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/firstdraft/pico.firstdraft.css@0.0.1/pico.firstdraft.css">
```

Where `@0.0.1` is the version number from the `package.json` file. Anytime an edit is made to `pico.firstdraft.css`, the SemVer version in `package.json` should be bumped. Bumping the version afer an edit will run the `release.yml` GitHub action workflow to generate a new release tag, automatically making the new stylesheet version available via [jsDeliver](https://www.jsdelivr.com/github).

The following external CDN links must also be included alongside ours:

```html
<!-- The official Pico CSS stylesheet -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@picocss/pico@2/css/pico.conditional.css">

<!-- The official Bootstrap utilities stylesheet -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/twbs/bootstrap@main/dist/css/bootstrap-utilities.css">
```
