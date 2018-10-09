+++
company = "Pessoas.vc"
date = "2018-10-08T23:27:26-03:00"
description = ""
icon = "https://media.cdnandroid.com/f7/be/64/78/imagen-pessoas-vc-0thumb.jpg"
projectdate = "2013 - 2014"
title = "Real Time Chat Engine using Python and Tornado"

+++
Pessoas.vc was running at Facebook, and one of the main goals to run there was to have a local chat for the users, where they could chat real time, without the hassle of page reloads, or COMET requests.

At the time, Facebook had bought FriendFeed and released FriendFeed HTTP Server and Framework to the wild.

Using them a combination of WebSockets, Python, and Tornado, I was able to integrate the internal PHP backend with the Live Chat process. Python was them in charge of received a user connection request, authenticating with the PHP backend to validate the user, handles all users communication with online users, and sending the messages copy to the backend in order to save them.

Working in a async way, with a proven C100K framework helped a lot, keeping things running smoothly, and being able to handle all our traffic without the need of more than 2 servers running with 4 workers each.

This project also interacted with the notifications system that I will explain later.