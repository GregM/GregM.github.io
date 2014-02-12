---
layout: post
title: Shadow Dom Update No More Hats And Cats
date:   2014-02-07
categories: posts
---

The challenge with working with bleeding-edge technologies is that sometimes things change a lot between a beta release and a production release. Daniel Buchner of Mozilla wrote a great email to www-style with the subject *::Parts of cats and hats everywhere, slashed by shadow* that explains how the group arrived at the most recent proposal for styling elements in the Shadow DOM.

If you've been following the work to date, Google had hat (^) and cat (^^) in place in Google Chrome Canary. But, there was a lot of debate around using the ^ character in general. It was such a debate that Daniel wrote the primary concern for using it was that "it introduces YAACs (Yet Another ASCII Character) - pretty soon we'll need a periodic table to remember them all."

Out with: ```div ^^ #shadow-dom-id```

In with: ```div /shadow #shadow-dom-id```

In Daniel's words:

> An extensible combinator is the gift that keeps on giving. With an extensible combinator (ex: / + a token) we can define tokens like shadow, and shadow-all, to enable the styling of shadowed elements. The best part is we can introduce other tokens in the future without YAACing on our shoes. This proposal brings with it all the positives that hat-wearing cats deliver, without the downside of two new, non-obvious, ASCII combinators that are hard-bound to a specific DOM API. The only negative I can think of currently:

> 1. /shadow is longer than ^

> Assessment: this proposal hits on all cylinders - it allows users to write familiar selectors without knowing one-off token names, provides a predictable flow for shadow element styling, and is symmetrical to the JS DOM encapsulation paradigm.

> Example: x-foo /shadow div