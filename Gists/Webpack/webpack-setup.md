# Webpack

## How to setup webpack in the project:
- npm init -y
- npm install webpack webpack-dev-server@latest webpack-cli --save-dev
- npm install babel-loader babel-core babel-preset-env --save-dev
- npm install sass-loader node-sass css-loader style-loader --save-dev

- npm install html-loader html-webpack-plugin file-loader --save-dev

*//to use jQuery*
npm install jquery --save
In `main.js` add `import 'jquery';`
Add additiona options to `webpack.config.js`

- npm install --save-dev extract-text-webpack-plugin  *// not working for webpack > 4 yet*

- create `webpack.config.js`

## Description:
- babel, scss - complies into `bundle.js`
- creates `img` folder with images inside 'dist' folder
- creates `.html` file in the dist folder and connects `bundle.js` to it

## webpack.config.js
```js
const path = require('path');
const webpack = require('webpack');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
    entry: './src/js/main.js',
    output: {
        path: path.resolve(__dirname, 'dist'),
        filename: 'bundle.js'
    },
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
            },
            {
                test: /\.(html)$/,
                use: [{
                    loader: 'html-loader',
                    options: {
                        minimize: true,
                        removeComments: false,
                        collapseWhitespace: false
                    }
                }],
            },
            {
                test: /\.(jpg|png)$/,
                use: [
                    {
                        loader: 'file-loader',
                        options: {
                            name: '[name].[ext]',
                            outputPath: 'img/',
                            publicPath: 'img/'
                        }
                    }
                ]
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
            filename: 'index.html',
            template: 'src/index.html'
        }),
        new webpack.ProvidePlugin({
            $: 'jquery',
            jQuery: 'jquery'
        })
    ]
};
```