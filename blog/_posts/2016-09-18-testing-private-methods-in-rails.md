---
layout: post
title:  "Testing Private Methods in Rails"
date:   2016-09-18
categories: rails
excerpt: >
  How I test private and protected methods in Rails 5 using RSpec and the
  .send(...) method.
---

{{ page.excerpt }}

When you get serious about testing your Rails applications, you will sooner
or later start testing every single method of your models. When that happens,
you will undoubtedly encounter the scenario of wanting to test your models'
private methods.

Usually you test methods by calling them on the model, like so:
`user.send_welcome_email`

<br/>
This won't at all work for private or protected methods. When I try to
test a private method in the same way, Rails (and RSpec) complain:

~~~
NoMethodError:
       private method `my_private_method' called for #<User id: 1>
~~~

<br/>
However, testing private methods is actually very simple. Just use the
`.send(:method)` function, where `:method` is the name of the private method
you are trying to test. Our example from above becomes:

~~~
user.send(:my_private_method)
~~~

<br/>
To pass arguments, simply add them:

~~~
user.send(:my_private_method, "some argument")
~~~

<br/>
There is actually a heated debate about whether private methods should be tested
at all. I will let you make that call.
