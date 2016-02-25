 ![Add-on icon](misc/spot64.png) Enlight
========================================


Firefox add-on providing syntax highlighting for raw code, based on the
highlight.js project.

Syntax highlighting relies on highlight.js project (see [project
homepage][hljs]. Currently packaged with the add-on is the version
9.2.0 of highlight.js, which provides
71    color themes and syntax for
150   languages.

## Install

Theory: just open the `enlight_highlightjs@jetpack-<version>.xpi` file
(`File->Open`) in Firefox. Confirm you want to install, and you're done. Note
that this is or will soon become impossible due to [Mozilla policy on add-ons
signature][signing]; so unless you use Firefox Developer Edition or Nightly, the
preferred way is to install through [the add-on page on Mozilla add-ons
platform][amo].

One needs the `jpm` tool to build the add-on ([documentation][jpm]). If you wish
to build from sources, the `xpi` add-on file itself can easily be generated
with a `jpm xpi` command from the Mozilla add-on SDK (see [documentation on
MDN][sdk]).

Building with `cfx` is no longer supported. WebExtensions do not seem to
support per tab activation of the toggle button, which makes it unsuitable for
this add-on for now.

## Usage

### Basics

On install, a new button with a ~~spotlight~~ light bulb
![buttonOff](data/lightbulb_off-32.png) (yes, it's supposed to be a
~~spotlight~~ light bulb − but the magnificent spotlight remains the add-on
icon in the add-on manager tab for now) should appear in Firefox toolbar.

To highlight raw source code in the active tab, click on this button and select
the language syntax you want to use (or “Autodetect” for automatic detection).
If you want to undo highlighting, just click again on the button
![buttonOn](data/lightbulb_on-32.png) (reloading the page also works).

### Options

You can also customize some options through Firefox add-on manager tab:
* Color theme selection (_default: Solarized Dark_): change the CSS theme in
  use for syntax highlight.
* Automatic highlighting (_default: off_): check it to automatically trigger
  syntax highlighting for all plain text files.
* Alternate icon set (_default: off_): use white icons; useful if you use a
  dark theme for Firefox, such as the default theme for Developer Edition
* Adapt background body color (_default: on_): remove white border due to
  body background color. There is no reason to deactivate this, unless you try
  to highlight non-plain text pages and get strange background modification.
* Add line numbers (_default: off_): add line numbers on the left of file
  content. Line numbers are created with CSS and are not part of the file
  contents.

When line numbering is enabled, it is possible to jump to line passed through
URL (_default: on_): scroll to e.g. line 27 and select it if a suffix such as
`#Line27` or `#line27` or `#L27` or `#l27` is appended to the URL **before**
the script loads (this does not relies on HTML anchors and cannot be triggered
by simple URL modification; reload the script for current page if you added the
suffix afterward).

## Current branch

Current branch embeds syntax for all languages supported by highlight.js.

Developers: beware, this branch is regularly rebased on master branch.

## License

The code relative to the add-on itself is placed under the Mozilla Public
License v. 2.0 (see file [LICENSE][mpl]).

The code for highlight.js (_i.e._ everything under the `data/highlightjs`
directory) was released under the BSD License (see relative [LICENSE][bsd] file
for details).

## Miscellaneous

Other than on the [hilight.js homesite][hljs], you can find a list of supported
languages in [data/languages-all.json][languages], and of available color schemes in
[package.json][package].

[hljs]: https://highlightjs.org
[signing]: https://blog.mozilla.org/addons/2015/02/10/extension-signing-safer-experience
[amo]: https://addons.mozilla.org/firefox/addon/enlight
[sdk]: https://developer.mozilla.org/en-US/Add-ons/SDK/Tutorials/Getting_started
[mpl]: https://github.com/Qeole/Enlight/blob/master/LICENSE
[bsd]: https://github.com/isagalaev/highlight.js/blob/master/LICENSE
[languages]: https://github.com/Qeole/Enlight/blob/master/data/languages-all.json
[package]: https://github.com/Qeole/Enlight/blob/master/package.json
[jpm]: https://developer.mozilla.org/en-US/Add-ons/SDK/Tools/jpm
