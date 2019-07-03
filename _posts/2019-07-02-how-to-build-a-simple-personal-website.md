---
layout: post
title: How to Build a Simple Personal Website
date: 2019-07-02 14:37 -0400
---

Over the weekend I put together a simple personal website using [Gandi.net](https://admin.gandi.net), [GitHub Pages](https://pages.github.com/), and [Cloudlfare](https://cloudflare.com/). If you follow this tutorial, you should be up and running without issue. But, software is always changing. Let me know if anything breaks and needs to be updated.

Good luck!

## Tutorial

### Register a Domain

1. Buy and register a domain. I used [Gandi.net](https://www.gandi.net/) to purchase `taylorsteinberg.com`.

### Configure DNS

1. On [Gandi.net](https://admin.gandi.net) add the following [A records](#a) to your DNS settings: Domain > DNS Records.

#### A Records

```text
;; A Records
example.com.    1   IN  A   185.199.108.153
example.com.    1   IN  A   185.199.111.153
example.com.    1   IN  A   185.199.110.153
example.com.    1   IN  A   185.199.109.153
```

Note: Replace `example.com` with your domain.

Note: Make sure you have a '.' at the end of each record: `example.com.`

2. On [Gandi.net](https://admin.gandi.net) update the `www` [CNAME record](#cname) in your DNS settings: Domain > DNS Records.

#### CNAME

```text
;; CNAME Records
www.example.com.    1   IN  CNAME   username.github.io.
```

Note: Replace username with your GitHub username.

### Create a Website

1. Create a new public repository on [GitHub](https://github.com/) under your personal account. I called mine [`personal-website`](https://github.com/tdstein/personal-website).
1. Create an [`index.html`](#index.html) file on the master branch of your new repository:

```html
<!DOCTYPE HTML>
<html>
    <body>
        <h1>Hello, World!</h1>
    </body>
</html>
```

### Configure GitHub Pages

1. Enable [GitHub Pages](https://pages.github.com/) for your repository: Settings > GitHub Pages > Source > Master Branch.
1. Configure GitHub Pages to use your custom domain: Settings > GitHub Pages > Custom Domain > `www.example.com`

Note: Make sure you include `www.` in the domain name.

This will create a CNAME record in your repository the value you entered.

### Configure Cloudflare

1. Register an account on [Cloudlfare](https://cloudflare.com/)
1. Add your site.
1. Choose a free plan.
1. Follow the instructions to change your nameserver on Gandi.net to Cloudflare: Domain > Nameserver
1. Enable "Always Use HTTPS": Crypto > Always Use HTTPS

Once configured your domain will automatically be redirected over `https`.

At this point, your DNS will transfer to Cloudflare.

### Wait

Your website will be available at your domain once your DNS changes have been propagated. This can take a few minutes or a few hours.
