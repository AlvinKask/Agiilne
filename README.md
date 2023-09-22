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

 
