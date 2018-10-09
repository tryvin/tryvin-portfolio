+++
company = "Hiper Social"
date = "2018-10-08T23:22:29-03:00"
description = ""
icon = "https://pbs.twimg.com/profile_images/1083773832/thumb_400x400.png"
projectdate = "2010 - 2010"
title = "Create a In-House parser for OpenSocial canvas XML"

+++
After we launched at Orkut, we had to expand, and the next social network at our list was MySpace.

We then had to do some small changes here and there to accommodate the users and their own stack.

First thing was to integrate the OpenSocial login we had from Orkut to MySpace, even thought they had joined forces to create the OpenSocial consortium, the thing wasn't really working the same way to all of them.

Using nothing more than a poor written documentation, patience, and a network inspector, I was able to make the social logins working at MySpace.

The time came, and we were running there, the next challenge was to make the Users profile available at their own homepage, Orkut had this "OpenSocial XML Format for Canvas", and we had this working nicely at Orkut, using some custom PHP code to generate the user personalized XML, the only thing we had to do to MySpace was writing a reader for this XML in order to display at their side.

The project was a success, all working flawless, using nothing but old PHP with SimpleXML.