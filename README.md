# The Music Guy (client site)

Test site [here](http://tmg-test-site.s3-website.eu-west-2.amazonaws.com), live site [here](https://www.themusicguy.co.uk/).

## Setup

* Copy the repo

`$ git clone https://github.com/mstuartf/themusicguy-site.git`

* Install packages

`$ cd themusicguy-site`

`$ npm install`

* Run development

`$ npm run dev`

* Create production build

`$ npm run build`

## S3 deployment

* Empty bucket
* Upload index.html, favicon.ico and contents of dist directory into bucket
* Overview tab > select all files in the bucket > Actions > Make Public > Make Public
