# Hugo static site on AWS S3

[Hugo](https://gohugo.io) is a fast and modern static site generator written in Go, and designed to make website creation fun again.

[Amazon Simple Storage Service *(Amazon S3)*](https://aws.amazon.com/s3) is an object storage service that offers industry-leading scalability, data availability, security, and performance.

## TL;DR;

```bash
$ duffle install hello-cnab -c aws-s3-creds -f ./bundle.cnab
```

## Introduction

This [CNAB bundle](https://cnab.io) bootstraps a static website deploying it on an [AWS S3 Bucket](https://aws.amazon.com/s3).

Under the hood, this package provisions the website using the [awscli](https://aws.amazon.com/cli/) rendering the site using [Hugo](https://gohugo.io).

See it in action in the following video:

<p>
  <img width="700" src="./demo.svg">
</p>

## Prerequisites

* AWS account with permissions to provision S3 buckets.

## Installing the CNAB Bundle

> **Important:** The bundle is not recommended for production purposes.

In order to manage the bundle, we are going to use a command line tool called [Duffle](https://duffle.sh), please ensure that you [have installed](https://github.com/deislabs/duffle/releases) its latest version before continue.

### Clone this repository

Clone this repository to download the bundle and the verification key to your filesystem:

```
$ git clone --recurse-submodules git@github.com:angelbarrera92/hugo-static-web-site-in-s3.git
$ cd ./hugo-static-web-site-in-s3.git
```

### Import Signing Key

CNAB bundles, by default, are signed by their provider and importing a verification key is required to verify the integrity and source of the package.

> **Tip**: Alternatively you can append the `--insecure` flag to every duffle command


```bash
# verification-public.key can be found in the git repo, download it and then run:
$ duffle key add verification-public.key --armored
```

### Verify signature

To verify the bundle, just type:

```bash
$ duffle bundle verify -f bundle.cnab
Signed by "Angel Barrera Sanchez <angelbarrerasanchez@protonmail.com>" (5A81 FE7A A779 DE57 55EA AFAE 3512 FAD7 7C6A 475)
```

### Define Credentials

Some credentials from your environment need to be supplied to the bundle. Specifically, AWS credentials are required to manage the S3 Buckets.  

First, generate a credentials file:


```bash
$ duffle creds generate aws-s3-creds -f ./bundle.cnab
```

This will create a file in `~/.duffle/credentials/aws-s3-creds.yaml` showing the credentials needed with empty values.

You can either fill the values in directly, or edit them by typing:

```bash
$ duffle creds edit aws-s3-creds
```

### Parameters

The following table lists the configurable parameters of the Hugo statis website in S3 CNAB bundle and their default values.

| Parameter          | Description                                      | Default      |
|--------------------|--------------------------------------------------|--------------|
| aws-default-region | Specifies the AWS region to send the request to. | eu-central-1 |

### Usage Examples

Installation with default settings, will create a bucket in `eu-central-1` region:

```bash
$ duffle install my-release -c aws-s3-creds -f ./bundle.cnab
```

Installation with specific region:

```bash
$ duffle install my-release -c aws-s3-creds --set aws-default-region=us-east-1 -f ./bundle.cnab
```

You can also uninstall a release

```
$ duffle uninstall my-release -c wordpress-creds
```

## Development

```bash
# Build a new version of the bundle
$ duffle build .
```

```bash
# Export the generated bundle
duffle show hugo-static-web-site-in-s3:1.0.0 --raw > ./bundle.cnab
```
