PocketVote
==========

[Get help or talk to developers on Discord!](https://discord.gg/B4WHSSq)

PocketVote is a middleman service for both Minecraft Server Lists and Minecraft
Server Owners. It aims to drastically better how voting is done on MCPE. Gone is
the days of old.

PocketVote is completely free to use, however any donations to cover the operational costs of PocketVote is gladly accepted.

*You can send Bitcoin (BTC) to the following address to support PocketVote: **3QC8XUfjXQSMg4CKvvQdscMPQts5wxM9su***

How it works, the easy version.
===============================

**I am a server owner:**

1.  Register at [PocketVote.io/register](https://pocketvote.io/register).

2.  Add a server at
    [PocketVote.io/servers](https://pocketvote.io/servers/create) by clicking the add server button.

3.  Click *Show Secrets* and copy your secret.

4.  Go to one of the [supported sites](#supported-sites)

5.  When prompted for your secret, provide the secret you got at PocketVote.io.

6.  Download one of the official plugins at
    [PocketVote.io](https://pocketvote.io/#services).

7.  Use the identity generated at
    [PocketVote.io/dashboard/servers](https://pocketvote.io/dashboard/servers)
    and follow the plugin instructions on how to utilize the identity.

[Instructions for PocketMine available
here](https://github.com/ProjectInfinity/PocketVote/blob/master/POCKETMINE.md)*.*

Please ensure that you **only** give your secret to sites you trust. If you for
some reason need to reset your secret you can do so in the same place that you
can view your secret.

**I am a server list operator:**

1. Register at [PocketVote.io/register](https://pocketvote.io/register) and
    select “Server List Site” under *I have a*.

2. Add a site at
    [PocketVote.io/dashboard/sites/create](https://pocketvote.io/dashboard/sites/create).

3. Go to
    [PocketVote.io/dashboard/sites](https://pocketvote.io/dashboard/sites).

4. Click *Show Secrets*.

5. Take note of the [JWT](http://jwt.io) secret and Identity header.

6. Look at [How it works, the developer
    version.](#how-it-works-the-developer-version)

How it works, the developer version.
====================================

**Server list operators:**

Make yourself familiar with [JWT.io](https://jwt.io/) as you will need to
understand it. It supports most languages available, so don’t feel required to
write your POST in one specific language.

In this example I will be using
[node-jsonwebtoken](https://github.com/auth0/node-jsonwebtoken). You can install
it by typing

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
npm install jsonwebtoken
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For use with PocketVote we will be utilizing standard HMAC SHA256 so you can do
the following:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
var jwt = require('jsonwebtoken');
var token = jwt.sign({ player: 'Steve', ip: '127.0.0.1', server: SECRET_YOU_GOT_FROM_SERVER_OWNER}, JWT_SECRET_YOU_GOT_FROM_POCKETVOTE);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Your token is now ready to be sent. Make sure you send the token parameter with
the name *token*.

When sending a request to PocketVote, you need to make sure that the target
address is **https://api.pocketvote.io/vote** failure to do so will reject your
request. The method also has to be **POST**.

In order to identify you, you’ve been given a UUID by PocketVote.io, please add
this to your HTTP headers with the key **Identity**

Do note that if your JWT library does not automatically insert a timestamp (iat)
then you **must** do this yourself.

If you see “success”, you’re all golden.

 

**Plugin developers:**

To run your code when a vote is registered simply listen to the **VoteEvent**.
You can get the IP, player name or site name through the event object.

Supported Sites
===============

If you own a server listing that supports PocketVote, open a [Github
Issue](https://github.com/ProjectInfinity/PocketVote/issues/new) and we’ll get
you added to the list.

- [Minecraftlist.org](https://minecraftlist.org/)

- [minecraftpocket-servers.com](http://minecraftpocket-servers.com)

- [Minecraft-PE-Servers.com](https://minecraft-pe-servers.com)

- [MinecraftPE-Servers.com](https://minecraftpe-servers.com/)

## Support on Beerpay
Hey dude! Help me out for a couple of :beers:!

[![Beerpay](https://beerpay.io/ProjectInfinity/PocketVote/badge.svg?style=beer-square)](https://beerpay.io/ProjectInfinity/PocketVote)  [![Beerpay](https://beerpay.io/ProjectInfinity/PocketVote/make-wish.svg?style=flat-square)](https://beerpay.io/ProjectInfinity/PocketVote?focus=wish)