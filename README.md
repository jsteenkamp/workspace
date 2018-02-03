# React Workspace Components

Prototyping with [React](http://facebook.github.io/react/), [Redux](http://redux.js.org/), and [GraphQL](http://graphql.org/) using [Apollo](http://dev.apollodata.com/).

## Tooling

We use [Yarn](https://yarnpkg.com/), [babel](https://babeljs.io/), and [webpack](https://webpack.js.org/).

## Structure

`src` - application source files that are complied by [babel](https://babeljs.io/) and build by [webpack](https://webpack.js.org/).

`dist` - deployment output. The development and production servers use files located in `dist`. Production built application files are saved in `dist/build`. Express server mappings serve static content from `build` and `public` directories on root path. The server API and processing modules are in the `dist/server` directory

`_assets` - build assets that are not deployed. The i18n messages are parsed and saved in `_assets/locales/data.json` when running `yarn intl`. This file is required for building the application and is bundled in the build output. Typically this file will be pulled from a separate repo used to manage translations. We do not load locales asynchronously so the locales data does not have to be deployed.

## Redux

Create FSAs using [redux-actions](https://github.com/acdlite/redux-actions).

Ensure redux data is immutable using [immutability-helper](https://github.com/kolodny/immutability-helper).

## GraphQL
 
[Apollo React Client](http://dev.apollodata.com/react/) and [Apollo Server](http://dev.apollodata.com/tools/graphql-server/index.html) with [Express](https://expressjs.com/)

For development [GraphiQL](https://github.com/graphql/graphiql) is available at `http://localhost:3000/graphiql`

## Routing

[react-router (v4)](https://reacttraining.com/react-router/)

## CSS

No Sass/SCSS pre-processor, use `styled-components`.

[Forget Normalize/Reset](http://jaydenseric.com/blog/forget-normalize-or-resets-lay-your-own-css-foundation) and use `base.css` that strips and adds styles where it makes sense to minimize the amount of declarations and overrides you will have to make later. 

Web browsers do have sane albeit ugly defaults. It does not make sense to reset everything.

## API

The application API allows us to use templates to format and map data to views and components and use plugins to render 3rd party components in views.
 
The application api methods are defined in `/app/api`. Typically these will methods will result in application state updates.

Developers can add `modules` in `/app/modules` which are imported and used by application components.

## Browsers

Test on OSX with Chrome, Chrome Canary, Firefox, Firefox Developer Edition (Canary), Safari, Safari Technology Preview (Canary), Webkit Nightly. 
 
Test on Windows 7 with Microsoft Internet Explorer 11.

# Issues

- Safari 10.1 does not render [flexbox with 100% height](https://bugs.webkit.org/show_bug.cgi?id=137730) correctly. This is known issue and fixed in Safari 10.2 TP and Webkit Nightly.
- Safari 10.1 and 10.2 TP do not display Context Menu submenu overlays fully although containers are the correct size.
- Upgrade from Webpack 2.5.1 to 2.6.0 breaks build in IE11 (Windows 7), seems to be an issue around promises.