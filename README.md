# 炭 (sumi) Foundation

[![License: OEL](https://img.shields.io/badge/License-OEL-green.svg?style=flat)](https://omnifi.foundation/licenses/OEL)
[![npm](https://img.shields.io/npm/v/npm.svg)]()
![@omnificoop](https://img.shields.io/badge/contact-@omnificoop-green.svg?style=flat)

**炭 (or charcoal in English) Foundation** is the main web project for Omnifi.Foundation.

## Posts

Articles (./content/posts) are located in a separate repository to make publishing content simpler. 

## Theme

The theme for the site is an Hugo submodule (./site/themes/sumi) and is separate from the content and function of the site to reduce the need for design and structural changes to be made in the same location as content and featue changes.

The styling can be found within the theme and is loaded during the build into the main project. 

## Build

The app currently relies on HUGO. To build it's recommended to use the `jojomi/hugo` Docker image as so:

```shell
make && docker run -it -p 8081:80 --name "sumi-hugo" -P -v $(pwd):/src jojomi/hugo hugo -d ../.build -s ./site -v; docker rm "sumi-hugo" && cp site/assets/scripts/js/*.js .build/scripts/js
docker rm -f sumi-nginx  
docker run --name sumi-nginx -v $(pwd)/.build:/usr/share/nginx/html:ro -p 8080:80 -d nginx     
```

This will provide the complete app build in the `.build` folder.