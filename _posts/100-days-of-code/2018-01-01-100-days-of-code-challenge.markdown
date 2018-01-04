---
layout: post
title:  "100-days-of-code-challenge"
date:  2018-01-01
categories: programming
---

With a brand new year, comes a fresh start, a clean slate. I am going to begin
my new year with something I have just come across: [100daysofcode](http://100daysofcode.com/) challenge. 
I have forked the 100 days of code repo from github and am using the log to
track my daily progress. It will be fun, and it will be a great way to keep me
accountable for building my python knowledge. Here is an example snippet from
the code I did for day 1.

### Day 1:
{% highlight python %}

def gen_ssh_keypair():
    """ Generate an RSA private / public keypair """
    key = RSA.generate(2048)

    # generate private key - output to file
    with open('rsa_privkey.pem', 'wb') as privkey:
        privkey.write(key.exportKey())

    # generate public key - output to file
    with open('rsa_pubkey.pem', 'wb') as pubkey:
        pubkey.write(key.publickey().exportKey())

    return 0
    
{% endhighlight %}


### Day 2:
Today we are going to make a Discord chat bot. Bots have always been interesting to me.
Trying to make a computer program behave like a human sounds like a fun
challenge, and a great way to play some fun pranks on my friends on Discord.
So far, I have sketched up the initial framework in my python program using the
discordpy library. I will need to learn more about the following:
- asyncio
- coroutines
These seem to be two main concepts that this library uses, and it will help aid
my skills in the future when making programs that focus on performance.

### Day 3:
Today I could not find time to work on the coding aspect of the bot, but I did
grab some audio recordings that I need for the bot. I am mainly making this bot
to prank my friends in discord with voice recordings of funny moments that
occur in discord. I am going to make it queryable via prepending commands with
a !. I still did get to code today for work. I am working on some stuff in
python and I have to write unit tests, so I wrote a test for a couple of
functions
