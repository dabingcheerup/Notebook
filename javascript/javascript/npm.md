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

npm run

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

##### Font-awesome and @fontawesome

Terminal:  
    Install font-awesome-loader and font-awesome:  
    1. npm install font-awesome --save  
    2. npm install font-awesome-loader --save-dev

    fontawesome integrates with react
    1. npm install --save @fortawesome/fontawesome
    2. npm install --save @fortawesome/react-fontawesome
    3. npm install @fortawesome/fontawesome-free-brands, @fortawesome/fontawesome-free-solid
    
    在react component中使用font-awesome
    ```
    App.jsx
    import React from "react";
 import ReactDOM from "react-dom";	 import ReactDOM from "react-dom";
 import { Button } from "react-bootstrap";	 import { Button } from "react-bootstrap";
+import FontAwesomeIcon from "@fortawesome/react-fontawesome";
 	 
 export default class App extends React.Component {	 export default class App extends React.Component {
   render() {	   render() {
     return (	     return (
-      <FontAwesome	+      <div>
-        className="super-crazy-colors"	+        <FontAwesomeIcon icon="check-square" />
-        name="rocket"	+        Favorite beverage: <FontAwesomeIcon icon="coffee" />
-        size="2x"	+      </div>
-        spin	
-        sytlestyle={{ textShadow: "0 1px 0 rgba(0, 0, 0, 0.1)" }}	
-      />	
     );	     );
   }	   }
 }	 }
    ```
    







