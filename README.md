# HandyLinks
HandyLinks #HL is an archive of helpful links.
# Git and backend tools 
## Impotant GIT 
1. [Sven Luijten How I git from A to Z](https://svenluijten.com/posts/how-i-git-from-a-to-z)

# Website development

## Places To Find Web Design Inspiration
1. [Awwwards](https://www.awwwards.com/)
2. [Dribbble](https://dribbble.com/)
3. [Behance](https://www.behance.net/)
4. [siteInspire](https://www.siteinspire.com/)
5. [CSS Nectar](https://cssnectar.com/)
6. [UI/UX Components design inspitation](https://calltoinspiration.com)
6. [UI ball Loaders](https://Uiball.com)


## Web tools for developers
1. [10015 All Online Tools in “One Box”](https://10015.io)
2. [](https://css-tricks.com/creating-an-editable-textarea-that-supports-syntax-highlighted-code/)
3. [3-column-layouts](https://matthewjamestaylor.com/3-column-layouts)




## Svg repo

[Svg repo](https://www.svgrepo.com/svg/24907/drone?edit=true)
## Build a complete off chain fullstack web3 app using Laravel Part-1

[BuildWeb3WithLaravel](https://celo.academy/t/build-a-complete-off-chain-fullstack-web3-app-using-laravel-part-1/30)

## How to build a Laravel REST API with Test-Driven Development

[laravel-rest-api](https://www.freecodecamp.org/news/how-to-build-a-laravel-rest-api-with-test-driven-development-c4bb6417db3c/)

## The most popular component library component library for Tailwind CSS

[Tailwind-CSS-component](https://daisyui.com/)
## laravel import large csv jobs queues

[large-csv-jobs-queues](https://laraveldaily.com/post/laravel-import-very-large-csv-jobs-queues)

## How to Use the CSS Box Model and Style SVG Images

[how-to-use-css-box-model-and-style-svg-images](https://www.freecodecamp.org/news/how-to-use-css-box-model-and-style-svg-images/)

## Color Contrast Checker

[Color Contrast Checker](https://coolors.co/contrast-checker/acebd0-000000)


# Screenshots

![Css Selector types](/images/selectors.jpeg)

# Remote jobs
## Top Websites to Find Remote Jobs for programmers:

1. [weworkremotely.com](https://weworkremotely.com)
2. [virtualvocations.com](https://virtualvocations.com)
3. [workingnomads.com](https://workingnomads.com)
4. [freshersworld.com](https://freshersworld.com)
5. [remoteok.com](https://remoteok.com)
6. [justremote.co](https://justremote.co)
7. [flexjobs.com](https://flexjobs.com)
8. [crossover.com](https://crossover.com)
9. [simplyhired.com](https://simplyhired.com)
10. [angel.co](https://angel.co)
11. [toggl.com](https://toggl.com)
12. [remote.co](https://remote.co)


# Crypto & NFTs
## How to launch an NFT collection: 9 steps for success

[successful-nft-drop](https://queue-it.com/blog/successful-nft-drop/)

## A to Z: NFT Glossary

[nft-glossary](https://www.finder.com/nft-glossary)



# Artificial inteligent (AI)
## Find cool artificial intelligence (AI) tools.

[AI Tools Club](https://www.finder.com/nft-glossary)

# Tutorial YouTube video
## Test Driven Laravel - e02 - Deleting a Record, Asserting Instance Of & Carbon Pars

[Test-Driven-Laravel](https://youtu.be/78EXSROAHWc)

## Introduction to APIs | Laravel API Course | Learn Laravel API | Laravel API Tutorial

[Introduction-to-Laravel-API ](https://youtu.be/D29sUCaUJg0)

## Laravel Package Development - e01 - Introduction

[Laravel-Package-Development](https://youtu.be/ivrc1ZKFgHI)

## Notion solidifying documentation for your startup

[Notion-solidifying-documentation](https://youtu.be/U2QBFs0ACQ8)

## Docker Tutorial for Beginners

[Docker-Beginners-tutorial-by-mosh](https://youtu.be/pTFZFxd4hOI)

# CI/CD For laravel share hosting

## you can deploy laravel app directly to share hosting 
## save the code bellow in .scripts folder as deploy.sh in your public_html folder

#!/bin/bash
set -e

echo "Deployment started ..."


# copy .env
(cp .env.example .env) || true
# if already is in maintenance mode
(php artisan down) || true

changed=0
git remote update && git status -uno | grep -q 'Your branch is behind' && changed=1
if [ $changed = 1 ]; then
# fetch the latest version of the app
git fetch git  (ssh://git@ssh.github.com:443/bazzlylinks/geotech-web.git)
# Pull the latest version of the app
git pull ssh://git@ssh.github.com:443/bazzlylinks/geotech-web.git
php artisan migrate --force
php artisan optimize:clear
php artisan up
    echo "Updated successfully";
else
# Exit maintenance mode
php artisan up
    echo "Up-to-date"
fi

echo "Deployment finished!"


## After this save the below code in your .github/workflows/ folder as laravel.yml

name: 🚀 Deploy on push main

on: 
  push:
    branches:    
      - main 
    
jobs:
  web-deploy:
    name: 🎉 Deploy
    runs-on: ubuntu-latest

    steps:
      - name: 🚚 Get latest code
        uses: actions/checkout@v2
      - name: Copy .env
        run: cp .env.example .env
      - name: Install composer Dependencies
        run: composer install -q --no-ansi --no-interaction --no-scripts --no-progress --prefer-dist
      - name: Install node dependencies
        run: npm ci
      - name: Directory Permissions
        run: chmod 755 -R storage bootstrap/cache
       
      - name: 📂 Deploy to server via ssh
        uses: appleboy/ssh-action@v0.1.7
        with:
          host: "hostIp"
          username: 'HostUsername"
          password: "hostPass"
          port: "hostPort"
          script: "cd /home/u665214148/public_html && sh ./.scripts/deploy.sh"


## Finally save the code bellow as .htacces file in your laravel project directory

<IfModule mod_rewrite.c>

<IfModule mod_negotiation.c>

Options -MultiViews -Indexes

</IfModule>

<IfModule mod_rewrite.c>

RewriteEngine On
RewriteCond %{REQUEST_URI} !^public

RewriteRule ^(.*)$ public/$1 [L]

</IfModule>

# Handle Authorization Header

RewriteCond %{HTTP:Authorization} .

RewriteRule .* — [E=HTTP_AUTHORIZATION:%{HTTP:Authorization}]

# Redirect Trailing Slashes If Not A Folder…

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_URI} (.+)/$

RewriteRule ^ %1 [L,R=301]

# Send Requests To Front Controller…

RewriteCond %{REQUEST_FILENAME} !-d

RewriteCond %{REQUEST_FILENAME} !-f

RewriteRule ^ index.php [L]


</IfModule>