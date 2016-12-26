---
layout: default
title: React.js
---

Ah React.js, how I've come to hate you in the past few months. I now fully understand what the concept of [Javascript
Fatigue](https://medium.com/@ericclemmons/javascript-fatigue-48d4011b6fc4#.yvusnn9n1). To get a React app going you need
to assemble a million moving parts each of which of whom barely acknowledge each others existence. Any boilerplate
project you might find is at least 6 months behind the curve which means it depends on node modules which changed
incompatibly 5 months ago and 3 times since. If you go with the boilerplate for your UI toolkit, you can rest assured it
won't play nice with, e.g., react-router, which another necessary component will demand be included.

Here's my search for a sort-of-coherent set of pieces which will allow me to concentrate on the app I must create. It's
not a very fancy app. It's a list of clients, a detail screen on each, and protected with a password. Just a few weeks
of work, right.

**WRONG** 

Boy oh boy was I wrong. React means that you're not building a web app. It means that you're first assembling a toolbox
**from scratch** and then use that toolbox to build a web app (you hope). A UI? 10 options. Data handling? 20 options
(saga? redux? flux? aaagh!). Routing? Oh great, more options. Accessing the backend? Guess what, more options. How does
this combinatory explosion of options hang together? **No friggin idea**.

I don't want to deal with authentication. Authentication is easy to get disastrously wrong, and a pain in the neck to
maintain the backend for. So I go with auth0, which makes it all nice and easy and packaged. Cool.

Auth0 seems to require react-router, but that seems like a reasonable way to go, so we're off.

Nobody sane wants to do a UI wholly by hand, so I'm picking an UI lib. Should be easy. React is all about components, UI
toolkits are all about components.

Ugh.

# What may still be viable contenders

### Material-UI

Has datepicker. Table with controls may or may not need [an external
component](https://github.com/andela-cdaniel/mui-data-table). But so far still a possibility. No idea whether it hates
react-router. Has some real problems with its internal styling solution which mandated a pretty extensive overhaul, but
there's no idea currently when that will be done, or how much work it will be to port to it.

### ANTD

allows controls in tables, has datepicker, but unsure about theming (and I like material). No idea whether it hates
react-router. Very few contributors, which is a *major* risk in the volatile javascript world. Table has
filter/sort/paging. Theming is limited, so the designer who got me pixel-perfect specs is going to be unhappy.

### Grommet

Has date picker, table allows components, but table has no paging, no search. This library has the most frustrating
project name I've encountered in a long time -- *nearly everything you find on google has to do with little metal
rings*, regardless of extra search terms you put in.

# What has fallen to the side

### React-toolbox

Wow, this looks good, and actively maintained. Except that it doesn't like react-router *at all*, and the table
component can not (realistically) have components like buttons/dropdowns/etc. okbyethen.

### Semantic-UI

No date picker? Really? okbyethen.

# What never really were contenders even if you couldn't be blamed for thinking they were

### Bootstrap

First stop was bootstrap. React-bootstrap seems to play nice with react-router, so no issues getting auth0 going. But
bootstrap is mainly just UI layout; it does bugger-all for all the other necessary components (dropdowns, date pickers,
sortable tables), and I'm sure as hell not cobbling together an personal UI library in hopes that it will style
reasonably consistently.

* [Pivotal](http://styleguide.cfapps.io/faq.html): no date picker, no traction
* [Foundation](http://webrafter.com/opensource/react-foundation-apps): is just UI layout, like Bootstrap. Useless.
* [MUIcss](https://www.muicss.com/docs/v1/react/introduction): no datepicker

