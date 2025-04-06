# hugo-isaac
This is the repo for hugo-isaac website I worked on in Barcelona. For the live website I am creating. 

this is the link to the live page hugo-isaac:
https://isaacpierreracine.github.io/hugo-isaac/

Run site locally: hugo serve 
or 
make dev

insert local address in browser: http://localhost:1313/

Reminder session with Lairs 18 mars 2025:
when making changes always:
git status
git add name of file with changes to commit
or
git add . (adds all files with changes)

git commit -m 'commit message'
git push

remove a file: rm -r (name of the file)

to get into the zen mode: command k and z

to create a new post:
hugo new content/path/to/content/new_post.md

Simple workflow:

Work on your site locally, running: 
hugo server --baseURL "http://localhost:1313/"
When you're ready to deploy, commit your changes and push to GitHub
GitHub Pages will use the production baseURL setting in your config file to serve your site
This approach keeps your workflow simple and avoids the need for separate config files or environment variables. Just remember to use the --baseURL flag when running hugo server locally.

this is my yaml file as per april 6 2025:
# todo: try dropping the /hugo-isaac/ from the base url + in images synthax
baseURL: "https://isaacpierreracine.github.io/hugo-isaac/" 
languageCode: en-us
title: isaac pierre racine
theme: PaperMod
publishDir: public

params:
  homeInfoParams:
    title: "Archive et portfolio de mon travail"
    content: Utiliser l'onglet 'Categories' pour choisir une discipline. 
  showbreadcrumbs: true
  cover:
    linkfullimages: true
  
menu:
  main:
    - name: About
      url: /about/
      weight: 10
    - name: Contact
      url: /contact/
      weight: 50
    - identifier: categories
      name: Categories
      url: /categories/
      weight: 20
    - identifier: tags
      name: Tags
      url: /tags/
      weight: 30
    - identifier: Archives
      name: Archives
      url: /Archives/
      weight: 40