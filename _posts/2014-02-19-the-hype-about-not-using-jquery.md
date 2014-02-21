---
layout: post
title:  "The hype about not using jQuery"
date:   2014-02-19 12:03:00
categories: en jquery
---

I see a hype by developers to criticize jQuery, I think the ideal is to be critical and balance the weight on the scale. Obviously you will realize that my arguments do not favor to simply ignore the use of jQuery and replace it with something else, even by Vanilla JS.

This article is mainly motivated from another [article newly released][1] at [Tableless](http://tableless.com.br) site. The article demonstrates they removed almost 100KB which would only run for a few functions and began to use pure JS.
[1]: http://tableless.com.br/considere-nao-usar-jquery

The first point we need to consider is to remove a JS library and not a framework. Without *inversion of control*, we use the lib only when we need it and it is easy to unplug it and use something else, like vanilla JS.

If the only reason is weight and load time on the site, I recommend putting a number of priorities first. Let's list some problems I found in the same site where the jQuery lib has been removed.

1. Consider not abusing on fonts.
========

It's pretty nifty being able to adapt the layout of your site to use different fonts than found by default in browsers. Even so, loading fonts can be very costly.

See the example:

[![Fonts](/images/tableless-fontes.png)](/images/tableless-fontes.png)

This shows that the site loads **more than 320KB of fonts**, with 4 different versions - regular, bold, light and medium - and that are normally used only 2 (regular and bold). If the site forego the light and medium, it would accomplish a saving of 160KB.

2. Consider not loading images.
========

In another example the same site carries more than 600KB of images, it is the biggest weight on the site. Let's look at this pie chart as the site is weighted:

[![Pizza chart](/images/tableless-pizza.png)](/images/tableless-pizza.png)

Of 694KB uploaded on the site, not considering fonts, 618KB correspond to images.

But the question is whether they are being used. I did this loading test on the home site, so I went to check what were those images. I finished at the first image I checked, the heaviest of them:

[![Images](/images/tableless-imagens.png)](/images/tableless-imagens.png)

The heavier image that was loaded, with more than 100KB, simply was not used in the home page, where I did the measuring and checking.

3. Consider using GZIP.
========

Many sites just do not use compression for they static files. This is something besides minimizing a JS file, but simply complements it with GZIP, for example. Using this jQuery would cost only 32KB to be loaded.

Remember that JS files - for being in essence a text file - have an incredible gain for GZIP compression in relation to images.

4. Consider making a custom build of jQuery.
========

One of the most interesting and not very recent advantages of jQuery is precisely to allow building a custom version using only the necessary items.

It costs nothing to take a read at [jQuery Github's readme file][2] to see how we get a version with only what we need from the library.
[2]: https://github.com/jquery/jquery#how-to-build-your-own-jquery

5. Consider running unit tests.
=======

Unit tests are important and should be part of the routine of all JS developers who want to keep their projects on a daily basis. They decrease error occurrences and do not allow multiple occurrences of a single error.

jQuery is quite tested. Therefore, even though you take a smaller part of the library, you will get a code that has been tested and can tell you that future errors can be outside of the library.

How many times do you have implemented something with jQuery and the bug was there in the library and not in your code?

If you actually find a bug in jQuery, report it at their [issue tracker][3]. There will have a team to fix the bug and create tests for it to not happen again. It's like outsourcing part of your code for free.
[3]: http://bugs.jquery.com/

6. Consider the cross-browser compatibility
========

Not long ago appeared the "You might not need jQuery", reaching the peak of the hype that I mentioned. Interestingly, they showed how to replace some parts of jQuery to pure JS, with few *ms* performance improvement.

The problem is that many times we face very boring compatibility issues.

Unlike developing something that runs on a server, either in Node, Perl, Python, Ruby, PHP, etc., is that we work with many different environments, because each browser is an environment. Each has its engine, its structure and its bugs.

All the code you can abstract in jQuery, consider an amazing reduction of time to test only the minimum that has been done after loading the library to make sure everything works on any browser you want to support. Remember that jQuery 1.x still supports IE6 (almost extinct), while the jQuery 2.x support IE9+ and other considered modern browsers. It is a time we do not have to lose.

Still considering the jQuery 2.x, it is worth remembering that only in this version we have over 100 items marked for workarounds on crossbrowser compatibility. [Rick Waldron](https://twitter.com/rwaldron) compiled [a list of these items][4]. If you want to create your own pure JS, it is worth checking that out to not fall into some of the gotchas already observed and fixed in jQuery.
[4]: https://gist.github.com/rwaldron/8720084#file-reasons-md

7. Consider your time
=======

There is a common phrase among developers I know: "*Optimized for Development*". This should be a mantra. Before over optimizing the performance of your website, remember that it can always be done gradually and without tying up your time with something already solved.

If you take it seriously that's not good to use a JS library - and that goes for jQuery, Dojo, YUI, etc. - you can lose a valuable time which could be used to solve the most important problems of your project.

Need a hint? Invest your free time creating unit tests for your functions. Worth leaving your design more stable, without reinventing the wheel.