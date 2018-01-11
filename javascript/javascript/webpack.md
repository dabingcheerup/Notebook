[Webpack](https://webpack.js.org/guides/getting-started/#using-a-configuration) is used to compile JS modules.
?what are JS modules 

Resource:
1.  [Introduction](https://survivejs.com/webpack/introduction/)

##Error
###(which project)Pomodoro timer_todolist
####(Problem need to solve)Try to use jquery UI so that items are sortable
#####(Specific error)ERROR Uncaught TypeError: $(...).sortable is not a function
**solution**: [use jquery-ui-bundle](https://stackoverflow.com/questions/44932576/jquery-ui-sortable-is-not-a-function-with-webpack) [2](https://knpuniversity.com/screencast/javascript-webpack/watch-require-jquery)
####add an external js file to bundle.js
#####*ERROR in Entry module not found: Error: Can’t resolve ‘babel-loader’ in ’/Users/…*
**solution:** run yarn first 
step1: in entry.js file which is index.js in this project, code: import './externalJSname';
step2: yarn
step3: npx webpack

####add repository
npm add github url
[guide to npm beginners](https://www.sitepoint.com/beginners-guide-node-package-manager/)