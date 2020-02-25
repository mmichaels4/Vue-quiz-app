# quiz_app

##
App was originally created following this tutorial: https://www.youtube.com/watch?v=4deVCNJq3qc&t=2133s
Although she gives setep-by-step instructions, I tried to not follow them entirely. 
Some major areas of difference include:
* Adding a final score page
* Adding a footer
* A more efficient method of shuffling.  

The data comes via opentdb.com in the form of a JSON file like:
```
{"response_code":0,"results":[{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"Which best selling toy of 1983 caused hysteria, resulting in riots breaking out in stores?","correct_answer":"Cabbage Patch Kids","incorrect_answers":["Transformers","Care Bears","Rubik&rsquo;s Cube"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What is the largest organ of the human body?","correct_answer":"Skin","incorrect_answers":["Heart","large Intestine","Liver"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What is on display in the Madame Tussaud&#039;s museum in London?","correct_answer":"Wax sculptures","incorrect_answers":["Designer clothing","Unreleased film reels","Vintage cars"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What was the nickname given to the Hughes H-4 Hercules, a heavy transport flying boat which achieved flight in 1947?","correct_answer":"Spruce Goose","incorrect_answers":["Noah&#039;s Ark","Fat Man","Trojan Horse"]}
```
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
