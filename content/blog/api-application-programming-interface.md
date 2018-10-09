---
title: "A.P.I. - Application programming interface"
date: 2018-10-08T21:04:25-03:00
draft: false
icon: "https://cloudmonix.com/wp-content/uploads/2018/02/api.png"
image: "https://cdn-images-1.medium.com/max/1200/1*lAR9Uh_gJ7dp23e0vhy5Hg.png"
---

From WikiPedia ([https://en.wikipedia.org/wiki/Application_programming_interface](https://en.wikipedia.org/wiki/Application_programming_interface)):
> In [computer programming](https://en.wikipedia.org/wiki/Computer_programming "Computer programming"), an **application programming interface** (**API**) is a set of [routines](https://en.wikipedia.org/wiki/Subroutine "Subroutine"), protocols, and tools for building [software applications](https://en.wikipedia.org/wiki/Software_application "Software application"). An API expresses a [software component](https://en.wikipedia.org/wiki/Software_component "Software component") in terms of its operations, inputs, outputs, and underlying types, defining functionalities that are independent of their respective implementations, which allows definitions and implementations to vary without compromising the interface. A good API makes it easier to develop a program by providing all the building blocks, which are then put together by the programmer.

Also from WikiPedia ([https://en.wikipedia.org/wiki/Representational_state_transfer](https://en.wikipedia.org/wiki/Representational_state_transfer)):
> In [computing](https://en.wikipedia.org/wiki/Computing "Computing"), **representational state transfer** (**REST**) is the [software architectural style](https://en.wikipedia.org/wiki/Software_architecture_styles_and_patterns "Software architecture styles and patterns") of the [World Wide Web](https://en.wikipedia.org/wiki/World_Wide_Web "World Wide Web").<sup>[[1]](https://en.wikipedia.org/wiki/Representational_state_transfer#cite_note-Fielding-Taylor_2000-1)</sup><sup>[[2]](https://en.wikipedia.org/wiki/Representational_state_transfer#cite_note-Richardson_2007-2)</sup><sup>[[3]](https://en.wikipedia.org/wiki/Representational_state_transfer#cite_note-Richardson_2013-3)</sup> REST gives a coordinated set of constraints to the design of components in a distributed [hypermedia](https://en.wikipedia.org/wiki/Hypermedia "Hypermedia") system that can lead to a higher-performing and more maintainable [architecture](https://en.wikipedia.org/wiki/Software_architecture "Software architecture").
>
> To the extent that systems conform to the constraints of REST they can be called RESTful. RESTful systems typically, but not always, communicate over [Hypertext Transfer Protocol](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol "Hypertext Transfer Protocol") (HTTP) with the same [HTTP verbs](https://en.wikipedia.org/wiki/HTTP_verbs "HTTP verbs") (GET, POST, PUT, DELETE, etc.) which web browsers use to retrieve [web pages](https://en.wikipedia.org/wiki/Web_page "Web page") and to send data to remote servers.<sup>[[4]](https://en.wikipedia.org/wiki/Representational_state_transfer#cite_note-Fielding-Ch5-4)</sup> REST interfaces with external systems using [resources](https://en.wikipedia.org/wiki/Web_resource "Web resource")identified by [Uniform Resource Identifier](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier "Uniform Resource Identifier") (URI), for example `/people/tom`, which can be operated upon using standard verbs, such as `DELETE /people/tom`.

So, what does these terms has to do with me? Well, I’m a web developer, and in this busy world we live on, we constantly needs to connect with other systems, and make then parse data. Well, this was a trouble at the ancient time, we didn’t have a standard way of doing it, and we had to parse web pages, so we could fetch results, simulate user interaction so that we could insert content and so on.

When I’m working with PHP and our projects I tend to use a PHP class, slightly modified, that parses a list of classes using PHP [Reflection](http://php.net/Reflection) class, and it’s comments generates the mapping, example:

[https://gist.github.com/tryvin/5c1fc37096b575d63c2a](https://gist.github.com/tryvin/5c1fc37096b575d63c2a)

You see the pattern, where we map HTTP methods into a CRUD (Create, Read, Update, Delete) handler, so, everyone will know that to create a user they just need to POST into the url /users/new, to get a list of all users they connect with /users, and to delete some user, they use the DELETE HTTP method into the url /user/&lt;userId&gt;.

Why is this easier? Think that you only need to create four methods, that do some simple http requests, and you are all set to interact with this server. Instead of doing a request, then a scrap, then ordering the data, or simulating a user form, and submiting this data, then scrapping the response.

We have a new project at PayGate where hostels, and hotels would interact with these booking sites like Booking.com, HostelWorld, and so on. Sadly, booking.com doesn’t have some RESTful API =/, Bad bad booking.com, no donut for you =/
