---
date: "Sun 7 Jul 2013 09:13:32 UTC"
layout: post
title: "License your gems"
---

Recently I was looking at a few libraries for doing terminal colors. Luckily there are [plenty of options](https://www.ruby-toolbox.com/categories/Terminal_Coloring).

One habit I do have is checking the licenses of gems I use. This case struck me - The #1 and #4 ruby-toolbox-rated gems are actually GPL licensed (See [term-ansicolor](https://github.com/flori/term-ansicolor) and [colorize](https://github.com/fazibear/colorize)).

There are [differing interpretations](http://en.wikipedia.org/wiki/GNU_General_Public_License#Libraries) of linking against GPL code (as opposed to LGPL). For my purposes, the GPL wasn't appropriate.

I'm quite often developing proprietary applications, as are many Rails developers. The common default in Rubyland is permissive licenses (MIT/BSD and Ruby), so there generaly isn't any issue making use of gems. It's so common that I see a lot of developers that use gems with apparent impunity from licensing, but that's another story...

One issue that struck me is that while I pay attention to gem licenses - I know plenty of people that don't. Similarly, the gem authors themselves don't make any such guarantee. I could install some_gem_x that installs some_other_license_gem_y.

To satisfy my curiosity I did a quick poll of gems registered with [https://rubygems.org/](https://rubygems.org/). The [gemspec standard](http://docs.rubygems.org/read/chapter/20) provides for specifying one or more licenses, but it's optional and only has limited use[^1].

Of the ~51,000 gems listed on RubyGems only 3,700 have a license defined in the gemspec[^2]. That's just 6%. That's not great for drawing any conclusions. The better news is that this 6% represents 40% of total downloads.

The next issue is the license field is free form. So it's perfectly valid to specify 'BSD'[^3] as opposed to 'BSD-2-Clause'. This leads to some ambiguity.

Even so, a simple analysis shows the vast majority are permissive. 3,000 alone are straight "MIT" licenses. BSD variants and Apache licenses follow closely behind. 

That said, the GPL and relatives do feature. Plus, there is possibly some [selection bias](http://en.wikipedia.org/wiki/Selection_bias) with this type of sample. The use of the license field in the gemspec might be correlated to permissive licenses in any manner of ways.

To speed up the process I put together a tool to example a Gemfile. To get started:

    $ gem install gemterms

Then change to a Rails project (or any Gemfile managed project) and execute:

    $ gemterms

You can run this on your project right now[^4]. 

Unfortunately this works off gemspecs, so there are a lot of gaps. It will take a while for licenses to start showing up in the licenses. To fill the gap I've considered scraping github to determine licenses. A trivial test shows Github-based projects represent at least 70% of gems listed on RubyGems.

The MIT license should be easy to spot - by the convention of using MIT-LICENCE.txt and the standard layout of the text. A small sample had good results.

Whilst the [Github Terms of Service](https://help.github.com/articles/github-terms-of-service) doesn't get explicit about scraping, it's somewhat impolite. Next step is to ask. Hopefully even a limited sample will plug most of the gap.

In the meantime, feel free to give `gemterms` a try. If you're a gem author or contributor - get your gemspec updated!

### Footnotes

[^1]: Are you a gem developer? If you don't have the license in your gemspec, please do so!

[^2]: To make life a bit easier, if a later gemspec specified a license it was assumed for the gem. For example, Rails started specifying _MIT_ in the gemspec as of 4.0.0.beta1.

[^3]: Which is ambiguous in itself.

[^4]: It's very much v0.1 software. [Feedback is welcome](https://github.com/jonathannen/gemterms)
