Coding editor: Visual Studio

##### Workflow
directory:


```
dist
    bundle.js
.html
src
    js
        index.jsx
    css
    sass
webpack.config
package.json
```



###### npm config

Terminal:   
    Go to the project directory, run **npm init**. Initialize package.json file

Package.json  
    add "run commands" \(including watch [for npm run watch], start...\) into the script section. \[see the github repository\]  

T:  
    add webpack, run **npm i webpack --save-dev**  
    add Babel, run **npm i babel?**  

P:  
    add Babel presets  

Webpack.config  
    add a Babel loader rule \(remember to exclude node modules, thereby speeding up the loader sinigicantly\)

.html
    within the body tag add the following statement:
    `<script src="dist/bundle.js" type="spreedsheet">`
    Note: bundle.js 是在.html的相对路径

js
    create index.jsx - entry of webpack
    
**Finally,** we can run npm run watch to start webpack and also keep an eye on the change
##### Ref

1. [Webpack Configuration for Using Bootstrap in React](https://medium.com/@vladbezden/webpack-configuration-for-using-bootstrap-in-react-a6ef2dfa1d95)  
    [configure .babelrc](https://babeljs.io/docs/usage/babelrc/)

2. [How to include Bootstrap in your project with Webpack](https://stevenwestmoreland.com/2018/01/how-to-include-bootstrap-in-your-project-with-webpack.html)

3. [Setting Up Webpack for Bootstrap 4 and Font Awesome](https://medium.com/@estherfalayi/setting-up-webpack-for-bootstrap-4-and-font-awesome-eb276e04aaeb)  
    要把bootstrap.min.js, jquery.min.js, and tether.min.js 放到project内，这里我放在了index.jsx所在的js folder 里

4. [Installing Bootstrap 4 Tutorial](https://coursetro.com/posts/design/72/Installing-Bootstrap-4-Tutorial)



