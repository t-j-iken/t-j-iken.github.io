---
layout: post
title: "School Project: Web Chat Client"
categories: misc
---

For a final group project in "CS352: Internet Technology", we were asked to create a simple web chat client using sockets and a client assigned cookie to remember a user being
logged in. The program uses a combination of self given python files to define some test input and self-produced Java files.

To implement this, we created two data structures: An ArrayList that contained our chat, and a map that mapped the user with a session cookie.

`ArrayList<String> chatLog = new ArrayList<String>();`

`Map<String, String> cookieMap = new HashMap<String, String>();`

When a user successfully logs in and sends a chat message, the ArrayList would be printed onto the screen, and kept track of the session using our map. Code and project is available on Github.

 


