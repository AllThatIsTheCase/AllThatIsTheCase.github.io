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
more than a year later, the best choices are still a lukewarm "maybe". I hate the React ecosystem)

# Selection criteria

**Components**:

Basics:  
<input disabled type="checkbox"> dropdownlist / select  
<input disabled type="checkbox"> date picker  
<input disabled type="checkbox"> time picker  
<input disabled type="checkbox"> tab  
<input disabled type="checkbox"> dialog / modal / pop up window  
<input disabled type="checkbox"> dropdown menu  
<input disabled type="checkbox"> table  
<input disabled type="checkbox"> allows controls (menu etc) in tables  
<input disabled type="checkbox"> responsive  
Extra:  
<input disabled type="checkbox"> loading indicator  
<input disabled type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
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
<input disabled checked type="checkbox"> dropdownlist / select  
<input disabled checked type="checkbox"> date picker  
<input disabled checked type="checkbox"> time picker  
<input disabled checked type="checkbox"> tab  
<input disabled checked type="checkbox"> dialog / modal / pop up window  
<input disabled checked type="checkbox"> dropdown menu  
<input disabled checked type="checkbox"> table  
<input disabled type="checkbox"> allows controls (menu etc) in tables  
<input disabled checked type="checkbox"> responsive  
Extra:  
<input disabled checked type="checkbox"> loading indicator  
<input disabled type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
<input disabled type="checkbox"> table with sorting, filtering  
<input disabled type="checkbox"> theme: sort of, but underdocumented and a major overhaul is underway.  

**Infrastructure:**

<input disabled type="checkbox"> plays nice with react-router  
<input disabled checked type="checkbox"> use ES6 and class syntax  
<input disabled checked type="checkbox"> compatible with React 15.4.0  
<input disabled checked type="checkbox"> actively updated and supported  
<input disabled checked type="checkbox"> should not have bug that broke the whole software reported in GitHub issues  
<input disabled checked type="checkbox"> open source  

* No idea whether it hates react-router.
* Has some real problems with its internal styling solution which mandated a pretty extensive overhaul, but there's no idea currently when that will be done, or how much work it will be to port to it.
* Sort of seems to allows controls (menu etc) in tables, but not natively it seems; an [external
  component](https://github.com/andela-cdaniel/mui-data-table) seems to do it, or otherwise a bunch of [example
  code](https://github.com/vorlov/material-ui-sortable-table) which runs with errors and a [promise that it will be in MUI in the next release](https://github.com/callemall/material-ui/issues/1352), but no promises or indication when that will drop.
* Essentially single developer, which is not where you want to be in the fickle JS world.

## ANTD

**Components**:

Basics:  
<input disabled checked type="checkbox"> dropdownlist / select  
<input disabled checked type="checkbox"> date picker  
<input disabled checked type="checkbox"> time picker  
<input disabled checked type="checkbox"> tab  
<input disabled checked type="checkbox"> dialog / modal / pop up window  
<input disabled checked type="checkbox"> dropdown menu  
<input disabled checked type="checkbox"> table  
<input disabled checked type="checkbox"> allows controls (menu etc) in tables  
<input disabled type="checkbox"> responsive  
Extra:  
<input disabled type="checkbox"> loading indicator  
<input disabled type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
<input disabled type="checkbox"> chart  
<input disabled checked type="checkbox"> table with sorting, filtering  
<input disabled type="checkbox"> theme: sort of, but underdocumented and a major overhaul is underway.  

**Infrastructure:**

<input disabled checked type="checkbox"> plays nice with react-router  
<input disabled checked type="checkbox"> use ES6 and class syntax  
<input disabled checked type="checkbox"> compatible with React 15.4.0  
<input disabled checked type="checkbox"> actively updated and supported  
<input disabled checked type="checkbox"> should not have bug that broke the whole software reported in GitHub issues  
<input disabled checked type="checkbox"> open source  

* Advocates dva, which is like react-create-app but with strong opinions on combining redux and stuff. Good. Documentation
  of dva is in Chinese. Bad.
* Very few contributors, which is a *major* risk in the volatile javascript world.
* Theming is limited, so the designer who got me pixel-perfect specs is going to be unhappy.
* The majority of discussion/docs is in Chinese, and the UI components default to Chinese. L10n exists but my language isn't supported and how to add new ones
  is loosely documented -- in Chinese.

Despite all this, it's still one of the two main contenders. This should tell you something about the sad state of the
React ecosystem.

## Grommet

**Components**:

Basics:  
<input disabled checked type="checkbox"> dropdownlist / select  
<input disabled checked type="checkbox"> date picker  
<input disabled checked type="checkbox"> time picker  
<input disabled checked type="checkbox"> tab  
<input disabled type="checkbox"> dialog / modal / pop up window  
<input disabled checked type="checkbox"> dropdown menu  
<input disabled checked type="checkbox"> table  
<input disabled checked type="checkbox"> allows controls (menu etc) in tables  
<input disabled checked type="checkbox"> responsive  
Extra:  
<input disabled type="checkbox"> loading indicator  
<input disabled checked type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
<input disabled checked type="checkbox"> table with sorting, filtering  
<input disabled type="checkbox"> theme  

**Infrastructure:**

<input disabled type="checkbox"> plays nice with react-router  
<input disabled checked type="checkbox"> use ES6 and class syntax  
<input disabled checked type="checkbox"> compatible with React 15.4.0  
<input disabled checked type="checkbox"> actively updated and supported  
<input disabled checked type="checkbox"> should not have bug that broke the whole software reported in GitHub issues  
<input disabled checked type="checkbox"> open source  

Themes are supported but no indication on how to develop them, and it talks of needing tools like
[Sketch](http://bohemiancoding.com/sketch/), [Illustrator](http://www.adobe.com/products/illustrator.html),
[Axure](http://www.axure.com) and [Balsamiq](http://www.balsamiq.com). Screw that noise.

This library has the most frustrating project name I've encountered in a long time -- *nearly everything you find on
google has to do with little metal rings*, regardless of extra search terms you put in.

## React-toolbox

**Components**:

Basics:  
<input disabled checked type="checkbox"> dropdownlist / select  
<input disabled checked type="checkbox"> date picker  
<input disabled checked type="checkbox"> time picker  
<input disabled checked type="checkbox"> tab  
<input disabled type="checkbox"> dialog / modal / pop up window  
<input disabled checked type="checkbox"> dropdown menu  
<input disabled checked type="checkbox"> table  
<input disabled checked type="checkbox"> allows controls (menu etc) in tables  
<input disabled checked type="checkbox"> responsive  
Extra:  
<input disabled type="checkbox"> loading indicator  
<input disabled checked type="checkbox"> dropdownlist / select with search/filter function (autocomplete)  
<input disabled checked type="checkbox"> table with sorting, filtering  
<input disabled type="checkbox"> theme  

**Infrastructure:**

<input disabled type="checkbox"> plays nice with react-router  
<input disabled checked type="checkbox"> use ES6 and class syntax  
<input disabled checked type="checkbox"> compatible with React 15.4.0  
<input disabled checked type="checkbox"> actively updated and supported  
<input disabled checked type="checkbox"> should not have bug that broke the whole software reported in GitHub issues  
<input disabled checked type="checkbox"> open source  

Wow, this looks good, and actively maintained. Except that it doesn't like react-router *at all*:

[react-toolbox/react-toolbox#144](https://github.com/react-toolbox/react-toolbox/issues/144)  
[react-toolbox/react-toolbox#851](https://github.com/react-toolbox/react-toolbox/issues/851)  
[react-toolbox/react-toolbox#855](https://github.com/react-toolbox/react-toolbox/issues/855)  
[react-toolbox/react-toolbox#984](https://github.com/react-toolbox/react-toolbox/issues/984)  
[react-toolbox/react-toolbox#1059](https://github.com/react-toolbox/react-toolbox/issues/1059)  

Table is not sortable without an [unmerged pull request](https://github.com/react-toolbox/react-toolbox/pull/1035) or an [unreleased external
component](https://github.com/react-toolbox/react-toolbox/issues/322). Has a [massive structural
change](https://github.com/react-toolbox/react-toolbox/pull/666) looming for over 6 months to address such issues but
that change has
unresolved conflicts and no clear indication of how much a client app would have to change. A boilerplate that's
referenced in the issue that tracks the forever-soon-now release doesn't start. Super.

## Semantic-UI

No date picker? Really? okbyethen.

# What never really were contenders even if you couldn't be blamed for thinking they were

## Bootstrap

First stop was bootstrap. React-bootstrap seems to play nice with react-router, so no issues getting auth0 going. But
bootstrap is mainly just UI layout; it does bugger-all for all the other necessary components (dropdowns, date pickers,
sortable tables), and I'm sure as hell not cobbling together an personal UI library in hopes that it will style
reasonably consistently.

* [Pivotal](http://styleguide.cfapps.io/faq.html): no date picker, no traction
* [Foundation](http://webrafter.com/opensource/react-foundation-apps): is just UI layout, like Bootstrap. Useless.
* [MUIcss](https://www.muicss.com/docs/v1/react/introduction): no datepicker

# Angular to the rescue?

So let's give angular a shot. 5-6 weeks in and React is actively (pun intended) trying to get me depressed and doing a
damn good job of it. At least Angular is supposed to be opinionated and full-stack, right?

**GODDAMN WRONG**

Angular works just fine. I'm following the tutorial and while there's an amount of magic going on under the hood that
scares even a Roby on Rails dev, at least things are *working*, **30 minutes into the tutorial**. Yay!

Except... hey, this is the tutorial for Angular 2. Hmm, I don't suppose that... nope, angular-material is Angular 1
only. OK, whatever, Angular 1 it is. Oh, Angular 1 is *nothing like* Angular 2? Uh, that doesn't bode well. And sure,
angular-2-material exists... sort of, but horribly incomplete. But hey, look what I just found! Mean.io promises an
opinionated *full-stack* framework! And there's even an mean-material! Which, of course, doesn't work, and requires
conflicting versions of packages. It's DLL-hell all over again.
