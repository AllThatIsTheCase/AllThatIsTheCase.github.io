---
layout: default
title: React.js
---

Ah React.js, how I've come to hate you in the past few months. I now fully understand what the concept of [Javascript
Fatigue](https://medium.com/@ericclemmons/javascript-fatigue-48d4011b6fc4#.yvusnn9n1) means. To get a React app going you need
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
toolkits are all about components. Yeah? No.

(criteria cribbed from [xubuild](https://xubuild.github.io/2015/11/11/compare-react-ui-libraries/). Quick conclusion:
more than a year later, the best choices are still a lukewarm "maybe". I hate React)

# Selection criteria

**Components**:

Basics:
<input disabled type="checkbox"> dropdownlist / select  
<input disabled type="checkbox"> date picker  
<input disabled type="checkbox"> time picker  
<input disabled type="checkbox"> tab  
<input disabled type="checkbox"> [slide in menu](http://callmenick.com/_development/slide-push-menus/)  
<input disabled type="checkbox"> dialog / modal / pop up window  
<input disabled type="checkbox"> dropdown menu  
<input disabled type="checkbox"> table  
<input disabled type="checkbox"> allows controls (menu etc) in tables  
<input disabled type="checkbox"> responsive  
Extra:  
<input disabled type="checkbox"> loading indicator  
<input disabled type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
<input disabled type="checkbox"> multi-select  
<input disabled type="checkbox"> chart  
<input disabled type="checkbox"> table with sorting, filtering  
<input disabled type="checkbox"> theme  

**Infrastructure:**

<input disabled type="checkbox"> plays nice with react-router
<input disabled type="checkbox"> use ES6 and class syntax
<input disabled type="checkbox"> compatible with React 15.4.0
<input disabled type="checkbox"> actively updated and supported
<input disabled type="checkbox"> should not have bug that broke the whole software reported in GitHub issues
<input disabled type="checkbox"> open source

# The contenders

## Material-UI

**Components**:

Basics:  
<input disabled type="checkbox" checked> dropdownlist / select  
<input disabled type="checkbox" checked> date picker  
<input disabled type="checkbox" checked> time picker  
<input disabled type="checkbox" checked> tab  
<input disabled type="checkbox" checked> [slide in menu](http://callmenick.com/_development/slide-push-menus/)  
<input disabled type="checkbox" checked> dialog / modal / pop up window  
<input disabled type="checkbox" checked> dropdown menu  
<input disabled type="checkbox" checked> table  
<input disabled type="checkbox"> allows controls (menu etc) in tables: sort of? Not natively it seems but an [an external component](https://github.com/andela-cdaniel/mui-data-table) seems to do it.  
<input disabled type="checkbox" checked> responsive  
Extra:  
<input disabled type="checkbox" checked> loading indicator  
<input disabled type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
<input disabled type="checkbox"> multi-select  
<input disabled type="checkbox"> chart  
<input disabled type="checkbox"> table with sorting, filtering  
<input disabled type="checkbox"> theme: sort of, but underdocumented and a major overhaul is underway.  

**Infrastructure:**

<input disabled type="checkbox"> plays nice with react-router  
<input disabled type="checkbox" checked> use ES6 and class syntax  
<input disabled type="checkbox" checked> compatible with React 15.4.0  
<input disabled type="checkbox" checked> actively updated and supported  
<input disabled type="checkbox" checked> should not have bug that broke the whole software reported in GitHub issues  
<input disabled type="checkbox" checked> open source  

No idea whether it hates
react-router. Has some real problems with its internal styling solution which mandated a pretty extensive overhaul, but
there's no idea currently when that will be done, or how much work it will be to port to it.

### ANTD

allows controls in tables, has datepicker, but unsure about theming (and I like material). It likes react-router, and
advocates dva, which is like react-create-app but with strong opinions on combining redux and stuff. Good. Very few
contributors, which is a *major* risk in the volatile javascript world. Table has filter/sort/paging. Theming is
limited, so the designer who got me pixel-perfect specs is going to be unhappy. And the majority of discussion/docs is
in Chinese, and the UI components default to Chinese. L10n exists but how mine isn't supported and how to add new ones
is undocumented. Despite all this, it's still one of the two main contenders. This should tell you something.

# What has fallen to the side

### Grommet

Has date picker, table allows components, but table has no paging, no search. This library has the most frustrating
project name I've encountered in a long time -- *nearly everything you find on google has to do with little metal
rings*, regardless of extra search terms you put in.

### React-toolbox

Wow, this looks good, and actively maintained. Except that it doesn't like react-router *at all*, and the table
component [can not (realistically) have components](https://github.com/react-toolbox/react-toolbox/issues/963) like
buttons/dropdowns/etc in cells. Table is not sortable without an [unmerged
pull request](https://github.com/react-toolbox/react-toolbox/pull/1035) or an [unreleased external
component](https://github.com/react-toolbox/react-toolbox/issues/322). Has a [massive structural
change](https://github.com/react-toolbox/react-toolbox/pull/666) looming for over 6 months to address such issues with
unresolved conflicts and no clear indication of how much a client app would have to change. A boilerplate that's
referenced in the issue that tracks the forever-soon-now release doesn't start.

okbyethen.

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

