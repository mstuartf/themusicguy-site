# skeleton-vue-site

This is a template Vue website to use as a starting point for new projects. Example [here](http://skeleton-vue-site.s3-website.eu-west-2.amazonaws.com)

## Features

* responsive layout using SplitSection components (option to flatten on desktop; reserve space behind floating header)
* FloatingHeader component for desktop and mobile
* mobile header with AnimatedBurger menu component and fullscreen menu dropdown
* load all strings from a copy.json file (only need to change in one place)
* auto scroll to each section from HeaderButton components (smooth scrolling using vue2-smooth-scroll)
* load SVG icons as js using (vue-svgicon)
* tailwind CSS (local tailwind.js config file)
* webpack / babel
* stage-3 presents in .babelrc file (so uglify doesn't break)

## Setup

* Copy the repo

`$ git clone https://github.com/mstuartf/skeleton-vue-site.git`

* Install packages

`$ cd skeleton-vue-site`

`$ npm install`

* Generate SVG files

`$ npm run generate-icons`

* Run development

`$ npm run dev`

* Create production build

`$ npm run build`

## S3 deployment

* Create new bucket - manually or using `$ aws s3 mb s3://bucket-name`
* Upload index.html and contents of dist directory into bucket
* Overview tab > select all files in the bucket > Actions > Make Public > Make Public
* Properties tab > Static website hosting > Use this bucket to host a website > set index.html as index and error file > Save
* Test using endpoint given
