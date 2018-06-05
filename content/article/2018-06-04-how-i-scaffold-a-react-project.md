---
title: "How I Scaffold a React Project"
date: 2018-06-04T21:40:35-04:00
draft: false
featuredImage: "images/scaffolding.jpg"
categories: ["react", "javascript"]
tags: ["react", "react-native", "javascript"]
author: "Nisarga Patel"
twitter:
  card: "summary"
  site: "@nphacker"
  title: "How I Scaffold a React Project"
  description: "Scaffolding a project is perhaps one of the most important and common things to do during the early development stage. Depending on how a project is set up in the beginning can affect a project's lifecycle and how things are maintained when the codebase starts growing larger."
  image: "https://nisarga.io/images/scaffolding.jpg"
---

Scaffolding a project is perhaps one of the most important and common things to do during the early development stage. Depending on how a project is set up in the beginning can affect a project's lifecycle and how things are maintained when the codebase starts growing larger.

##### Using a boilerplate

Most of the frontend React based projects I do start out by generating a barebones boilerplate using Facebook's excellent and highly popular [`create-react-app`](https://github.com/facebook/create-react-app). For mobile applications I first decide whether or not I need to use any native based modules such as [`react-native-svg`](https://github.com/react-native-community/react-native-svg) or [`react-native-ble-plx`](https://github.com/Polidea/react-native-ble-plx) (for Bluetooth capabilities) and if the answer is no I use [`create-react-native-app`](https://github.com/react-community/create-react-native-app). If I do require native modules then I just use `react-native init` via the react-native-cli, although I may choose to eject out of a create-react-native-app created project later, if I realize that native modules are needed.

##### The `src` directory

The first directory I create if it doesn't already exist is the project root level `src` directory. The purpose of the `src` directory is so that all of the JS or TS code is in one place and easier to see. It's definitely optional but I prefer to have one. The rest of the folders are nested within the `src` directory.

##### The `constants` or `globals` directory

A `constants` directory is useful because it is a good place to easily access globally used constants. For example, if one decides to use Redux to manage state for their project it's a good idea to have all of the constants corresponding to actions in an easily accessible place. 

##### The `components` directory

In the `components` directory I store all of the UI view components, there is little to no frontend logic defined in these components and I try to keep them all extended from `PureComponent` with just a single `render()` method. Although one may opt to use a nested folder per component with an `index.js` file inside specifying the component, I usually go with `ComponentName.js` to avoid ambiguity when editing files in a text editor. 

##### The `containers` directory

In this directory I store all of my logical container components. For an in depth explanation in regards to the differences between presentational and container components refer to [this excellent article by Dan Abramov](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0). Container components do not include any presentational information and are only concerned with *how things work* rather than *how things look*.

##### The `views` directory

The `views` directory contains the screens or the page components for the application. Similar to the `components` directory the components in the `views` directory do not contain any business logic and are only concerned with how the data appears to the user on the screen and are all pure components.

##### The `reducers` directory

This directory contains all of my Redux reducers which define global application state. If state is only used for a particular view I don't mind defining local state in a container, but for things like user account details, or data used throughout the application I use reducers.

##### The `stores` directory (optional)

Since I usually use Redux for state management I only have one store, but if for some reason I do require multiple stores having a `stores` directory is useful.

##### The `util` or `lib` directory

Often times I use a set of useful utility functions throughout multiple applications, perhaps this may be functions for wrapping API calls such that they use an access token or special headers, or utility functions to communicate with `AsyncStorage` on mobile or `localStorage` on web. 

##### The `actions` directory

This is where all of my Redux Action Creators go, I may choose to nest a folder called `async` in this directory to specify asynchronous actions. For async actions I use the standard method which is via the [`redux-thunk`](https://github.com/reduxjs/redux-thunk) middleware.

##### The `navigation` directory

The `navigation` directory is where I put my `react-router` (on web) or `react-navigation` (on mobile) specifications. I usually [integrate my navigation with Redux](https://reactnavigation.org/docs/en/redux-integration.html).

##### The `static` or `assets` directory

The `static` directory is where I put my static assets, this could be icons, fonts, images etc. I usually nest folders within this directory depending on how my application is organized. 

##### The `stylesheets` directory

Although I may define stylesheets within presentational components, I usually like keeping my styles in one place within the `stylesheets` directory.

##### The `hocs` directory (optional)

If I notice that frontend application logic may be repetitive across multiple components I may choose to create a [Higher Order Component](https://reactjs.org/docs/higher-order-components.html). The files in this directory are named `withFunctionalityName.js` where FunctionalityName is the name of what the HOC adds to the component.

##### The `api` directory (optional)

I may also choose to isolate all of the async requests that communicate to an API in their own `api` directory.

##### Conclusion

There are definitely a lot of ways to scaffold a React based application but choosing and defining a standard way and sticking to it can go a long way in ensuring that code stays organized and easy to maintain. If you have any suggestions or comments in regards to how you scaffold your own projects feel free to comment below.

Thanks!