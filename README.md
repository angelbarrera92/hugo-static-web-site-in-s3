# HOW TO

```bash
$ git clone --recurse-submodules git@github.com:angelbarrera92/cnab-hugo-s3-bundle.git
$ cd cnab-hugo-s3-bundle/
$ duffle build .
$ duffle credentials generate aws-s3 duffle-s3-site:0.4.1
$ duffle install my-site-cnab -c aws-s3 --set aws-default-region=eu-central-1 duffle-s3-site:0.4.1
Executing install action...
hey I am installing things over here
{
    "Location": "http://my-site-cnab.s3.amazonaws.com/"
}
Building sites … 
                   | EN  
+------------------+----+
  Pages            |  7  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  3  
  Processed images |  0  
  Aliases          |  0  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 6 ms
upload: cnab/app/hellocnab/public/404.html to s3://my-site-cnab/404.html
upload: cnab/app/hellocnab/public/categories/index.xml to s3://my-site-cnab/categories/index.xml
upload: cnab/app/hellocnab/public/categories/index.html to s3://my-site-cnab/categories/index.html
upload: cnab/app/hellocnab/public/dist/js/app.3fc0f988d21662902933.js to s3://my-site-cnab/dist/js/app.3fc0f988d21662902933.js
upload: cnab/app/hellocnab/public/tags/index.html to s3://my-site-cnab/tags/index.html
upload: cnab/app/hellocnab/public/index.xml to s3://my-site-cnab/index.xml
upload: cnab/app/hellocnab/public/sitemap.xml to s3://my-site-cnab/sitemap.xml
upload: cnab/app/hellocnab/public/index.html to s3://my-site-cnab/index.html
upload: cnab/app/hellocnab/public/dist/css/app.955516233bcafa4d2a1c13cea63c7b50.css to s3://my-site-cnab/dist/css/app.955516233bcafa4d2a1c13cea63c7b50.css
upload: cnab/app/hellocnab/public/tags/index.xml to s3://my-site-cnab/tags/index.xml
upload: cnab/app/hellocnab/public/images/gohugo-default-sample-hero-image.jpg to s3://my-site-cnab/images/gohugo-default-sample-hero-image.jpg
The url is: http://my-site-cnab.s3-website.eu-central-1.amazonaws.com/
```

```bash
$ duffle uninstall my-site-cnab -c aws-s3 --set aws-default-region=eu-central-1
Executing uninstall action...
hey I am uninstalling things now
delete: s3://my-site-cnab/404.html
delete: s3://my-site-cnab/categories/index.html
delete: s3://my-site-cnab/tags/index.xml
delete: s3://my-site-cnab/categories/index.xml
delete: s3://my-site-cnab/images/gohugo-default-sample-hero-image.jpg
delete: s3://my-site-cnab/dist/css/app.955516233bcafa4d2a1c13cea63c7b50.css
delete: s3://my-site-cnab/index.html
delete: s3://my-site-cnab/index.xml
delete: s3://my-site-cnab/dist/js/app.3fc0f988d21662902933.js
delete: s3://my-site-cnab/sitemap.xml
delete: s3://my-site-cnab/tags/index.html
remove_bucket: my-site-cnab
```

## Links

- https://engineering.ifdb.com/2017/10/quick-static-websites-on-aws-s3-and-cloudfront-with-the-aws-cli/
- https://engineering.bitnami.com/articles/production-ready-packaging-with-cnab-and-bitnami-kubernetes-production-runtime-bkpr.html
