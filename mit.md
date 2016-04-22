---
layout: default
title: What MIT gets wrong about Using Zotero with LaTeX and BibTeX
---

You're probably here because you visited the mit.edu page on [Zotero at MIT: Zotero with LaTeX and
BibTeX](http://libguides.mit.edu/c.php?g=176000&p=1159208), and you want to learn about the [Better
BibTeX](https://github.com/retorquere/zotero-better-bibtex/wiki) utility that page linked to. If you want to find out what
Better BibTeX can do for you, you can visit the
[documentation](https://github.com/retorquere/zotero-better-bibtex/wiki), but if you just want to download Better BibTeX
for Zotero, you can find the latest release [here](https://github.com/retorquere/zotero-better-bibtex/releases/latest).

The MIT page contains some omissions however that could unnecessarily scare you away from using Zotero for your Bib(La)TeX
needs. The MIT librarians seem to be actively hostile to this being pointed out, which is why I've put up this page. On
this page, I assume you're open to using Better BibTeX to address these problems -- if not, you probably would not be
here, right? Onwards then. The headers below match the relevant section of the [MIT
page](http://libguides.mit.edu/c.php?g=176000&p=1159208) to explain what I think could be reformulated.

## How do I export from Zotero to BibTeX?

The points below will assume you will use the 'Better BibTeX' format rather than the 'BibTeX' format as the MIT page
instructs.

## How can I fix references that had problems formatting special characters?

Not even the standard BibTeX exporter from Zotero makes these entirely basic mistakes anymore, so I have no idea why
this is still up there. Still, there *are* some LaTeX constructs that Zotero does not export well. Better BibTeX however
does, and if you ever find an exception, I very much welcome [bug
reports](https://github.com/retorquere/zotero-better-bibtex/issues) so I can get that corrected. I haven't had bug
reports like these in ages though. Better BibTeX has quite comprehensive coverage when it comes to translating
references to correct BibTeX.

## How can I make an organization name display correctly?

It doesn't look like the MIT librarians have ever used Zotero. You can toggle author fields in Zotero between two-part
and single-part names by clicking the icon to the right of the author name. Single-part author names are written out
properly quoted automatically. This is not something you need or want to by hand.

## How can I override BibTeX capitalization conventions?

Again, the MIT librarians are making unwarranted assumptions here about what Zotero writes out *and* are suggesting a
"solution" that is actually as bad as the problem it sets out to solve. The proper way to prevent

> title={IEE Proceedings}

to be turned into

> Iee proceedings

when your document is compiled is **not** to encode it as the MIT librarians suggest using

> title="{IEE Proceedings}"

but rather

> title=\{\{IEE\} Proceedings\}

The "solution" suggested by the MIT librarians does indeed prevent BibTeX from meddling with your capitalization, except
some citation styles *demand* that they are able to do this -- some styles demand that that titled would become

> IEE proceedings

and the MIT "solution" prevents this. You only want to protect those exact *parts* that you want to exclude from this
process, and guess what: *Zotero already does this* for words containing uppercase letters; in the case of Better BibTeX, it will even do this for letters line `Ñ` . If there are some parts where you want to keep something
lowercased regardless of the BibTeX style you chose, you can wrap that part in `<span class="nocase">....</span>` and whatever's between them will be excluded
from case-changing. This is formally supported in Zotero and will work for BibTeX but also if you're using your
references in Word/LibreOffice/etc.

Again, you do not need or want to make this change manually every time you export to BibTeX when Zotero is perfectly
capable of doing this for you.
