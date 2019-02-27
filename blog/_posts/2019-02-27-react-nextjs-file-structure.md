---
layout: post
title:  "React/Next.js File structure"
date:   2019-02-27
categories: react
excerpt: "How I structure directories, folders, and files of my React/Next.js projects."
---

Have you heard of [Next.js](https://github.com/zeit/next.js) yet? It's an
awesome framework for React that bring server-side rendering, automatic code
splitting, and much more.

But just like React, Next.js provides you with a lot of freedom and flexibility
for where to put your files. Great for beginners. But as someone coming from
Ruby on Rails and having become fond of its rigid file structure, one of my
first search queries was for "best React file structure".

Combining my own experiences and the best practices I found, here is what I have
been using:

```
pages/
+-- profiles/
    +-- ProfilesIndexPage.js
    +-- ProfilesShowPage.js
    +-- ProfilesEditPage.js
    +-- sections/
        +-- ProjectCardCollection.js
        +-- ProjectCard.js
+-- projects/
    +-- ProjectsNewPage.js
    +-- ProjectsShowPage.js
    +-- ProjectsEditPage.js
+-- sessions/
    +-- SessionsNewPage.js
+-- errors/
    +-- NotFoundErrorPage.js
    +-- ServerErrorPage.js

layouts/
+-- ApplicationLayout.js
+-- LandingLayout.js

blocks/
+-- Button.js
+-- Row.js
+-- Column.js

components/
+-- ProfilePicture.js
+-- ProjectCard.js

hocs/
+-- withLayout.js

helpers/
+-- getColor.js
+-- getComponentDisplayName.js
+-- getContext.js

config/
+-- routes.js
+-- server.js
```

# File Structure Explained

## Pages

Each page reflects one route in the React app. For example, we may have a
`/projects/:id` route with the purpose of displaying a single project.
Then we have a corresponding `ProjectsShowPage.js` file. Or a `/projects/` route
to show a list of all projects. Then we have a `ProjectsIndexPage.js` file for
that.

These pages are grouped into subdirectories by their resource (`projects`,
`profiles`, `sessions`) to keep the number of items in the `pages` directory
manageable.

## Layouts

Layouts are reuseable templates for our pages, such as ApplicationLayout and
ProjectLayout. The layouts are responsible for content that appears on many
pages, such as navigation menus.

I was inspired to use layouts by [@dominik.t](https://medium.com/@dominik.t/complete-guide-to-structuring-large-react-redux-apps-bc91e2136d4c).


## Blocks

Blocks are generic components used throughout the application. They could be a
button or a layout element. These "templates" are very generic and I often copy
them from one project into the other. It's sort of my way of enhancing whatever
CSS framework I use (such as Material).

## Components

Components are app-specific components used throughout the application. It could
be a preview card for a project. Or a particular form that is used in multiple
places. Unlike blocks, components are highly specific to my application. They
require objects to be passed in or have dependencies on other app-specific
pieces.

## HOCs (higher-order components)

This is where I place my higher-order components. I'm still learning how to get
the full potential out of HOCs, but one clear application has already emerged
 I use the `withLayout.js` HOC to wrap my pages into a layout. Like so:

```javascript
// pages/projects/ProjectsNewPage.js

class ProjectsNewPage extends Component {
  // ...
}

export default withLayout(ProjectsNewPage, ApplicationLayout)
```

[Read more about HOCs here](https://reactjs.org/docs/higher-order-components.html).

## Helpers

Helpers are pure Javascript files that fulfill a single, specific purpose. For
example, when using Material, I always have a `getColor.js` helper that allows me
to dynamically retrieve the hex value of a Material color with a given shade.

## Config

Any configuration files go here, such as route definitions and server settings.


## `.js` or `.jsx`?
Very controversial question. See [this long discussion on
airbnb's style guide](https://github.com/airbnb/javascript/pull/985). And [this
one on the React repo](https://github.com/facebook/react/issues/3582).  

Some recommend only using `.js` for pure Javascript and using `.jsx` for
anything React. The distinction can be helpful when you're searching for files
in your app (if it's a component, you can search for anything ending with `.jsx`
as opposed to `.js`).  

In my opinion, though, using `.jsx` is not worth the hassle. Most of your files
will end up being `.jsx`, so the benefit you derive from distinguishing it from
the pure Javascript files in your `helpers` and `config` directory is small.
Plus, [Facebook itself recommends using `.js`](https://github.com/facebook/create-react-app/releases/tag/v0.4.1).

# Still Learning!

I'm still learning every day. My ideal directory structure may evolve over time,
especially with the size of the projects I am working on. So far, the above has
served me well :)
