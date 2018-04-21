<!--
.. title: Heterarchy: Decentralization and Federation in Social Networking
.. slug: fediverse
.. date: 2018-04-21 11:25:41 UTC-04:00
.. tags: fediverse, mastodon, social networks, microblogging
.. category: 
.. link: 
.. description:  An idiosyncratic primer on the fediverse for friends and colleagues, particularly in academia.
.. type: text
-->

Despite its hifalutin title, this is not a theoretical or (primarily) political essay. It's rather meant as an idiosyncratic primer on the "fediverse" for friends and colleagues (particularly in academia) who have heard about or are looking for "something different/better than Twitter/Facebook/etc." Caveat: <abbr title="I am not an expert">IANAE</abbr>, but after a few weeks dipping my toes into the fediverse I find that I can answer some basic questions at least provisionally. Everything I offer here was gleaned from web searches (I use [DuckDuckGo](https://duckduckgo.com/), at present), from trying things out, from watching other people do things, from talking to friends, and from reading especially these posts:

 - [Ruth Kitchin Tillman](https://glammr.us/@platypus). [“Overview of Mastodon & Why I Like It.” _Ruth Kitchin Tillman_](http://ruthtillman.com/mastodon-overview/) (blog), November 14, 2017.

 - Seth Kenlon. [“A Beginner’s Guide to Microblogging on Mastodon.” _Opensource.com_](https://opensource.com/article/17/4/guide-to-mastodon) (blog), April 6, 2017.

You may find reading them first to be more rewarding that continuing below the fold here immediately.

<!-- TEASER_END -->

## Why

It's not hard to find legitimate complaints and concerns about the dominant services in social media today (see, for example, [Zeynep Tufekci's column in the _New York Times_](https://www.nytimes.com/column/zeynep-tufekci)). Some people are reacting by seeking alternative social communication mechanisms that differ from Twitter, Facebook, and the like by being less centralized, providing more privacy options, and protecting personal information from exploitation. The ascendant alternatives are, for the moment, coalescing around an open standard for exchanging social networking information over the web called ActivityPub.

## What

__ActivityPub__ has recently been formalized as [a W3C Recommendation](https://www.w3.org/TR/activitypub/). It specifies "a client/server <abbr title="application programming interface">API</abbr> for creating, updating and deleting content" ([Wikipedia](https://en.wikipedia.org/wiki/ActivityPub)). Here, "content" means data commonly used in social media or micro-blogging environments like status updates, image posts, direct messages, and hashtags. By "client" we mean a program running on your computer, phone, or table.  ActivityPub also provides for server-to-server exchange of notifications and content. Using this protocol, multiple copies of software installed on different servers under separate administrative control could potentially __federate__ to create a decentralized, distributed network that differs from the centralized, top-down-managed systems most social media users know today. ActivityPub would permit individuals to connect and communicate each other, via client connections through one of these servers and, thanks to the server-to-server federation, across other servers to their connected clients' users.

In fact, a social network __fediverse__ based on ActivityPub has emerged. The best-known software tool used to set up a federated server is called __[Mastodon](https://github.com/tootsuite/mastodon)__. Its creators, led by [Eugen Rochko](https://mastodon.social/@Gargron), describe it as follows:

> Mastodon is a free, open-source social network server based on open web protocols like ActivityPub and [OStatus](https://en.wikipedia.org/wiki/OStatus). The social focus of the project is a viable decentralized alternative to commercial social media silos that returns the control of the content distribution channels to the people. The technical focus of the project is a good user interface, a clean [<abbr title="Representational state transfer">REST</abbr> API](https://en.wikipedia.org/wiki/Representational_state_transfer) for 3rd party apps and robust anti-abuse tools.

Note that you will often see, [even in Rochko's own writing](https://hackernoon.com/welcome-to-mastodon-111d9227e56a), some slippage in terminology. "Mastodon" is often used to connote the entire federated network, rather than just the server software. But in fact, there are other software packages that make use of ActivityPub and can (or potentially can) federate with Mastodon servers (e.g., [Hubzilla](https://project.hubzilla.org/page/hubzilla/hubzilla-project) and [Pleroma](https://git.pleroma.social/pleroma/pleroma)). More are likely to emerge. 

_Yes, I'm leaving aside [GNU Social](https://gnu.io/social/) for now, since [it hasn't yet added full ActivityPub support alongside OStatus](https://git.gnu.io/gnu/gnu-social/issues/256)._

## How

The basic steps to get started microblogging in the fediverse are:

 - Find and join an "instance"
 - Connect to your new account on your host instance 
 - Find and follow friends, colleagues, and other accounts of interest
 - Do that thing you do

### Finding and joining an instance

The word __instance__ is often used as a generic term for a copy of Mastodon running on a particular server. Each instance is separately established and administered, and they each have their own themes (or not), rules, moderation practices (or not), and so on. Rochko and the other core developers of Mastodon run one of the biggest instances, [mastodon.social](https://mastodon.social/about), but there are over 2,500 instances in the fediverse at the time of this writing. To find one you like and think you can trust, you can try the flagship [join.mastodon.org](https://joinmastodon.org/) site. There's also [instances.social](https://instances.social/), which is operated by the maintainer of another big, general-purpose instance,  [mastodon.xyz](https://mastodon.xyz/about).

Although I initially explored options with both of these tools, in the end I took a different approach to finding an instance to join. I sought out friends and colleagues who were already using Mastodon and looked into the instances they were using. In addition to the two listed above, I found out about three more that I'll mention here since they might be of interest to my intended audience. 

__Scholar.social__ is a small instance (less than 1,000 people), run by Benjamin Carlisle at McGill University. He describes its focus as follows:

> scholar.social is meant for: researchers, grad students, librarians, archivists, undergrads, academically inclined high schoolers, educators of all levels, journal editors, research assistants, professors, administrators—anyone involved in academia who is willing to engage with others respectfully.

__glammr.us__ is (at present) a very small instance, run by [@joshuatj@glammr.us](https://glammr.us/@joshuatj):

> glammr.us is a space for folks interested in productive conversation about, well, galleries, libraries, archives, museums, memory work and records. It is pronounced “glamorous” as our work is often charmingly or fascinatingly attractive, especially in a mysterious or magical way. Sometimes it is also full of excitement, adventure, and unusual activity (oh, yes). It is also inspired by Toys’R’us to showcase the fun playful side of glammr.us tooters. But you don't necessarily have to only post about GLAMMR-related topics, bring your whole self. Talk about fun things you saw, your exciting day or even your struggles. Many of us are Twitter refugees looking for an inclusive and community-supported approach to social media. If any of these things sound good to you, consider joining us by contributing as little as a $1 a month on patreon to help keep our server online.

[Glammr.us has an online code of conduct](https://glammr.us/about/more) (scroll down the page). 
 
__Social.coop__ is owned and operated (and co-financed) by a formal co-operative, with established bylaws that dictate open, democratic policy-making. I applied to join the coop because of that openness and the bylaws and participatory governance as a bulwark against arbitrary administrative actions. And they clearly had healthy administrative and technical [bus numbers](https://en.wikipedia.org/wiki/Bus_factor). Happily, I was accepted as a co-owner and member.

Once you've picked an instance and worked through whatever application/joinup/payment process that instance has in place, you'll want to establish some sort of profile and start following others and producing content. Mastodon instances provide a default web experience, subject to customization by the instance admins. There are also a growing number of mobile apps for connecting to your instance. On my OSX laptop, I connect to the social.coop instance's web interface using Firefox. On my iphone, I use [John Gabelmann's _Amaroq for Mastodon_](https://itunes.apple.com/us/app/amaroq-for-mastodon/id1214116200?mt=8).

## Finding and following other people

Many of the people I know from my meatspace and/or <span title="people on Mastodon tend to use 'birdsite' as a substitute for the name 'Twitter'">birdsite</span> social networks who were also already in the fediverse were either on mastodon.social or scholar.social, rather than my home instance social.coop. No matter their instance, following them (once logged into my social.coop account) was as easy as visiting the webpage corresponding to their Mastodon profile. 

So, for example, I typed the following into my search engine:

> eric kansa mastodon

I clicked through the results to [https://octodon.social/@ekansa](https://octodon.social/@ekansa). Once there, I clicked "remote follow":

<img src="/images/fediverse/remote_follow.png"/>

You may also be able to find people you know by typing their names into your Mastodon instance's search box, but your results may depend on whether anyone else on your instance is already following someone from the other instance (or other techno-administrative factors that at present I only vaguely intuit). Search is also your friend for finding people with similar interests. Imagine a hashtag and search for it; see who uses it. Watch your "Local Timeline" (i.e., every post on your instance) for users and topics of interest. Dip into the firehose of the "Federated Timeline" to sample the fediverse _Zeitgeist_.

<abbr title="For What It's Worth">FWIW</abbr>, the core developers of Mastodon also run https://bridge.joinmastodon.org/, which is supposed to help you "find your friends on Mastodon." I haven't used it either, because it requires authenticated access to your Twitter account.

## Microblogging

Most instances I've seen suggest you offer a self-introduction (using the #introductions hashtag) in the interest of explaining yourself to other folks on your local timeline. Consider your privacy before you do this: Mastodon gives you the ability to limit the scope of your posts ("toots" are the domain-specific term) to "public" timelines, only non-public timelines (i.e., instance-internal), "followers only", or "direct" (i.e., only to individuals whose accounts you mention in the post itself).

Here's [my initial introduction](https://social.coop/@paregorios/99644416200468402) and [a follow-up introduction](https://social.coop/@paregorios/99836014294446671) I made after watching what other people were doing in that regard. I'm not sure whether either of them is all that great, so you might lurk for a few days and watch how others on your instance behave. You can look for more by searching for the hashtag #introductions. Don't be surprised if someone on your instance (admin or otherwise) initiates contact to welcome you and encourage an #introductions post.

## Crossposting

Some people like to cross-post from birdsite to their Mastodon instance (or vice versa). I haven't tried myself, but I've seen people recommend:

 - [t2m](https://github.com/YoloSwagTeam/t2m)
 - [Mastodon Twitter Crossposter](https://crossposter.masto.donte.com.br/)

## Now What

Now, I'd suggest that if you haven't yet read the blog posts cited above [from Ruth Tillman](http://ruthtillman.com/mastodon-overview/) and [from Seth Kenlon](https://opensource.com/article/17/4/guide-to-mastodon), now would be good time. Reading both of them will give you a broader introduction than I've tried to lay out here.





