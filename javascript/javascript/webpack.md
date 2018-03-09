[Webpack](https://webpack.js.org/guides/getting-started/#using-a-configuration) is used to compile JS modules.  
?what are JS modules

Resource:  
1.  [Introduction](https://survivejs.com/webpack/introduction/)

##### Error


```

 \(which project\)Pomodoro timer\_todolist

\(Problem need to solve\)Try to use jquery UI so that items are sortable

 \(Specific error\)ERROR Uncaught TypeError: $\(...\).sortable is not a function

solution: [use jquery-ui-bundle](https://stackoverflow.com/questions/44932576/jquery-ui-sortable-is-not-a-function-with-webpack) [2](https://knpuniversity.com/screencast/javascript-webpack/watch-require-jquery)

```


```
Error: Invalid configuration object. Webpack has been initialised using a configuration object that does not match the API schema.
 - configuration.module has an unknown property 'loaders'.
 意思在webpack.config.js的module里缺少loaders的property。

原因是新版本的webpack[把loader改名为rule](http://michelleliu.io/debug/webpack-error-configuration-module-has-an-unknown-property-preloaders)
```


```
Warning: [in asset size limit](https://github.com/nuxt/nuxt.js/issues/823): The following asset(s) exceed the recommended size limit (244 KiB).
This can impact web performance.
Assets:
  bundle.js (414 KiB)
  bundle.map.js (1.12 MiB)
  
  
```


```
WARNING [in entrypoint size limit](https://github.com/webpack/webpack/issues/3486): The following entrypoint(s) combined asset size exceeds therecommended limit (244 KiB). This can impact web performance.
Entrypoints:
  main (1.52 MiB)
      bundle.js
      bundle.map.js

WARNING in webpack performance recommendations:
You can limit the size of your bundles by using import() or require.ensure to lazy load some parts of your application.
```






#### add an external js file to bundle.js

##### _ERROR in Entry module not found: Error: Can’t resolve ‘babel-loader’ in ’/Users/…_

**solution:** run yarn first   
step1: in entry.js file which is index.js in this project, code: import './externalJSname';  
step2: yarn  
step3: npx webpack

#### add repository

npm add github url  
[guide to npm beginners](https://www.sitepoint.com/beginners-guide-node-package-manager/)





