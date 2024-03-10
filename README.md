# FreeBird
A guide for self-hosting a Nitter instance

## Why
[Nitter](https://github.com/zedeus/nitter) is a fantastic alternative frontend for Twitter. Instead of using Twitter's official web interface or app, which contains ads or algorithmic contents that you may not like, Nitter enables you to **browse** Twitter content without those potential distractions. Nitter also exposes Twitter contents as RSS feeds so that you can 1) view them in an RSS reader 2) manipulate them programatically, such as crossposting to Mastodon, filtering and archiving.

If this sounds interesting to you, read on.

There were once [public Nitter instances](https://github.com/zedeus/nitter/wiki/Instances) that you can just use. However, with some [recent changes happening on Twitter's side](https://github.com/zedeus/nitter/issues/983), it's becoming increasingly hard for people to host public Nitter instances.

However, regardless of the demise of public Nitter instances, it is still possible to use Nitter as long as you host your own instance and use it on a personal scale only, and this is a guide that helps you do exactly that.

## What can you expect
* A [Nitter](https://github.com/zedeus/nitter) instance
    * Notice that only 1) viewing profiles and 2) view individual tweets are the pages/RSS feeds that I personally use and can commit offering support to. I personally cannot commit to offering support for other pages/RSS feeds such as search.
    * The Nitter instance is also protected by either 1) an nginx instance that password-protects all web interfaces and RSS feeds or 2) a Tailscale private network so that only you on your personal devices can access the Nitter instance. The reason for such protection is rampant web scrapers that can cause your instance to be heavily rate limited by Twitter's servers.

Depending on the setup you pick later, you can optionally have
* A [miniflux](https://github.com/miniflux/v2) instance that can poll Twitter accounts from the Nitter instance as RSS feeds
    * Depending on the volume of Twitter accounts that you want to follow, the miniflux instance may not be able to poll the absolutely latest tweet timely.
    * A custom polling scheduler for Miniflux is included so that instead of polling all accounts all at once and causing the Nitter instance to be rate-limited, Twitter accounts are polled one by one and with random time intervals in between.
* A [rss-lambda](https://github.com/k-t-corp/rss-lambda) instance that you can use to perform operations such as filter by keyword on RSS feeds.
* A [nitter-xposter](https://github.com/k-t-corp/nitter-xposter) instance that you can use to crosspost from (public) Twitter accounts to Mastodon and Bluesky accounts

## What do you need
* A **burner/temporary** Twitter account **without 2FA enabled** (sign up [here](https://twitter.com/i/flow/signup))
* Some Linux and terminal knowledge

## Decide where to host the Nitter instance
* [fly.io, a Platform-as-a-Service hosting provider](https://fly.io/) -> [go to the "Host on fly.io" section](#host-on-flyio)
* A server or NAS -> [go to the "Host on a server or NAS" section](#host-on-a-server-or-nas)

## Host on fly.io
With the fly.io setup, you will get a personal, password-protected Nitter instance on the Internet.

Although fly.io is a paid platform, the setup uses as minimal as possible resources and your usage should fall into their free tier as long as you keep it just for personal usage.

You need a computer with Docker installed (verify by running `docker run hello-world` and `docker compose -v` if you are unsure), then follow this guide

[Host on fly.io](./docs/host-on-fly-io.md)

## Host on a server or NAS
You need a server or NAS running Linux on x86_64 or arm64 with Docker installed (verify by running `docker run hello-world` and `docker compose -v` if you are unsure)

Depending on what you specific components you want from the `What can you expect` section, you may pick one of the following setups

* [I want everything! (without crossposting)](./docs/i-want-everything-without-crossposting.md)
* [I only want a Nitter instance and without Tailscale](./docs/i-only-want-a-nitter-instance-and-without-tailscale.md)
* [I only want a Nitter instance and crossposting without Tailscale](./docs/i-only-want-a-nitter-instance-and-crossposting-without-tailscale.md)

## Like what you see?
Consider support us on [Patreon](https://www.patreon.com/sekaisoft) :)
