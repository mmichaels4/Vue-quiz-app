# quiz_app

##
App was originally created following this tutorial: https://www.youtube.com/watch?v=4deVCNJq3qc&t=2133s
Although she gives setep-by-step instructions, I tried to not follow them entirely. 
Some major areas of difference include:
Markup : * Bullet list
* Adding a final score page
* Adding a footer
* A more efficient method of shuffling.  

The data comes via opentdb.com in the form of a JSON file like:
{"response_code":0,"results":[{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"Which best selling toy of 1983 caused hysteria, resulting in riots breaking out in stores?","correct_answer":"Cabbage Patch Kids","incorrect_answers":["Transformers","Care Bears","Rubik&rsquo;s Cube"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What is the largest organ of the human body?","correct_answer":"Skin","incorrect_answers":["Heart","large Intestine","Liver"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What is on display in the Madame Tussaud&#039;s museum in London?","correct_answer":"Wax sculptures","incorrect_answers":["Designer clothing","Unreleased film reels","Vintage cars"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What was the nickname given to the Hughes H-4 Hercules, a heavy transport flying boat which achieved flight in 1947?","correct_answer":"Spruce Goose","incorrect_answers":["Noah&#039;s Ark","Fat Man","Trojan Horse"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What is the French word for &quot;hat&quot;?","correct_answer":"Chapeau","incorrect_answers":["Bonnet"," &Eacute;charpe"," Casque"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What company developed the vocaloid Hatsune Miku?","correct_answer":"Crypton Future Media","incorrect_answers":["Sega","Sony","Yamaha Corporation"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"Which candy is NOT made by Mars?","correct_answer":"Almond Joy","incorrect_answers":["M&amp;M&#039;s","Twix","Snickers"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"According to the nursery rhyme, what fruit did Little Jack Horner pull out of his Christmas pie?","correct_answer":"Plum","incorrect_answers":["Apple","Peach","Pear"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"How many furlongs are there in a mile?","correct_answer":"Eight","incorrect_answers":["Two","Four","Six"]},{"category":"General Knowledge","type":"multiple","difficulty":"easy","question":"What is the name of NASA&rsquo;s most famous space telescope?","correct_answer":"Hubble Space Telescope","incorrect_answers":["Big Eye","Death Star","Millenium Falcon"]}]}

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
