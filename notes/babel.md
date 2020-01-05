## Babel

[How to run Node.js app with ES6 features enabled?](https://stackoverflow.com/questions/28782656/how-to-run-node-js-app-with-es6-features-enabled)

1st,
`npm i -D babel-cli babel-preset-es2015`

2nd,
add script to `package.json`
`"start": "babel-node --presets es2015 src/index.js"`

3rd,
optional build script
`"build": "babel --presets es2015 -d <destination folder> <starting folder>"`
example:
`"build": "babel --presets es2015 -d lib/ src"`
