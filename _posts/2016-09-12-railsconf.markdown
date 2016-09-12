---
layout: post
title:  "Rails Conf 2016"
date:   2016-09-12 13:00
categories: conference rails
author: Jessica Dussault
---

I've been sitting on this blog post for several months now, so my apologies for a rather late update!  In May the dev team (Karin, Greg, and I) headed to Kansas City for the Ruby on Rails 2016 conference.

![Rails Conf Xing]({{ site.url }}assets/2016-09-12/railsconf.png)

<div class="img_caption">People in the conference hotel thought that there was a train convention going on.</div>
<!-- image source: http://railsconf.com/assets/railsign@2x-1a72e3f7754db1202dc8273bc86b4cbad70848a6208aab92a38d5eaa44cfa437.png -->

Most of our dev team was not particularly familiar with Rails before going.  I had worked haphazardly with Rails, but not with ActiveRecord (which is kind of the heart of Rails, in my opinion).  I was interested in hearing about general Rails advice, Rails 5 news, and interesting features I might not have heard about from just getting some basic apps set up.  Karin was really interested in the asset pipeline, design, and dev team management.  Greg spent a lot of time in the security track.  

I was happy to get my history fix in when one of the keynotes addressed dev team organization using [Skunk Works](https://en.wikipedia.org/wiki/Skunk_Works) as an example of [creative team structure and the importance of thinking outside the box](https://www.youtube.com/watch?v=ggPE-JHzfAM&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=2).

![Skunk Works Logo]({{ site.url }}assets/2016-09-12/skunkworks.png)

<div class="img_caption">If you don't know what Skunk Works is, I recommend <a href="https://en.wikipedia.org/wiki/Skunk_Works">reading about it</a>.  Particularly if you like things like the SR-71!  And who doesn't?</div>
<!-- image source: By Source, Fair use, https://en.wikipedia.org/w/index.php?curid=13354884 -->

Here are some of the talks which I found very interesting.  I'm sure that Karin and Greg have more they would recommend, too!

## Making a Rails App with 140 Characters (or less) by Nate Berkopec

[Making a Rails App with 140 Characters](https://www.youtube.com/watch?v=SXV-RRsjsFc&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=4)

Nate Berkopec's talk was good old fashioned fun.  He took an almost inane idea and made it incredibly interesting.  While he cavalierly ripped code from the framework, I learned a lot about all of the libraries that Rails loads up, how things are loaded, when they are loaded, why they are loaded, and if they MUST be loaded.

{% highlight bash %}
rackup \
-r action_controller/railtie \
-b 'run Class.new(Rails::Application)(config.secret_key_base=?x).initialize!'
{% endhighlight %}

<div class="img_caption">"All this application can do is serve empty 404 responses.  But it is a Rails application!!!" -- Nate Berkopec</div>


## Multi-table Full Text Search with Postgres by Caleb Thompson

[Multi-table Full Text Search](https://www.youtube.com/watch?v=OzHhJPlgZaw&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=27)

This is one that is noteworthy because I ....pretty much completely disagreed with the presenter.  Thompson did an admirable job connecting tables in a massive query that I surely would have struggled with substantially, but the whole time I was thinking "why don't you just use Solr or Elasticsearch?"  He did address them at the end, but said he didn't want to use tools like Solr or ES because it would add to the technology stack (true) and that then you need additional steps to populate them and keep them in sync with your databases (also true).  However, at a certain point, it seems like the time spent upfront getting one of those types of tools set up would vastly outweigh running gigando queries constantly.  I might be biased since we use Solr quite a bit here.

## RSpec and Rails 5 by Justin Searls

[RSpec and Rails 5](https://www.youtube.com/watch?v=vntVoC5uSYk&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=82)

This presentation was one of the more memorable ones of the conference.  He started quite a discussion that people were still talking about over meals and snacks a few days later.  Searls was not actually supposed to be presenting on RSpec, but stood in when the original speaker was unable to attend, so it might not be that surprising that his talk was not nearly as much about RSpec as it was about the state of the Rails community.  Searls is an incredibly gifted speaker and really pulled the audience along on a fun adventure...at least it was fun until he went Real Talk on us.  

> "When an ecosystem is popular everything is easy, cuz there's just, you know, wave after wave of person on the internet who's gonna write open source for free just for the ego, just for the fame, to be attributed to the new, popular thing."

He goes on to explain that things like Java, Go, and JavaScript are unlikely to die out because large companies are relying upon them and therefore will lend their support to maintaining them.  Rails, on the other hand, largely depends on a volunteer community.  But once something like Rails matures, then "when you maintain a popular gem like RSpec it no longer makes you rich and famous."  

Searls is concerned that as it ages, Rails will no longer have the vibrant community that it once did.  The talk was extremely relevant, as one of the primary maintainers of Sprockets had [recently excused himself from working on it](http://schneems.com/2016/05/31/saving-sprockets.html), leaving a huge void in his wake.

![Image of Richard Schneeman as Indiana Jones]({{ site.url }}assets/2016-09-12/sprockets.jpg)

<div class="img_caption">"Sprockets, why did it have to be sprockets?" - from Richard Schneeman's talk titled <a href="https://www.youtube.com/watch?v=imE397wVWgY">Saving Sprockets</a></div>
<!-- image source: http://www.sandimetz.com/99bottles -->

## Succession by Katrina Owen

[Succession](https://www.youtube.com/watch?v=59YClXmkCVM&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=81)

This talk was probably my favorite talk of the entire conference.  It was essentially just a step by step demo of how to refactor some code, presented in an incredibly approachable way.  Because of my unorthodox introduction to programming ("So, your CV says that you 'learn things pretty fast and stuff and probably you could learn to program?'"), I often feel like I'm lacking some basic knowledge that other devs magically know.  Code design practices and refactoring tips are among them, so I was really enchanted by Owen's presentation.

Owen is also the creator of [Exercism](http://exercism.io/) which provides interesting programming challenges in different languages, which received a burst of applause when she mentioned it at the conference, so that might be an interesting resource to try out sometime.

<img src="{{ site.url }}assets/2016-09-12/exercism.svg" 
  height="100px" alt="Exercism Logo"/>

<div class="img_caption">It has a pretty sweet logo, too.</div>
<!-- image source: http://exercism.io/icons/logo.svg -->

## Get a Whiff of This by Sandi Metz

[Get a Whiff of This](https://www.youtube.com/watch?v=PJjHfa5yxlU&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=78)

I said that Owen's talk on Succession was my favorite presentation at the conference, but honestly it's really hard for me to say that this wasn't also my favorite talk.

I was reminded of early in my programming life when when of my coworkers said he was nervous anytime he saw a "private" JavaScript method being called anyway other than `this._blah()`.  That is, if you say `this.some_other_class._blah()` then you should consider rethinking why you're doing that at all.  That was the first time I learned about "code smell" though it would be until this summer's Rails Conf to realize that it was, in fact, "code smell."

I was vaguely familiar with the term "code smell" but I didn't know much about it.  I certainly didn't know that people have been compiling lists of warning signs and recipes for corrective steps to take.  I took pages of notes during the talk, and I intend to do a lot more reading on the topic.  I spent some time almost immediately after the convention rethinking and refactoring some code, and I credit Owen and Metz for points of inspiration there.

![99 Bottles of OOP book cover]({{ site.url }}assets/2016-09-12/99bottles.jpg)

<div class="img_caption">Since I liked Metz and Owen on their own, I'm guessing that <a href="http://www.sandimetz.com/99bottles">their book</a> is AWESOME.</div>
<!-- image source: http://www.sandimetz.com/99bottles -->

## Closing Keynote by Paul Lamere of Spotify

[Closing Keynote](https://www.youtube.com/watch?v=f7XN3RuDzmc&list=PLE7tQUdRKcyZGYLfj6oRQWPxB6ijg1YsC&index=89)

One of the most interesting and enlightning talks of the entire conference was the final keynote.  Paul Lamere of Spotify spent an hour talking to us about the interesting things that Spotify is doing with user data, audio manipulation, music generation, and more.  This talk was not particularly specific to Rails, but it was fascinating.  I really recommend taking a listen to it if you have a spare hour of your time.  Sadly, the American Sign Language interpreters did not make it into the official conference video, which is a tragedy because they were amazing during this keynote.  On the fly, they had to interpret everything from metal to rap to pop and did a fantastic job!  It was a great way to end the Rails Conference, and I'm glad that we had the opportunity to experience it!
