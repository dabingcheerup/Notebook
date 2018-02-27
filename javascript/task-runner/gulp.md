#####Error
1. [Can not GET on http://localhost:3000](https://stackoverflow.com/questions/43203637/cannot-get-on-http-localhost3000/43228030)
    
```
gulp.task("serve", ["sass"], function() {
  browserSync.init({
    server: {
      baseDir: "src",
      index: "resume.html"
    }
  });
```


