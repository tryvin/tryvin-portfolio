---
title: "SET: Answers to Technical Questions job interviewers likes to ask. - Part 1"
date: 2018-10-09T19:54:52-03:00
draft: false
icon: "http://letscontent.com/wp-content/uploads/technical-content-writing.png"
image: "http://biogenx.ca/wp-content/uploads/2014/10/Design.jpg"
---

**Question:** *Please detail a time an architectural decision and/or design pattern was implemented on a development project that added technical debt. Why was the decision made and what problems did it cause? Would you do anything differently if you were architecting the system from scratch now?*

**Answer:** Let's go throught item by item so it will be easier to understand

##### What architectural and/or design patterns have I worked on:

* ETL (Extract, transform, load)
    * Where? A lot of projects in my life have been all about scrapping content from one place, transforming it, and inserting into a central place, or even displaying it directly to the user.
    * **What kind of Design Patterns have you worked on with this architectural pattern?**
        * Data mining: Analysing huge amounts of data, and discovering patterns into this data for later usage into some bussiness decisions guidance software I have worked in the past.
        * Change data capture: I, and I would assume all of us developers, work with this kind of design pattern on a daily basis, when we use a Database Framework, when we do some hooks setup for triggering some actions based on a user behaviour like updating a row.
* MFT (Managed file transfer)
    * Where? Within HIPAA projects, and POS projects. When you give users permission to upload content to your software you must be able to track their file views, and control who can see what, and who can download what. Keeping files secure, and auditable.
* EAI (Enterprise Application Integration)
    * Where? All the bussiness projects I have worked on, most of the times, the clients needed their software to communicate or extract data from other software they were running, so I had to use some of ETL, imagination, and writting connectors in legacy code in order to interact with legacy software.
    * **What kind of Design Patterns have you worked on with this architectural pattern?**
        * Publish–subscribe pattern: Working with Mosquito, and some others MQTT broker software, integrating different kind of systems in a fashion way.
        * Request–response: API calls, File write and reading, Unix Sockets, all the kind of communication that are made possible with the current technology.
        * Messaging pattern: Cracking binary network protocols to discover how to communicate with the desired software.
* TDS/OLTP (Transaction data stores / Online transaction processing):
    * Where? Whenever I'm using mySQL I'm using a transaction data store. Over the course of the years I have found different ways of improving, and analysing the queries I sent to the data store in order to keep things running smoothly and bullet proof. Partitioning data is a big step when using large datasets, but this can't be the only step you need to take, this must be used together with other stores technics, like using a cache system to improve the timing when trying to retrieve information from a traditional transaction data store.
    * What can you do when not using a transaction data store?
        * Basically, we have what we call today the noSQL databases, most of them remove the transaction parts, and allow multiple updates at the same time to the same path, as their ideal is not data update safety, instead, they rely on performance, and simplicity of development. IMHO, you can't just go directly with noSQL without first thinking if your project will really behave better with this kind of approach.
* Business analytics, Transactional reporting:
    * Where? When working with analytics data in the projects, as the next step after launching a new live version, the process of development is paused, but we still need to study how the customers will interact with the software, that said, reading raw data, using of the ETL processes, and then using some in-house codes together with available software we have today like ElasticSearch, or even Facebook's Presto.
* Text analytics, NLP, Decision management, Deep learning:
    * Where? Salesforce bussiness analysis project, I had to use text analytics, with some natural language processing, so the software would be able to use decision management code in order to categorize the best gigs a company would have inside their leads, and bussiness contacts, and within their classification the code was using of the process of deep-learning to better categorize the next gigs into a way the company like.
* And many more architectural and design patterns we have today available, patterns that aren't into the big books, best practices of software development based on what kind of technologies we have available today, best practices for code indentation, for variable naming, and so on.

With all that said, I think I'm now able to answer the first question

###### Please detail a time an architectural decision and/or design pattern was implemented on a development project that added technical debt:

In my Dev life I have stepped into a lot of projects, but this last one would give you a idea of what bad decisions do. This project was a Uber-like app, two different versions one for Android, and one for iOS.

The whole idea behind the project was that someone creates a job posting picking a address from a map, fills some info, and post it to the system, then, a user sees this map, picks jobs from this map, and start proving their service, great idea, badly designed at the code level basis.

First: Two codebases, this would hurt the principle of maintable codebase, assuming that this simple app doesn't had a real need of using a native code, a simple React Native app would do the job.

Second: Bad written code, not well organized, with a lot of static calls here and there.

Third: No source control at the beggining of the project, the whole code was sent to a GIT repository all at once, preventing you from really searching throught the history of the project to understand some design decisions.

*Why was this decision made?*

The client wasn't a tech-savy client, he received some bad advice at the time from his developer, and started the project without getting more professional advices.

*What kind of issue two codebases gave in this project?*

The iOS code started first, more aligned with the original application bussiness plan, features were implemented there with feature-first mind, but then, after finishing the iOS code, Android had started. With the timeframe tight, the original developer made some mistakes when developing with Android, which of course, lead to small bugs here and there, and got live without proper testing.

*How would React Native help this project? (Answers: Would you do anything differently if you were architecting the system from scratch now?)*

Using a singular codebase at top of React Native could have things go way faster, the code would be better maintable, and you would only need to do one or two small changes here and there to make it work perfectly at the other platform. You could even reuse this same code to do a web version of the app, using React Native Web, or even, a Electron version of it.

*How would you suggest a refactor to the client?*

Showing him the technical needs of his app, and how the code was organized in both of the platforms, also, showing him what kind of features got lost at the transition from iOS to Android, and always, trying to translate the best I could from the tech-terms to a non-tech person.

**Question:** *What would you say was your best experience of version control workflows in a team? Which parts of it did you find particularly helpful? Were there any pain-points that you are still searching for ways to resolve?*

**Answer:** Again, let's go throught item by item so it will be easier to understand

*What would you say was your best experience of version control workflows in a team?*

I have started working with version control since the CVS era, going throught SVN, that said, my best experience with version control was my first experience with version control. We were a small team of web developers, and were getting too much issues from a "file.php", "file1.php", "file1.php.bak" design. We then had to find a way of improving this, the main issue: *Run a webserver update whenever we would send the file to the version control*, to solve that, I was responsible to setup a SVN server, with some post-receive hooks. These post-receive hooks would run a checkout at a temporary directory, run whatever script we had to run, update the links at the webserver to this new folder, and let everyone knows that this new version was live.

*Which parts of it did you find particularly helpful? (Continues the answer from the last paragraph)*

Why I say that my first experience with version control was my best experience with this kind of workflow? People tend to give too much of "hipe" over a version control system, but they forgot what is the real version control deal, version, control. And that's it, you have a lot of version control systems out there, you have CVS, SVN, GIT, HG, and so on, but they all do the same, you can tag (branch), you can archive, you can use a centrallized server, you can use a local storage, you can see logs of who did what, you can revert changes, checkout a old version of your code, rebase, force push, it's not a big deal, it's a usual way of working today, if you can't work in a version control workflow, I'm sorry to say, but you can't work with Dev.

*Were there any pain-points that you are still searching for ways to resolve?*

I wouldn't think my pain points, but, Yes, sadly version control for binary files ain't good a we think, of course, you can store the binary files there, in git you can use GIT-LFS, but you can't really diff files, some of the UX/UI designers I work on still use their old "file", "file1", "file2" way of working. Sometimes, trying to use a version control with Photoshop files can just make you worse than good.

**Question:** *When writing tests, how do you decide which things to test? Have you been in a situation where tests were causing more trouble than they were worth? What did this tell you about the tests, or the architecture of the overall application?*

**Answer:** Again, let's go throught item by item so it will be easier to understand

*When writing tests, how do you decide which things to test?*

I will try to keep it simple: Basically everything can be testable, but I always try to write tests for things that are bussiness critical, why? When you are working in a real agile development, you understand that code is first than documentation. If what you have done is a simple thing that won't impact the app if it breaks, you can proceed your development, and finish more tasks in order to get your sprint done. Later in the sprints you can get back to this old code, maybe do a little refactoring, and write some unit tests.

But please, do remember, we always have to write test steps to the QA team in order for helping them to test the Tickets we send to them.

*Have you been in a situation where tests were causing more trouble than they were worth?*

Yes, again, agile development, somethings are just hard to write unit tests, because they need some setups that are already done in the final enviroments that would need to setup a whole docker container just to run a small test, either because it's a "Redis connection testing", or because it just connects with a well tested backend to send a SMS.

*What did this tell you about the tests, or the architecture of the overall application?*

Go back to *When writing tests, how do you decide which things to test?*, and read again the *Have you been in a situation where tests were causing more trouble than they were worth?* item.

**Question:** *Have you had experience working with containers or VMs that allow a team to develop in an identical environment to production? If so, what kind of tools and workflows have you found to be the most helpful? Was there anything you still needed to be mindful of when working this way?*

**Answer:** Again, let's go throught item by item so it will be easier to understand

*Have you had experience working with containers or VMs that allow a team to develop in an identical environment to production?*

**Simple and straight answer:** Yes, I had.
**More extensive answer:** One of my jobs as DevOPS is to create Dockerfiles and docker-compose files to the other devs, as I'm also taking care of the system administration I know exactly what is running at the servers, and can write whatever container I need so the devs can test their codes locally. To be honest, I have been in the Linux world way before Docker was a thing, I have worked with all kinds of Virtual Machines, from VMware ESX to Xen ones.

*If so, what kind of tools and workflows have you found to be the most helpful?*

**Simple and straight answer:** docker-compose, Terraform, Vagrant, and the good and old chroot.
**More extensive answer:** docker-compose, Terraform, Vagrant, and the good and old chroot, all aligned with CI, and CD tools like Travis, CircleCI, Microsoft AppStore Deploys, among some other tools. It's DevOPS after all.

*Was there anything you still needed to be mindful of when working this way?*

**Simple and straight answer:** No.
**More extensive answer:** No, I would reuse the same version control explanation, this is a day-to-day tool, when you get used to it, you start working in a way that best fits the tool. I don't need to be thinking, I just write things that work in this way.
