---
layout: post
title: You must use Bundler 2 or greater with this lockfile.
date: 2019-01-12T14:16:22.720Z
microblog: false
author: Phil
---
Are you using Jekyll post build actions on Netlify? I was, had updated by build environment on my Mac (OS X Mojave). 

I could not get it to build - the errors:

7:41:05 PM: You must use **Bundler 2** or greater with this lockfile.
7:41:05 PM: Error during gem install
7:41:05 PM: Error running command: Build script returned non-zero exit code: 1
7:41:05 PM: Failing build: Failed to build site
7:41:05 PM: failed during stage 'building site': Build script returned non-zero exit code: 1

The Gemfile.lock had this line at the bottom:

BUNDLED WITH
   2.0.1

So what was wrong I was building with Bundler 2. The problem is I was building with Bundler 2, but Netlify build servers are currently using 1.17.1. So gem uninstall bundler and use:

gem install -v 1.17.1

Delete the Gemfile.lock, and re-run bindler install. You should now have this in the Gemfile.lock:

BUNDLED WITH
   1.17.2

Push to GitHub and the build should work.
