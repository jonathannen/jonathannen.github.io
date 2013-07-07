---
date: "2011-09-29 17:00:08"
layout: post
title: "How fresh are your gems?"
---

I often check my Gemfile to see how "current" my gems are with the latest versions. Even with older projects I like to upgrade reasonably often, relying on good testing to keep the application fresh and operating. If I don't do this I find project get stale and harder to keep up-to-date.

I was doing this manually, so I decided a short script was in order.

This is now wrapped up in a simple gem. To take a look, simply:

    $ gem install gemfresh

Then change to a Rails project (or any Gemfile managed project) and execute:

    $ gemfresh

Gemfresh will take a look at your Gemfile and Gemfile.lock - it will then compare this with data sourced from RubyGems sources (generally [https://rubygems.org/](https://rubygems.org/)). The report will tell you whats current, what can be upgrade and what is "obsolete".

There are plenty of good reasons to have older versions in your Gemfile, but this is just an easy way to see opportunities to upgrade.
