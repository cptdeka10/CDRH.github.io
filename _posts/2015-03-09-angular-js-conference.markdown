---
layout: post
title:  "ng-conf 2015 Live Streaming"
date:   2015-03-09 10:00
categories: conference
author: Jessica Dussault
---

Thursday, I took a road trip to Omaha to watch the [ng-conf](http://www.ng-conf.org/) (angular.js conference) with some nice folks from [The Garage by Aviture](http://garagebyaviture.com/).  I have very little experience with angular besides scanning through their docs a few times, but I thought it would be interesting to see what kinds of features and applications they would be touting at their conference.  Though most of my observations were a bit superficial, since I don't have extensive knowledge about Angular's inner workings, I found plenty to think about with regard to current projects at the CDRH.

#### The Death of jQuery (or at least an alternative)
This I got less from the presentations themselves and more from the programmers working at Aviture, who have been using Angular for a year or so.  The feeling I got from them, overall, was that there was a bit of a learning curve to get into it, but then once you understood how everything works Angular is a dream to use.  One of the devs told me that anything you can do with jQuery, you can do with Angular.  Therefore, before learning Angular he was faced with the question of whether he would rather do something quick and familiar with jquery or spend some time investigating how to do it with Angular.

#### Documentation
Near the beginning of the conference, they announced that since the learning curve for Angular 1 had been so steep, they were rethinking how they wanted to present the documentation for [Angular 2](angular.io).  Therefore, Angular 2 plans on having several sets of docs.  At the moment, their Angular 2 website hints at having separate APIs for Dart and JavaScript.  I can't disagree with that division, I don't have much to do with Dart so I don't mind looking through docs that don't involve it.

A very recent experience I had leads me to believe that multiple sets of docs could continue to add to confusion for inexperienced programmers.  A few weeks ago I was helping some students set up a simple page to view information they had put in [Firebase](https://www.firebase.com/docs/), and much of the student's confusion came from paging through the wrong set of docs when looking for example code.  They had enough programming experience to get them through some of the basics, but they had gotten sidetracked by node.js setup instructions for Firebase which didn't make a lot of sense to them since they weren't working on server-side anything (although it made enough sense since it was javaScript to make them believe they were in the right place).  Now, most of the developers using the Angular documentation would be able to discern quickly if their quick google search for a method had dumped them into the wrong set of docs, but someone just starting up with programming could be disconcerted.

#### Prototyping with Angular
Some devs from the Google UX team gave one of the more interesting presentations of the day on prototyping ([video here](http://youtu.be/ufZpHuiyepg)).  Prototype websites for testing user interaction and design elements are a wonderful thing, but usually they do not incorporate real data nor do they have a lot of the bells and whistles that the production website will have.  They're a frame to get an idea of how the real website will work.  The Google team came up with some cool tools to use for prototyping that use Angular to make them more interactive.  Here are some of the highlights that I thought were cool:

- Design in the browser

  Rather than doing all the design work in a tool (Illustrator / Photoshop), quickly toggling colors and images in the browser can give you a cool idea of how the UI looks in a browser.
  
- Tracking user interaction

  Angular can keep track of which videos a user played, buttons that they clicked, and more.  If you want to get an idea of how users are navigating your demo site or prototype, these statistics can be very useful.
  
- Accessibility

  Why make a class called "checkbox" when you can describe that its ROLE is a checkbox?  [ngAria](https://docs.angularjs.org/api/ngAria) supports [Accessible Rich Internet Applications](http://www.w3.org/TR/wai-aria/) offering a host of descriptions and functionality for users with accessibility concerns.  For more on accessibility at the conference, see this talk: [Accessibility Design Made Easy](http://youtu.be/_2Pt6Xx94Bc)
  
- Using real data

  No more lorem ipsum, the Google team is using Google Sheets to pull in data and update values on the fly.  All you need to do is reload your prototype to get any information that was added to the sheet.

Of all of the points, I think the Google Sheets idea has the greatest potential for the CDRH.  We have discussed the idea of pulling information from a spreadsheet like a google doc, as it is a friendly interface for students, it has some basic versioning, and it can be worked on from anywhere and by multiple people.  Although it wouldn't be ideal to use data from a spreadsheet in a production environment, it could be useful while building the site.

#### Observables

A team from Netflix building a monitoring system gave a talk about using observables: [Reactive all the Things](https://www.youtube.com/watch?v=zbBVG8bOoXk&feature=youtu.be&t=2m48s).  They had built a tool that manipulating arrays constantly with things like .map(), .filter().  For those that are not familiar with how those work in JavaScript, they iterate through items in an array and then return a new array.  So you might filter an array of 100 items and get back a new array with 73 items that fit your criteria.  Unfortunately for the Netflix team, when they were working with massive data sets, everything crashed and burned.  Therefore, they switched to using streams which helps out your garbage collector.  As somebody who has been watching the development on streams in node.js from the sidelines but who has had very little reason to use them beyond posting requests, I found the talk gave me a pretty compelling reason to start using them in my every day coding.

#### Ravioli Code
Compared with the infamous spaghetti code, the speaker was advocating "ravioli" code, in which functionality is located in a single file.  Each file, the speaker elaborated, might have some cheese and broccoli, but in general it is clearly a wrapped up piece of pasta.  Later, your files will get smushed / minimized into a single giant file to be sent to a browser, but on the developer end things remain clear.

The talk was specific to the angular style guide, but there were a lot of things that the speaker touched on that resonated with me.  He asked whether it was better to put all controllers together, all views together, etc, or whether it was better to separate them by feature.  When I worked for a software company, although the files were clearly labelled, it could be annoying to hunt through several directories looking for all the code related to a feature like, say, a pdf generator.  It would have been much easier to refer to a directory called pdf_generator with all of those files contained inside.  Of course, that's easy to say without trying it.  Breaking things into features might end up being just as annoying in its own way, like not being able to quickly compare controllers or losing a sense of which files are used for helper methods...still, seems like the kind of thing I would be willing to risk.

The speaker stressed writing with "lift":
- Locating code quickly
- Identifying intention / purpose at a glance
- Flat file structure (when possible)
- DRY

Nothing about that is terribly novel.  Everybody should be trying to write code that's intuitive both for oneself and for the other hapless individuals who may come across it in the future.  Still, it's good to be reminded.  I think I am probably guilty of overcommenting my code in order to make it clear what is happening, which just muddles the files up with text.  Instead, if I have broken things into logical files and directories, it should help out whoever is about to open a file to look at the code.

#### Summary
Overall, there were a lot of fun things to think about from the conference.  I might hold off on dabbling more with Angular until Angular 2 is out and a bit established, because I'm not keen to learn Angular 1 if its going to be deprecated in a few months.  However, it looks so powerful that I am positive it will be useful in either prototype website designs or production functionality here at the CDRH.
