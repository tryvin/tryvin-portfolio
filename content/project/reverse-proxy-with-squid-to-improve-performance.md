+++
company = "StayTrack"
date = "2018-10-08T22:52:31-03:00"
description = ""
projectdate = "2008 - 2008"
title = "Reverse Proxy with Squid to improve performance"

+++
The company had a big issue, their static pages were being served by the internal IIS server.

At the time, IIS wasn't really improved as what we have today. My job was to discover how to reduce the company site loading time, in order to improve the user experience.

After some hours of debugging I found that the main culprit were pages that could simply be cached and served by a reverse proxy.

In addition I found out that the PHP scripts were taking too long to load when trying to use the IIS handler.

Then using a combination of Squid + Apache I was able to do a set of rules that were used to route the requests to the right servers, keeping static pages, and PHP pages being sent to the apache server, and the proprietary tracking system calls, which used a DLL directly to the farm of IIS servers.

The Squid helped Apache doing caches of most of the static pages.

With this project, we decreased the load of the site pages from 30 seconds to merely 2 seconds, a improve rate of 1500%!