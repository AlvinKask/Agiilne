# Agiilne

 - Lae alla terminal - ms store'ist
 - lae ja installi gitbash
   - Add agit bash profile to windows terminal
   - use visual studio code as gits default editor
   - override default branch name for new repositories
 - winget search github
 - winget install github.cli (--source winget)
 
 ## *Peale seda töötab käsklus "gh"*
### Loo connection githubi ja arvuti vahel
```
gh auth login
? What account do you want to log into? GitHub.com
? What is your preferred protocol for Git operations? HTTPS
? Authenticate Git with your GitHub credentials? Yes
? How would you like to authenticate GitHub CLI? Login with a web browser

! First copy your one-time code: 2625-4807
Press Enter to open github.com in your browser...
✓ Authentication complete.
- gh config set -h github.com git_protocol https
✓ Configured git protocol
✓ Logged in as AlvinKask
```
### Loo uus repo
```
gh repo create
? What would you like to do? Create a new repository on GitHub from scratch
? Repository name kta22elearnscraping

? Repository name kta22elearnscraping
? Description
? Visibility Public
? Would you like to add a README file? Yes
? Would you like to add a .gitignore? No
? Would you like to add a license? Yes
? Choose a license The Unlicense
? This will create "kta22elearnscraping" as a public repository on GitHub. Continue? Yes
✓ Created repository AlvinKask/kta22elearnscraping on GitHub
? Clone the new repository locally? Yes
Cloning into 'kta22elearnscraping'...
```
 
### Ava visual studio code ja uuenda asjad
``` 
u-453@T238-06 MINGW64 ~
$ cd kta22elearnscraping/

u-453@T238-06 MINGW64 ~/kta22elearnscraping (main)
$ code .

u-453@T238-06 MINGW64 ~/kta22elearnscraping (main)
$ node -v
v14.15.4

u-453@T238-06 MINGW64 ~/kta22elearnscraping (main)
$ winget install openjs.nodejs
```
 
### Loob failipaketi ja hakkab hoiustama seal packageid
```
u-453@T238-06 MINGW64 ~/kta22elearnscraping (main)
$ npm init -y
```
### Visual studio dode'is
- new file ".gitignore"
- sisse kirjutada "node_modules"
- https://github.com/axios/axios
```
u-453@T238-06 MINGW64 ~/kta22elearnscraping (main)
$ npm i axios
```
 
- new file "main.js"
- package.json -> "type": "module",

### main.js
```
import axios from "axios";

axios.get('https://api.chucknorris.io/jokes/random').then(response=> {
    console.log(response.data);
});
```
### Installi cheerio
```
npm i cheerio
```
### main.js
```
import axios from 'axios';
import * as cheerio from 'cheerio';

axios.get('https://xkcd.com/2831/').then(response=> {
    const $ = cheerio.load(response.data);
    let img = $('#comic>img')
    console.log(img.attr('title'));
    console.log(img.attr('alt'));
    console.log(img.attr('src'));
});
```
- Kirjuta reminali "node main.js"
 
### Alternatiiv
```
let response = await axios.get('https://xkcd.com/2831/');
const $ = cheerio.load(response.data);
let img = $('#comic>img')
console.log(img.attr('title'));
console.log(img.attr('alt'));
console.log(img.attr('src'));
```
### Kuva 10 esimest koomuskit
```
for(let i = 1; i<10; i++){
    let response = await axios.get('https://xkcd.com/' + i);
    const $ = cheerio.load(response.data);
    let img = $('#comic>img')
    console.log(img.attr('title'));
    console.log(img.attr('alt'));
    console.log(img.attr('src'));
}
```
### Kuva 10 esimest koomuskit aga tee seda aeglaselt, et server ei arvaks, et tegu DDOS rünnakuga
```
function delay(time){
    return new Promise(resolve => setTimeout(resolve, time));
}


for(let i = 1; i<10; i++){
    let response = await axios.get('https://xkcd.com/' + i);
    const $ = cheerio.load(response.data);
    let img = $('#comic>img')
    console.log(img.attr('title'));
    console.log(img.attr('alt'));
    console.log(img.attr('src'));
    await delay (1000);
}
```
### CASHE 10 esimest koomuskit
```
import axios from "axios";
import * as cheerio from 'cheerio';
import fs from 'fs';

function delay(time) {
    return new Promise(resolve => setTimeout(resolve, time));
} 
  

for(let i = 1; i<10; i++){
    let data;
    let response;
    if(!fs.existsSync('./cache/' + i + '.html')){
        response = await axios.get('https://xkcd.com/' + i);
        await delay(1000);
        console.log('NOT CACHE!!!!');
        data = response.data;
        fs.writeFileSync('./cache/' + i + '.html', data);
    } else {
        console.log('CACHE!!!!');
        data = fs.readFileSync('./cache/' + i + '.html');
    }
    const $ = cheerio.load(data);
    let img = $('#comic>img')
    console.log(img.attr('title'));
    console.log(img.attr('alt'));
    console.log(img.attr('src'));
    
}
```
