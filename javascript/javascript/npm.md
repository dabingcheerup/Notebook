#### Workflow

###### directory:

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

##### npm config

Terminal:  
    
    Go to the project directory, run **npm init**. Initialize package.json file

Package.json  
    
    add "run commands" \(including watch \[for npm run watch\], start...\) into the script section. \[see the github repository\]

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

##### Create a simple react app

install react in npm \(create an react app?\)  
index.jsx - create react components

```
import React from "react";
export default class App extends React.Component {
  render() {
      return <p> Hello React!</p>;
  }
}
```

App.jsx - define render function

```
import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
ReactDOM.render(<App />, document.getElementById("content"));
```

npm run watch

##### Bootstrap config

Terminal:

    1. npm install bootstrap
       add import 'bootstrap' to index.jsx
    2. npm install jquery -D
    3. npm install popper.js -D  
       add plugin into webpack.config.js file module part  
       Note: Bootstrap needs jquery, popper.js and t  
       must copy and add bootstrap.min.js, jquery.min.js, and tether.min.js from node\_module folder to js folder

   install dependencies to webpack

    4. npm install css-loader sass-loader file-loader url-loader node-sass extract-text-webpack-plugin transfer-webpack-plugin image-webpack-loader jquery --save-dev
    5. set rules in webpack.config
    
######Ref
[重要create-react-app: importing Bootstrap 3 / 4.0 with jQuery cleanly (Node.js)](http://blog.oddicles.org/create-react-app-importing-bootstrap-jquery-cleanly-node-js/)
[Webpack Configuration for Using Bootstrap in React](https://medium.com/@vladbezden/webpack-configuration-for-using-bootstrap-in-react-a6ef2dfa1d95)

##### Font-awesome and @fontawesome

Terminal:  
    
    Install font-awesome-loader and font-awesome:  
    1. npm install font-awesome --save  
    2. npm install font-awesome-loader --save-dev

    fontawesome integrates with react
    1. npm install --save @fortawesome/fontawesome
    2. npm install --save @fortawesome/react-fontawesome
    3. npm install @fortawesome/fontawesome-free-brands, @fortawesome/fontawesome-free-solid
    
在react component中使用@fortawesome
    
```
// App.jsx
import React from "react";
import ReactDOM from "react-dom";
import { Button } from "react-bootstrap";
import FontAwesomeIcon from "@fortawesome/react-fontawesome";

export default class App extends React.Component {
  render() {
    return (
      <div>
        <FontAwesomeIcon icon="check-square" />
        Favorite beverage: <FontAwesomeIcon icon="coffee" />
      </div>
    );
  }
}
    
```

在html中使用@fortawesome
    1. import dependencies (fontawesome, brands, solid)
    2. automatic svg replacement 就是自动找到tag <i>替换成svg
    3. 在HTML中 fas代表的是fontawesome-free-brands中的svg


```
//index.jsx

import React from "react";
import ReactDOM from "react-dom";
import App from "./App";
import "bootstrap";
import "bootstrap/dist/css/bootstrap.min.css";
import "font-awesome/css/font-awesome.min.css";
import fontawesome from "@fortawesome/fontawesome";
import FontAwesomeIcon from "@fortawesome/react-fontawesome";
import brands from "@fortawesome/fontawesome-free-brands";
import {
  faWrench,
  faGraduationCap,
  faFile,
  faBriefcase,
  faLanguage
} from "@fortawesome/fontawesome-free-solid";

fontawesome.library.add(
  brands,
  faGraduationCap,
  faWrench,
  faFile,
  faBriefcase,
  faLanguage
);
//automatic svg replacement
fontawesome.dom.i2svg();

//ReactDOM.render(<App />, document.getElementById("edu"));

```
######Ref
[@fortawesome/react-fontawesome in npm](https://www.npmjs.com/package/@fortawesome/react-fontawesome)
[SVG with JavaScript ](https://fontawesome.com/how-to-use/svg-with-js)
[FontAwesome npm Installation And Basic Usage](https://code.luasoftware.com/tutorials/npm/fontawesome-npm-installation-and-setup/#automatic-svg-replacement-npm)
[fontawesome.com](https://fontawesome.com/)

#####[devicon](http://konpa.github.io/devicon/)
直接在HTML 通过external link使用

#####compile scss to css
######Ref
[Watch and Compile Sass in Five Quick Steps](https://webdesign.tutsplus.com/tutorials/watch-and-compile-sass-in-five-quick-steps--cms-28275)

#####Ref
Github
[GitHub Pages sites Setup](https://help.github.com/articles/user-organization-and-project-pages/)
[Introduction to Webpack: Entry, Output, Loaders, and Plugins](https://css-tricks.com/introduction-webpack-entry-output-loaders-plugins/)
[怎么预览 GitHub 项目里的网页或 Demo？](https://www.zhihu.com/question/24156818)

npm
[How to Use npm as a Build Tool](https://www.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/)
    







