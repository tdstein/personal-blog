---
layout: post
title: How to Build a Simple Personal Website
categories: software
tags: tutorial
date: 2019-07-02 14:37 -0400
---

This tutorial will teach you how to host a personal website on the internet for free, plus domain fees, using [Gandi.net](https://admin.gandi.net), [GitHub Pages](https://pages.github.com/), and [Cloudlfare](https://cloudflare.com/).

## Prerequisites

You will need a personal account on each of the following:

- [Gandi.net](https://admin.gandi.net)
- [GitHub](https://github.com/)
- [Cloudlfare](https://cloudflare.com/)

## Domain

1. Register a domain on [Gandi.net](https://www.gandi.net/).

## DNS

### A Records

1. On [Gandi.net](https://admin.gandi.net) add the following [A records](#a) to your DNS settings: Domain > DNS Records.

```text
;; A Records
example.com.    1   IN  A   185.199.108.153
example.com.    1   IN  A   185.199.111.153
example.com.    1   IN  A   185.199.110.153
example.com.    1   IN  A   185.199.109.153
```

Note: Replace `example.com` with your domain.

Note: Make sure you have a '.' at the end of each record: `example.com.`

### CNAME

2. On [Gandi.net](https://admin.gandi.net) update the `www` [CNAME record](#cname) in your DNS settings: Domain > DNS Records.

```text
;; CNAME Records
www.example.com.    1   IN  CNAME   username.github.io.
```

Note: Replace username with your GitHub username.

## Website

1. Create a new public repository on [GitHub](https://github.com/) under your personal account. I called mine [`personal-website`](https://github.com/tdstein/personal-website). You can call yours whatever you want to.
1. Create an [`index.html`](#index.html) file on the master branch of your new repository:

```html
<!DOCTYPE HTML>
<html>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

## Hosting

1. Enable [GitHub Pages](https://pages.github.com/) for your repository: Settings > GitHub Pages > Source > Master Branch.
1. Configure GitHub Pages to use your custom domain: Settings > GitHub Pages > Custom Domain > `www.example.com`

Note: Make sure you include `www.` in the domain name.

This will create a CNAME record in your repository the value you entered.

## SSL

Use the following steps to enable `ssl` to secure your website by encrypting all traffic over `https`.

1. Add your domain on [Cloudlfare](https://cloudflare.com/).
1. Choose a free plan.
1. Follow the instructions to change your nameserver on Gandi.net to Cloudflare: Domain > Nameserver
1. Enable "Always Use HTTPS": Crypto > Always Use HTTPS

Once configured your domain will automatically be redirected over `https`.

At this point, your DNS will transfer to Cloudflare and traffic will be redirected.

## Wait

Your website will be available at your domain once your DNS changes have been propagated. This can take a few minutes or a few hours.
