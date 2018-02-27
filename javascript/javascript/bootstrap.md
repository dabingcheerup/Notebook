#####Installation
######Ref
1. [Installing Bootstrap 4 Tutorial](https://coursetro.com/posts/design/72/Installing-Bootstrap-4-Tutorial)
    Errors and Solutions that I met when I tried to install bootstrap
    1) jQuery not uploaded diy: npm install jquery --save
    2) Popper not installed: npm install popper.js --save
    3) gulpfile.js node_modules/popper.js/dist/umd/popper.min.js not from node_modules/popper.js/dist/popper.min.js as this gives the unexpected token error in chrome.
    4) Gulp not working: 
    npm install -g minimatch (Enter) 
    npm install -g graceful-fs (Enter)
    npm link gulp (Enter)
    
    I also had to restart my computer after installing node.js and again for Git Bash
    gulp then works as it does in your demonstration.