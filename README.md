Emfed: Simple Client-Side Mastodon Feed Embedding
=================================================

Twitter used to have a really convenient way to embed a feed into your website, but now Twitter is dead.
Emfed is a simple replacement for [Mastodon][] that works entirely in the browser, without a server-side component (beyond your favorite Mastodon instance itself).

To use it, put a special link like this where you want the feed to appear:

    <a class="mastodon-feed"
       href="https://mastodon.social/@Mastodon"
       data-toot-limit="4"
       >follow me into the Fediverse</a>

Then include the JavaScript (probably at the end of your `<body>`):

    <script type="module" src="https://esm.sh/emfed"></script>

Emfed generates some pretty basic markup for the feed.
You probably want to style it to look like a proper social media feed, which you can do with plain ol' CSS scoped to the `.toots` selector, or you can use its provided CSS (in your `<head>`):

    <link rel="stylesheet" type="text/css"
          href="https://cdn.jsdelivr.net/gh/sampsyo/emfed@main/toots.css">

You can customize the feed with `data-` attributes:

* `data-toot-limit`: The maximum number of toots to display.
* `data-toot-account-id`: Emfed needs to make an extra API request to translate your human-readable username (like `@Mastodon`) into an internal ID (like 13179) before it can look up your toots. If you have [empathy for the machine][eftm], you can make everything faster by specifying the ID directly here.

Emfed sanitizes the HTML contents of toots using [DOMPurify][] to avoid malicious markup and XSS attacks.

[mastodon]: https://joinmastodon.org
[eftm]: https://atp.fm/115
[DOMPurify]: https://github.com/cure53/DOMPurify

Alternatives
------------

* [Mastofeed](https://www.mastofeed.com): A server-side iframe-embeddable feed generator.
* [Fedifeed](https://fedifeed.com): Like Mastofeed, but for other ActivityPub software too.
* [untitled embed script from idotj](https://gitlab.com/idotj/mastodon-embed-feed-timeline): Also client-side. I wanted something with secure HTML embedding, automatic username lookup, and simpler URL-based configuration.

Author
------

Emfed is by [Adrian Sampson][adrian].
It is dedicated to the public domain under the terms of [the Unlicense][unl].

[adrian]: https://www.cs.cornell.edu/~asampson/
[unl]: https://unlicense.org