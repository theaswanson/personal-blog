---
title: Deploying a SPA to S3 Using GitHub Actions
date: "2021-03-05T21:00:00.000Z"
description: "Continuous delivery is the bomb, and with GitHub Actions it's easy to setup. Let's take a look at how to automatically build and deploy a single-page app to S3 after each commit."
---

Continuous delivery is the bomb, and with GitHub Actions it's easy to setup. Let's take a look at how to automatically build and deploy a single-page app to S3 after each commit.

1. Create S3 bucket
   - Configure for static web hosting
2. Create user in S3
   - Get bucket name
   - Get key ID
   - Get secret access key
3. Set secrets in GitHub repo
4. Create GitHub action
   - Create personal access token that allows workflows (optional)
