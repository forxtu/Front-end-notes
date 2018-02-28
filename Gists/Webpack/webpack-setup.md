# Webpack

How to setup webpack in the project:

- npm init -y *//create package.json*
- npm install webpack webpack-dev-server webpack-cli --save-dev
- npm install babel-loader babel-core babel-preset-env --save-dev
- npm install css-loader style-loader --save-dev
- npm install sass-loader node-sass --save-dev

- create `webpack.config.js`
Babel, scss. All complies into 1 bundle.js file.
Source map for styles - display .scss path in the dev tools
```js
module.exports = {
    entry: ['./js/main.js', './scss/main.scss'],
    output: {
        path: __dirname + "/dist",
        filename: './bundle.js'
    },
    watch: true,
    devtool: "source-map",
    module: {
        rules: [
            {
                test: /\.scss$/,
                use: [
                    { loader: "style-loader" },
                    {
                        loader: "css-loader",
                        options: { sourceMap: true }
                    },
                    {
                        loader: "sass-loader",
                        options: { sourceMap: true }
                    }
                ]
            },
            {
                test: /\.js$/,
                exclude: /(node_modules|bower_components)/,
                use: {
                    loader: 'babel-loader',
                    options: {
                        presets: ['env']
                    }
                }
            }
        ]
    }
};
```
- import bundle.js file into 'index'
- create .js and .scss files and code!