# notetaker

> A realtime synced notebook

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## Setting up Deploy to Github
### Step 1: Install the node module
npm install --save-dev vue-gh-pages

## Step 2: Add the following to the scripts section in your package.json:
```"deploy": "node ./node_modules/vue-gh-pages/index.js"```

## Step 3: Add homepage field to your package.json file:
```"homepage": "https://github.com/myusername/my-app"```

## Step 4: Now when you're ready to push to github, run:
```npm run deploy```
This will create an optimized production build of your project ready for github pages.

## Debug Deployment Errors
```git config --system core.longpaths true```