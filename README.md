[![My Skills](https://skillicons.dev/icons?i=webpack,tailwind)](https://skillicons.dev)
<h1>How to use Webpack5 and TailwindCss</h1>   

<h2>Setting up folder</h2>
<p>Before start make sure you have installed <a href="https://nodejs.org/en">node.js</a><br>
After installing node.js install yarn.<br>
Open up terminal and type "npm install --global yarn" - don't copy quotes. <br>
After installation is complete type "yarn --version" to see what version do you have.</p>

<p>In terminal type mkdir "name of your project" to make new folder.<br>
Then type cd "name of your project" and "yarn init -yp".<br>
If you are using visual studio code just type code . it will automaticly open vscode.<br>
Now open up terminal in vsc by pressing ctrl + ` (Backtick) and select cmd instead powershell.</p>

<p>You should have just "package.json"</p>

<h2>Next step is to add Webpack and other dependencies</h2>
<ol>
  <li>yarn add -D webpack webpack-cli</li>
  <li>yarn add babel-loader @babel/core @babel/preset-env</li>
  <li>yarn add tailwindcss@latest postcss@latest autoprefixer@latest</li>
  <li>yarn add postcss-loader html-webpack-plugin</li>
  <li>yarn add -D style-loader</li>
  <li>yarn add -D css-loader</li>
</ol>

<h2>Setting webpack.config.js</h2>
<p>After installing webpack and dependencies make webpack.config.js file in root of your folder and the following:</p>

```javascript
  const HtmlWebpackPlugin = require('html-webpack-plugin');
  const path = require('path');
  const isProduction = process.env.NODE_ENV === 'production';

  const stylesHandler = 'style-loader';

  const config  = {
    entry: './src/index.js',
    output: {
      path: path.resolve(__dirname, './dist'),
      filename: 'main.js',
      clean: true,
    },
    plugins: [
      new HtmlWebpackPlugin({
      template: 'index.html',
      }),
  ],
      module: {
        rules: [
        {
        test: /\.(js|jsx)$/i,
        loader: 'babel-loader',
      },
      {
        test: /\.css$/i,
        use: [stylesHandler, 'css-loader', 'postcss-loader'],
      },
      {
        test: /\.(eot|svg|ttf|woff|woff2|png|jpg|gif)$/i,
        type: 'asset',
      },
    ],
  },
};

module.exports = () => {
  if (isProduction) {
    config.mode = 'production';
  } else {
    config.mode = 'development';
  }
  return config;
};

```
<p>The next step is to create more files.<br>
Create index.html in root of folder.<br>
Webpack will use that index.html to generate final HTML.<br>
Create folder named "src" and "index.js" in it.<br></p>

<h3>Your project folder should look like this:</h3>

<p>Your project name: <br>
|- node_modules <br>
| - src <br>
  |- index.js <br>
|- index.html <br>
|- package.json <br>
|- webpackconfig.js <br>
|- yarn.lock <br>
</p>

<p>To make sure everything is working great let's writte some code.</p>

<p>index.html</p>

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TailwindCss &amp; WebPack5</title>
</head>
<body>
    <h1>Hello World</h1>
</body>
</html>
```

<p>index.js</p>

```javascript
console.log('Hello world');
```

<p>Update <b>package.json</b> with following commands:</p>
<p>Add a comma after the penultimate curly bracket and paste the following:</p>

```json
"scripts": {
    "build": "webpack --mode=production --node-env=production",
    "build:dev": "webpack --mode=development",
    "build:prod": "webpack --mode=production --node-env=production",
    "watch": "webpack --watch"
  }
```

<p>Now get back to terminal again and run <b>"yarn build:dev"</b> <br>
This command will make <b>"dist" folder</b> and <b>index.html</b> and <b>index.js</b> files in it.<br>
Go to <b>"dist"</b> folder and open <b>index.html</b> in <b>browser.</b> If everthing is ok you should see just like this:
img here</p>

```
yarn build:dev
```
