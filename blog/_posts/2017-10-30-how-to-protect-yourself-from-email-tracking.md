---
layout: post
title:  "How to Protect Yourself from E-Mail Tracking"
date:   2017-10-30
categories: personal
excerpt: "Nowadays, email tracking is everywhere. Don't like it? You can protect yourself."
---

Nowadays, email tracking is everywhere. In every newsletter, in most commercial
email, and even an increasingly large number of individuals are using tools like
[Mailtrack](https://mailtrack.io/) to learn when and how many times their emails
have been opened.

![Mailtrack in Google Inbox]({{ "/images/posts/2017-10-30-how-to-protect-yourself-from-email-tracking/mailtrack.png" | prepend: site.baseurl }})  
Example of Mailtrack in Google Inbox.
[Image Source](https://ca.finance.yahoo.com/news/mailtrack-io-shows-email-read-171502787.html)

These email trackers work by inserting a 1x1 transparent image into the emails
you sent out. That transparent image has a URL that is unique to each email you
send.

For example, it could be: *https://mailtrack.io/trace/mail/6a583DAOda=7fe7a261f0a33d64870252b85c0d62ddf88e6.png?u=3BNQD2125830*

Now, when your recipient then opens that email, their web browser makes a
request to that unique URL to load the image. Mailtrack - or whatever
application you are using - is tracking those incoming requests. Based on the
URL of the request, Mailtrack knows which email is being read by whom.

I appreciate that hack for its ingenuity. But I don't always want people to know
whether or not I have read their emails. It's my mail, it's my inbox - I will
read my mail when and how I want.

To protect yourself from e-mail tracking, you need to prevent your browser from
loading that transparent tracking image. Fortunately, if you're using Gmail, it
is rather straightforward.

Here we go:  
1. Go to your [**Gmail Settings**](https://mail.google.com/mail/#settings/general)
2. Scroll down to the section labeled '**Images**'
3. Select '**Ask before displaying external images**'
4. Scroll to the bottom and click '**Save Changes**'

The next time you receive an email with tracking, you will see that images have
been prevented from auto-loading. Here is an email from my friend Jessy in which
I successfully prevented mailtracking:

![Prevented Mail Tracking]({{ "/images/posts/2017-10-30-how-to-protect-yourself-from-email-tracking/prevented-mailtrack.png" | prepend: site.baseurl }})  

If you also use Google Mail on your phone, you may want to turn off automatic
image loading there, too. Check out this article for instructions:
[https://support.google.com/mail/answer/145919](https://support.google.com/mail/answer/145919)
