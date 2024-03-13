[![My Skills](https://skillicons.dev/icons?i=webpack,tailwind)](https://skillicons.dev)

# Intro

### What is TailwindCss?
Tailwind CSS is a utility-first CSS framework designed to enable users to create applications faster and easier. You can use utility classes to control the layout, color, spacing, typography, shadows, and more to create a completely custom component design — without leaving your HTML or writing a single line of custom CSS.

### What is Webpack5
Webpack is a module bundler for JavaScript applications. It processes your application’s modules and packages them into one or more bundles, often a single bundle.js file, optimizing loading time for browsers.

## How to use TailwindCss with Webpack5

Before start make sure you have installed **node.js** and **yarn**  
Download **node.js** [here](https://nodejs.org/en)  
After installing **node.js** install **yarn**  
Open up **CMD** on **Windows**, **Terminal** on **Mac** and type **"npm install --global yarn"**  
After installation is complete type **"yarn --version"** to see what version do you have.
<br>

```
npm install --global yarn
```

```
yarn --version
```
<br>

## Create folder structure

In **CMD** or **Terminal** run **mkdir name of your project** to make new folder  
To open that folder run **cd name of your project**  
Type **yarn init -yp**  
If you are using visual studio code just type code . it will automaticly open vscode   
Now open up built-in terminal in vscode by pressing **ctrl/cmd + `** (Backtack)

```
mkdir project name
```

```
cd project name
```

```
yarn init -yp
```
> [!NOTE]
> Now you should have file named **package.json** in your project.
<br>

![package-json](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/1e0bffaf-1055-4e45-9954-9fb395a2c206)

## Installing Webpack5 and other Dependencies

In  **Terminal** type this commands:

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

<br>

>[!IMPORTANT]
>After installing **Webpack5** and **Dependencies** make **webpack.config.js** file in root of your folder and the following:

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

>[!IMPORTANT]
>Create **index.html** in root of folder.

<br>

> [!NOTE]
> Webpack will use that index.html to generate final HTML.  
Create folder named **"src"** and **"index.js"** in it.  

Your project folder should look like this:

![folder-structure-1](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/ba8e6597-0d0b-418a-b7cf-9194b826daed)

To make everything is working great in **src/index.js** type **:
```javascript
alert("Hello World");
```
and in **src/index.html**:

```html
<h1>Hello World</h1>
```

> [!NOTE]
> Update **package.json** with following commands:

>[!IMPORTANT]
>Add a **comma** after the **penultimate curly bracket** and paste the following:  

```javascript
"scripts": {
    "build": "webpack --mode=production --node-env=production",
    "build:dev": "webpack --mode=development",
    "build:prod": "webpack --mode=production --node-env=production",
    "watch": "webpack --watch"
  }
```

![package-json](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/0e66e67c-2505-441a-9f0b-c663b272e594)

Now run this command:

```
yarn build:dev
```

> [!NOTE]
> This command will make **dist** folder with **index.html** and **index.js** files in it.
> Go to **dist** folder and open **index.html** in **browser**.   

If everthing is ok you should see just like this: 

![first-run](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/64098568-9825-401f-9f57-55fa25f42d40)

>[!IMPORTANT]
>Create **"postcss.config.js"** on the root directory and add the following: 

```javascript
module.exports = {
  plugins: [
    ['tailwindcss'],
    ['autoprefixer'],
  ],
};
```

![postconfigcss](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/5c5e5356-2db3-4532-ac1d-dcc8929b38d5)

>[!IMPORTANT]
>Again back to terminal and run next command **yarn tailwindcss init**.

```
yarn tailwindcss init

```
>[!NOTE]
>This will generate a file called **tailwind.config.js**, open it and add the following:

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

![tailwindcss-config](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/22d4c746-c5da-412e-9999-19b5639e7733)

>[!IMPORTANT]
>Create **style.css** file in **src** folder and add the following:
>
```
@import "tailwindcss/base";
@import "tailwindcss/components";
@import "tailwindcss/utilities";
```

![style css](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/077dd613-72fb-4538-8fcc-2a09fc68eda8)

> [!NOTE]
> Delete alert function from src/index.js to stop annoying alert and import style.css just like this:

```javascript
import './style.css'
```
![import-styles](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/c650416f-75f5-48d4-aeeb-3eabb16ac74c)

>[!IMPORTANT]
>Add following in **index.html** in root of the folder:

```html
<body class="bg-gray-800 h-screen flex justify-center items-center">
    <h1 class="text-white text-5xl">Hello World</h1>
</body>
```
>[!IMPORTANT]
>Run finall command: 

```
yarn watch
```

Now we can use **TailwindCss** with **Webpack5** 😎  

![final (2)](https://github.com/adnancodes29/TailwindCss-and-WebPack5/assets/162288583/58d41bff-1c49-4c2c-8624-5b1943fe1ff8)



 

