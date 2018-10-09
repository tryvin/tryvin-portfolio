+++
company = "Hiper Social"
date = "2018-10-08T23:14:37-03:00"
description = ""
icon = "https://pbs.twimg.com/profile_images/1083773832/thumb_400x400.png"
projectdate = "2009 - 2009"
title = "Creating a In-House CDN for Images"

+++
We had a huge issue, the images were being stored in a single server, and that said, we had to migrate this to a distributed servers architecture.

At the time, I had researched some of the best CDNs available, but they all lacked one thing: "low prices". Working on a budget means being creative, and some times, you need to do it right, and do it first.

After presenting the options we had to the members board, we decided to go with a different approach: "Let's copy some of these guys and do our own CDN".

That said, I worked around the clock with the team to create our own CDN, my test farm? A Xeon server setup with VMware ESX, and 4 virtual machines. At that time, we didn't have docker to help us, Linux was starting with their LXC containers, and chroot wasn't a viable option.

At the end of two weeks I had a MVP version, this was using a central database to control where the files were, helping us to add new servers easily. In order to do a upload, you had to request a token from the central server, and this server would send to you a token, and a upload URL at the chosen server. Distributing the load between 3 servers helped us to handle the million of users traffic we had every day. Using nginx to serve the static files over Apache was the best choice we could have done.

Lesson from this project? Sometimes, using a pre-made solution isn't the right choice.