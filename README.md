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
