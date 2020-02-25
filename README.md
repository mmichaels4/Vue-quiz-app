# quiz_app

##
App was originally created following this tutorial: https://www.youtube.com/watch?v=4deVCNJq3qc&t=2133s
Although she gives setep-by-step instructions, I tried to not follow them entirely. 
Some major areas of difference include:
* Adding a final score page
* Adding a footer
* A more efficient method of shuffling.  

The data comes via opentdb.com in the form of a JSON file that you can see here: <https://opentdb.com/api.php?amount=10&category=9&difficulty=easy&type=multiple>. Each time you access that link, it returns different data.

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
