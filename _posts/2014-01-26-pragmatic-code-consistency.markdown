---
layout: post
title:  "Pragmatic Code Consistency"
date:   2014-01-26 01:46:00
categories: en
---

I always wanted to write an article in English and always wanted to use the word [Pragmatic][Pragmatic] in something to speak about. I'm trying to accomplish both on the same time.

[Pragmatic]: https://en.wikipedia.org/wiki/Pragmatism 'Pragmatism on Wikipedia'

When we write code, there's one thing we need to focus beyond the results, and that's the code consistency. This means you need to adopt conventions that would make your all project's code like it was written by the same person. It doesn't matter how many people were involved, you can't differentiate personal styles.

To adopt a code style and establish a style convention you must not cling to personal tastes but such really important things as maintainability, readability and re-usability.

Code consistency looks like a permanent issue on the Open Source communities, as I've seen this discussion today on [twitter][1]: 

> Hmm, I think I (and JS devs) just been told told to fuck off over semicolons: https://t.co/SwzuRAkaGc &mdash; @marcosc

[1]: https://twitter.com/marcosc/statuses/426130967758385152

It all started after a rejection from a [PR on Github][PR on Github] when a WHATWG spec editor refused to set a patch inserting semicolons to some JS code. The reason: *"I do not like semicolons"*.

[PR on Github]: https://github.com/whatwg/xhr/pull/16

He took it to a very personal taste and forgot the importance of the project he is editing. Forget about liking or not liking semicolons, focus on keep it consistent. The flaw was because the spec presents multiple code styles. I'm not arguing here that is needed to insert semicolons on every statement, although I like it. **I'm arguing that having 10% if the code with another style would lead some readers to deviate their attention for that differences**.

The more you keep consistency, more you focus on what's important.

Misleading the focus increases the chances for errors. The cited project on Github is of much importance to the Open Source community. It's a spec for `xhr` api on Browsers and that may also lead us to other problem, now not only speaking for inconsistency, but for the lack of semicolons: not every developer is a specialist and they may fail hard with ASI.

Think of a newbie JS developer that would like to know on how to use xhr API by reading that spec? That developer didn't read __Crockford__'s book or even __David Herman's Effective JS__ to hear a subconscious voice saying: "It's a trap!". 

That's only one good argument to choose for using semicolons, but it's also a statement on how the "I don't like it" argument looks fragile. Code consistency is important to not deviate the attention from unnecessary differences. In the spec case, you need to document and exemplify the xhr API.

It's easy to find a lot of Code Conventions as it is not hard to write a new one and it is ridiculous easy to adopt one to your project. Discuss with your team and keep to till the end as the master key of your Maintainable Code. You'll gonna have a good time pushing collaborators to adapt their patches to your projects' conventions, like mixed tabs and spaces, comments styles and ASI handling. 

If you don't know any convention guides yet, I recommend you my 2 favorites: 

- [Idiomatic.JS](https://github.com/rwaldron/idiomatic.js)
- [jQuery Code Style](http://contribute.jquery.org/style-guide/js/)

If you don't like spaces between the parenthesis, you can also try the [JS Code Style from B2G Gaia](https://developer.mozilla.org/en-US/Firefox_OS/Platform/Gaia/Hacking#Coding_style_basics). 
