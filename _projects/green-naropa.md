---
layout: project
title:  "Green Naropa"
status: "Inactive"
excerpt: >
  Inspiring people to take small actions to reduce their climate footprint. And
  providing them with the resources they need to successfully do so.
---

The idea for Green Naropa was born late in 2015: Every year, people form resolutions
about changes they want to make in their lives or goals they want to accomplish. If
we made it easy and fun, could climate actions not easily be part of that list, too?

## Objectives

### Inspire Small Actions

Our goal was to inspire people to integrate small and easy actions into
their every day life. The first step was to provide people with a list of
actions that they could take. These actions were grouped in four major
categories: Transportation, Home Energy, Food, and Consumption.

<div class="row">
  <div class="col s6 m4 l3">
    <img class="materialboxed"
      width="100%"
      data-caption="Inspiring Small Actions: From re-using one's water bottle
      to biking more"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'screenshot_5.png' }}"/>
  </div>
</div>

Each category had about ten actions ranging from using a re-useable water
bottle to having more plant-based meals to borrowing and exchanging used
books rather than buying new ones.

None of these actions required major lifestyle changes &mdash; often times
people had already been wanting to do such things, but what was holding them
back was knowing how.

How many times have you considered offsetting your
carbon emissions from flights, but then did not end up doing it because
you did not want to spend the time researching and comparing the various
carbon emission offsetting websites? That's where our step 2 comes in.

### Provide Tips and Resources

Once people were inspired to integrate a few new good-for-the-climate practices
into their lives, we wanted to make it as easy as possible for them to succeed.
For us, that meant providing a list of tips and resources for each action that
would help with its implementation.

<div class="row">
  <div class="col s6 m4 l3">
    <img class="materialboxed"
      width="100%"
      data-caption="Did you know that each 12 ounce plastic water bottle causes
      0.15 pounds of CO2 emissions?"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'screenshot_5.png' }}"/>
  </div>

  <div class="col s6 m4 l3">
    <img class="materialboxed"
      width="100%"
      data-caption="Boulder has plenty of resources, so that you never have to buy
      a new book!"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'screenshot_6.png' }}"/>
  </div>
</div>

### Make a Commitment

And lastly, we wanted people to make a commitment on the website to their
actions. This was not only for them to hold themselves more accountable, but it
was also so that we could reach out to those who had made commitments to check
in on how they were doing as well as provide them with new tips and suggestions
regularly.

<div class="row">
  <div class="col s6 m4 l3">
    <img class="materialboxed"
      width="100%"
      data-caption="Did you know that each 12 ounce plastic water bottle causes
      0.15 pounds of CO2 emissions?"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'screenshot_4.png' }}"/>
  </div>
</div>

In addition, it allowed users to share their commitments publicly on Facebook,
Twitter, or Google+. A practice that, we imagined, would strengthen one's
commitment. In addition, it might also inspire that person's friends to take
on a few climate actions.

## Distribution Strategy
To spread awareness of the site, we put up twenty posters around the three
Naropa campuses. The posters came in four different varieties (see Posters
below) and were printed poster-size to be more eye-catching.

In addition, we worked with Naropa University, the Naropa Sustainability
Council, and the Student Union of Naropa &mdash; all of which shared a link
to Green Naropa on their Facebook pages.

Lastly, we attempted to encourage word-of-mouth propagation by making it easy
and convenient to share one's climate commitment goals on Facebook, Twitter, and
Google+.

## Impact

The resulting impact &mdash; compared to the time of development &mdash;
remained rather small.

<img class="materialboxed"
  width="100%"
  data-caption="Total of 403 page views, 192 visitors, and an average visit
  duration of two minutes"
  src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'analytics.png' }}"/>


As you can see from the analytics graph, visits spiked in the week after launch
in early February and then declined quickly. It shows that those people that
were interested in a website like this did not choose to return &mdash; and why
would they? There was nothing to keep their engagement going: Making a commitment
on this website was a one time action.

We were aware that we were not permanently engaging our visitors, but we had
hoped that we might go viral enough at Naropa University to draw in new users
every week. Thereby effectively keeping our number of visitors steady.

Since engagement dropped so quickly, we soon ceased continuing to work on the
website. Nothing had been happening in terms of updates or marketing since
at least April 2016, if not earlier.

In total, we had 43 signed up users for a total commitment count of 235.

## Resources

### Screenshots

<div class="row">
  {% for i in (1..4) %}
  <div class="col s3 m3 l3">
    <img class="materialboxed"
      width="100%"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'screenshot_' | append: i | append: '.png' }}"/>
  </div>

  {% endfor %}
</div>

<div class="row">
  {% for i in (5..7) %}
  <div class="col s3 m3 l3">
    <img class="materialboxed"
      width="100%"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'screenshot_' | append: i | append: '.png' }}"/>
  </div>

  {% endfor %}
</div>

### Posters

<div class="row">
  {% for i in (1..4) %}
  <div class="col s3 m3 l3">
    <img class="materialboxed"
      width="100%"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'poster_' | append: i | append: '.png' }}"/>
  </div>

  {% endfor %}
</div>

### Logos

<div class="row">
  {% for i in (1..4) %}
  <div class="col s3 m3 l3">
    <img class="materialboxed"
      width="100%"
      src="{{ page.url | prepend: '/images' | prepend: site.baseurl | append: 'logo_' | append: i | append: '.png' }}"/>
  </div>

  {% endfor %}
</div>

## Technical Details
- Domain: [http://www.greennaropa.org/](http://www.greennaropa.org/)
- Language/Framework: Ruby on Rails
- Server: 512 MB VPS (DigitalOcean)

## Source Code
Check out the source code on [Github][green-naropa-source-code].

[green-naropa-source-code]: https://github.com/fwoelm/netzero
