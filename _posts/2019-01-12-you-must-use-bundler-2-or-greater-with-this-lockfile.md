---
layout: post
title: You must use Bundler 2 or greater with this lockfile.
date: 2019-01-12T14:16:22.720Z
microblog: false
author: Phil
---
Are you using Jekyll post-build actions on Netlify? 

I was, had updated my build environment on my Mac (OS X Mojave). I could not get it to build - the errors:

```bash
7:41:05 PM: You must use Bundler 2 or greater with this lockfile.
7:41:05 PM: Error during gem install
7:41:05 PM: Error running command: Build script returned non-zero exit code: 1
7:41:05 PM: Failing build: Failed to build site
7:41:05 PM: failed during stage 'building site': Build script returned non-zero exit code: 1
```

The Gemfile.lock had this line at the bottom:

```bash
BUNDLED WITH
   2.0.1
```

So what was wrong, I was building my site with Bundler 2. The problem was I was building with Bundler 2, but Netlify build servers are currently using 1.17.1. Thus Netlify build servers are currently out of date. So on my machine, the fix is to run gem uninstall bundler and then use:

```bash
gem install bundler -v 1.17.1
```

Delete the Gemfile.lock, and re-run:

```bash
bundle install
```

You should now have this in the Gemfile.lock:

```bash
BUNDLED WITH
   1.17.1
```

Push to GitHub and the build should work.
