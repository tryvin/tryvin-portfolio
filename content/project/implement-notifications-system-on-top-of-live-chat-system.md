+++
company = "Pessoas.vc"
date = "2018-10-08T23:31:55-03:00"
description = ""
icon = "https://media.cdnandroid.com/f7/be/64/78/imagen-pessoas-vc-0thumb.jpg"
projectdate = "2013 - 2014"
title = "Implement Notifications System on top of live chat system"

+++
After the live chat project was done, I had another challenge, add a layer to the notifications alerts.

Using the PHP backend as the entry point, Python was able to retrieve users notifications, and send them to the connected clients.

This gave us the ability to notify users about their own notifications, and the ability to give users a general warning in less then 10 seconds.

Users received the notification in milli-seconds as long as they were connected with the WebSocket systems.