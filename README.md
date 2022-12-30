# Skillforest

A writeup/mockup of what a distributed learning system on top of the World Wide Web could look like, leveraging open standards in hopes of bringing together educators and learners across the network.

## Build

Refer to [Jekyll's installation documentation](https://jekyllrb.com/docs/installation/) (with one caveat — the site is built using Ruby 3.0; earlier versions may work, but are untested) and [command line usage](https://jekyllrb.com/docs/usage/).

💭 I would've placed a Skillforest-compatible annotation here, requiring to learn about Ruby _runtime_ (no need to dive into the _language_), basics of [Bundler](https://bundler.io/) and let the system resolve the rest. But for now that's only a dream.

## Contribute

If you're interested in contributing to the project, [get in touch](https://dside.ru/en/)!

I could use some expertise on some subjects. I intend to eventually acquire some for myself, but help could accelerate this process tremendously.

- **[RDFa](https://www.w3.org/TR/rdfa-primer/) and Semantic Web:** the very core of the project is expected to be a _convention/standard_ that others can use to expose their materials to compatible tools. This project shares a lot of goals and usage patterns with [Open Graph Protocol](https://ogp.me/) and so the same foundation was chosen for this as well.
- **Browser app development:** my "rich frontend" experience so far is highly exotic ([re-frame](https://day8.github.io/re-frame/re-frame/)) and did not leverage the JavaScript ecosystem that much. This project may very well require leveraging several large libraries like [Quadstore](https://github.com/belayeng/quadstore) ([the IndexedDB-backed variant](https://github.com/belayeng/quadstore#browser-usage)) and the broader RDF/JS suite. The goal is to get an offline-capable browser application (not so much for offline use as much as to make it not depend on a server).
- _(Out of initial scope, but could be handy)_ **Native app development:** I've worked on games before, but very little on native GUIs. Would be great to have a drastically different alternative to an easy-to-try browser app.

## License

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa]. 

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

Is it too restrictive? Probably. I could feasibly be talked into releasing this under a more permissive license if somebody needs it. But for now — just CC-BY-NC-SA.

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
