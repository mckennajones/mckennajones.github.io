---
title: "This site is now served from a cabinet in my living room"
date: 2025-09-16
---

If you're able to read this then you've successfully fetched this site from my mini server in the cabinet under the TV in my living room. I'm using [Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) to do so. Let's talk a little bit more about it below.

## Why Even Bother Self Hosting This?

It's a valid question. And honestly for some, the answer might be that it's not worth the effort. Previously I was hosting this using GitHub Pages, which works great. You don't have to think about nearly anything. Connect your domain, setup a GitHub Actions workflow and you're off to the races.

But to me it was missing a couple of key things: ownership, control, and visibility. 

Over the past couple years I have jumped head first into the [Self Hosting](https://en.wikipedia.org/wiki/Self-hosting_(web_services)) world (more on that in a later post), which has really picked up in popularity recently. Even [PewDiePie has joined the movement](https://youtu.be/u_Lxkt50xOg?feature=shared). Needless to say I've started to value more and more the ability to control my own data.

With GitHub Pages you gain no insight into who is accessing your site. And while I generally respect GitHub as a company, relying on them to serve something so personal feels a little wrong.

Finally, there is of course the "it's fun" argument. I don't think I am alone in feeling this way. It's simply cool and satisfying to put something out on the internet that is running in your living room.

## How?

There are a couple ways I considered accomplishing this:
- Open a port on your router - Obvious security concerns here. And would depend on you having a static IP with your ISP.
- [Tailscale Funnel](https://tailscale.com/kb/1223/funnel) - I already use Tailscale for accessing my self-hosted services when I'm away from home, so this seemed like a good choice. However, the main thing it's missing is bringing your own domain name, which made it a non-starter for this use case.
- [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-networks/) - Basically the same as above, but using Cloudflare's network.

Cloudflare Tunnels ended up being the best for my use case. I was already using them for DNS on mckennajones.com and mckjns.com, so the setup was fairly painless. Basically it just included this:
1. Install the cloudflared daemon on my server.
2. Run my website locally. It's wrapped up in a [super simple Docker container](https://github.com/mckennajones/mckennajones.github.io/blob/main/Dockerfile) using Nginx.
3. Create the Tunnel in the Cloudflare Dashboard, pointing to the appropriate port of the Docker container, and using the correct domain name.
4. Start the cloudflared daemon with the tunnel token.
5. It just works 🎉

Now, you might argue that relying on a company like Cloudflare goes against the nature of self-hosting. And I partially agree, but I think it's a fair price to pay in order to securely do something like this.

## Does it perform well?

In my limited testing, it seems so! I ran basic tests using the synthetic monitoring that is available on Cloudflare and my newly self-hosted site performs basically identically to the GitHub Pages site. Do let me know if you experience any slow loads though!