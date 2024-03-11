[![My Skills](https://skillicons.dev/icons?i=webpack,tailwind)](https://skillicons.dev)

# How to use tailwind with webpack

Before start make sure you have installed **node.js** and **yarn**  
Download **node.js** [here](https://nodejs.org/en)  
After installing **node.js** install **yarn**  
Open up **terminal** and type **"npm install --global yarn"**  
After installation is complete type **"yarn --version"** to see what version do you have  

```
npm install --global yarn
```

```
yarn --version
```

In terminal type **mkdir name of your project** to make new folder then **cd name of your project**  
Type **yarn init -yp**  
If you are using visual studio code just type code . it will automaticly open vscode   
Now open up terminal in vsc by pressing **ctrl + `** (backtack) and select **cmd** instead **powershell**  

```
mkdir project name
```

```
cd project name
```

```
yarn init -yp
```
Now you should have file named **package.json** in your project.

## Installing Webpack and other dependencies

In terminal type this commands:
```
yarn add -D webpack webpack-cli
```
```
yarn add babel-loader @babel/core @babel/preset-env
```
```
yarn add tailwindcss@latest postcss@latest autoprefixer@latest
```
```
yarn add postcss-loader html-webpack-plugin
```
```
yarn add -D style-loader
```
```
yarn add -D css-loader	
```
After installing **webpack** and **dependencies** make **webpack.config.js** file in root of your folder and the following:

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

## Creating more files

Create **index.html** in root of folder.  
[!NOTE] Webpack will use that index.html to generate final HTML.  
Create folder named **"src"** and **"index.js"** in it.  

Your project folder should look like this:

[!project structure](https://github.com/[adnancodes29]/[TailwindCss-and-WebPack5]/blob/[main]/images/folder-structure-1.jpg?raw=true)

To make everything is working great in **src/index.js** type **"alert("Hello World");"** and in **index.html** **Hello World**

Update **package.json** with following commands:  
Add a **comma** after the **penultimate curly bracket** and paste the following:  
To make everything is working great in **src/index.js** type **"alert("Hello World");"** and in **index.html** **Hello World**

Update **package.json** with following commands:  
Add a **comma** after the **penultimate curly bracket** and paste the following:

```javascript
"scripts": {
    "build": "webpack --mode=production --node-env=production",
    "build:dev": "webpack --mode=development",
    "build:prod": "webpack --mode=production --node-env=production",
    "watch": "webpack --watch"
  }
```

Now get back to terminal againg and run **yarn build:dev**  
This command will make **dist** folder and **index.html** and **index.js** files in it.  
Go to **dist** folder and open **index.html** in **browser**.  
If everthing is ok you should see just like this:  

Now get back to terminal againg and run **yarn build:dev**  
This command will make **dist** folder and **index.html** and **index.js** files in it.  
Go to **dist** folder and open **index.html** in **browser**.  
If everthing is ok you should see just like this:

```
yarn build:dev
```

img here



Create **"postcss.config.js"** on the root directory and add the following: 

```javascript
module.exports = {
  plugins: [
    ['tailwindcss'],
    ['autoprefixer'],
  ],
};
```

Again back to terminal and run next command **yarn tailwindcss init**. This will generate a file called **tailwind.config.js**, open it and add the following:

```
yarn tailwindcss init

```
```javascript
module.exports = {
  purge: [
    './*.html',
    './src/**/*.js'
  ],
  darkMode: false, // or 'media' or 'class'
  theme: {
    extend: {},
  },
  variants: {
    extend: {},
  },
  plugins: [],
}
```

Create **style.css** file in **src** folder and add the following:
```
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

Now we can use **tailwindcss**. To test this we can add next **class** to our **body tag**.

> [!NOTE]
> Delete alert function from src/index.js to stop annoying alert and import style.css just like this:

```javascript
import './style.css'
```
 

