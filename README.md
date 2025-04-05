# Bootstrap Webpack Demo

![Static Badge](https://img.shields.io/badge/Bootstrap-5.3.5-blue)

This repo demonstrates how to use [Webpack](https://webpack.js.org/) to bundle, compile and minify JavaScript, SCSS, images, and fonts, while optimising the output for performance. It uses various loaders and plugins to process files and generate the final build:

- [**CSS Minimizer Webpack Plugin**](https://webpack.js.org/plugins/css-minimizer-webpack-plugin/): Uses [CSSNANO](https://cssnano.github.io/cssnano/) to minimise the CSS output, reducing file size and improving page load times.
- [**PostCSS Preset Env**](https://github.com/csstools/postcss-plugins/tree/main/plugin-packs/postcss-preset-env): Uses [Autoprefixer](https://github.com/postcss/autoprefixer) to add vendor prefixes and ensure compatibility with older browsers.
- [**PurgeCSS**](https://purgecss.com/): Analyses your content and your CSS files. Then it matches the selectors used in your files with the one in your content files. It removes unused selectors from your CSS, resulting in smaller CSS files.
- [**Babel Preset Env**](https://babeljs.io/docs/babel-preset-env): Transpiles ES6+ JavaScript for cross-browser compatibility while allowing the use of modern JavaScript features.
- [**Webpack Dev Server**](https://webpack.js.org/configuration/dev-server/): Serves files from the output directory with live reloading for development workflows.

## Requirements

- A supported LTS version of [Node.js](https://nodejs.org/en)
- [Node Version Manager](https://github.com/nvm-sh/nvm) (optional)
- [Docker](https://www.docker.com/) (optional)

## Get started

You can run on your local host, or in a Docker container:

### On your host

1. Install Node, preferably using `nvm`. The version is set in the `.nvmrc` file and is typically the latest LTS release codename.

   ```shell
   nvm install
   ```

2. Install the Node package dependencies from [npm](https://www.npmjs.com/):

   ```shell
   npm install
   ```

### Using Docker

1. Build the image

   ```shell
   docker build -t bootstrap-webpack:latest .
   ```

2. Run the container

   ```shell
   docker run -p 8000:8000 bootstrap-webpack:latest
   ```

## How to

### Use Bootstrap components

The `main.scss` file at `/src/scss` is highly selective about which `components` are imported in order to keep distributon file sizes small.

By default, the following components are imported, because they are used in the [starter template](https://github.com/twbs/examples/tree/main/starter/):

- [Buttons](https://getbootstrap.com/docs/5.3/components/buttons/)
- [Dropdown](https://getbootstrap.com/docs/5.3/components/dropdowns/)
- [Navbar](https://getbootstrap.com/docs/5.3/components/navbar/)
- [Navs](https://getbootstrap.com/docs/5.3/components/navs-tabs/)

Simply uncomment any other components in `main.scss` that you need to use.

The same approach applies to JS; the `main.mjs` file at `/src/js` only imports JS for the components being used:

- [Buttons](https://getbootstrap.com/docs/5.3/components/buttons/)
- [Collapse](https://getbootstrap.com/docs/5.3/components/collapse/)
- [Dropdown](https://getbootstrap.com/docs/5.3/components/dropdowns/)

For comparison (using Bootstrap v5.3.5):

| Asset           | Size (KB) |
| --------------- | --------- |
| Precompiled CSS | 232       |
| Selective CSS   | 22 (-91%) |
| Precompiled JS  | 61        |
| Selective JS    | 42 (-31%) |

### Format source code

Use [Prettier](https://prettier.io/), an opinionated code formatter, for consistency.

To check formatting (without changing):

```shell
npm run format:check
```

To reformat files:

```shell
npm run format:fix
```

### Lint source code

Use [ESLint](https://eslint.org/) to statically analyse your code to quickly find problems.

To check for issues:

```shell
npm run lint:check
```

To attempt to automatically fix issues:

```shell
npm run lint:fix
```

### Build assets

Use [Webpack](https://webpack.js.org/) loaders and plugins to output CSS, JS, fonts and images to `./dist`:

```shell
npm run build
```

### Watch changes

Rebuild distribution assets automatically when source is changed:

```shell
npm run watch
```

### Run dev server

Start a simple web server with live reloading:

```shell
npm start
```

Go to <http://localhost:8000>

### Upgrade dependencies

Use [npm-check-updates](https://www.npmjs.com/package/npm-check-updates) to upgrade Node package dependencies (such as [bootstrap](https://www.npmjs.com/package/bootstrap)):

```shell
npm run upgrade:latest
```

If you want to be more cautious you can apply only minor or patch level upgrades:

```shell
npm run upgrade:minor
```

```shell
npm run upgrade:patch
```
