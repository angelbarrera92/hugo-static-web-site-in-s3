# HOW TO

```bash
git clone --recurse-submodules git@github.com:angelbarrera92/cnab-hugo-s3-bundle.git
cd cnab-hugo-s3-bundle/
duffle build .
duffle credentials generate aws-s3 duffle-s3-site:0.4.1
duffle install my-site-cnab -c aws-s3 --set aws-default-region=eu-central-1 duffle-s3-site:0.4.1
```

```bash
duffle uninstall my-site-cnab -c aws-s3 --set aws-default-region=eu-central-1
```
