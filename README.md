PocketVote
==========

PocketVote is a middleman service for both Minecraft Server Lists and Minecraft
Server Owners. It aims to drastically better how voting is done on MCPE. Gone is
the days of old.

How it works, the easy version.
===============================

**I am a server owner:**

1.  Register at [PocketVote.io/register](https://pocketvote.io/register).
2.  Add a server at [PocketVote.io/dashboard/servers/create](https://pocketvote.io/dashboard/servers/create).
3.  Go to [PocketVote.io/dashboard/servers](https://pocketvote.io/dashboard/servers).
4.  Click *Show secret* and copy your secret.
5.  Go to one of the [supported sites](#supported-sites)
6.  When prompted for your secret, provide the secret you got at PocketVote.io.
7.  Download one of the official plugins at [PocketVote.io](https://pocketvote.io/#services).

Please ensure that you **only** give your secret to sites you trust. If you
for some reason need to reset your secret you can do so in the same place
that you can view your secret.

**I am a server list operator:**

1.  Register at [PocketVote.io/register](https://pocketvote.io/register) and select “Server List Site” under *I have a*.
2.  Add a site at [PocketVote.io/dashboard/sites/create](https://pocketvote.io/dashboard/sites/create).
3.  Go to [PocketVote.io/dashboard/sites](https://pocketvote.io/dashboard/sites).
4.  Click *Show secrets*.
5.  Take note of the [JWT](http://jwt.io) secret and \_identity header.
5.  Look at [How it works, the developer version.](#how-it-works-the-developer-version)

How it works, the developer version.
====================================

This part is at the moment for server list sites only.

Make yourself familiar with [JWT.io](https://jwt.io/) as you will need to
understand it. It supports most languages available, so don’t feel required to
write your POST in one specific language.

In this example I will be using
[node-jsonwebtoken](https://github.com/auth0/node-jsonwebtoken) as an example.
You can install it by typing

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
this to your HTTP headers with the key **\_identity**

If you see “success”, you’re all golden.

Supported Sites
===============

If you own a server listing that supports PocketVote, open a [Github
Issue](https://github.com/ProjectInfinity/PocketVote/issues/new) and we’ll get
you added to the list.
