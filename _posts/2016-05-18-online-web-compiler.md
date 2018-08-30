---
title: "Building an app to deploy sandboxed compilers (in 3 days!)"
date: 2016-05-18
permalink: /posts/2016/05/online-web-compiler/
tags:
  - compiler
  - deployment
---

Sometimes researchers need tools to show to the world (and their peers)
their on-going research. Instead of relying on reviewers (of papers) to install
different compilers with multiple and possibly clashing dependencies,
there is a tendency to deploy these languages in sandboxes in the cloud.
I love the idea!

Following this tendency, I put 3 days of work to created a simple web
application that allows
our research group to manage multiple compilers deployed on the cloud
via a single admin panel. Every compiler runs in its on Linux container
(for security reasons), can have dedicated examples and its own description.
I intend on publishing the code as soon as I fix some issues.
(Building the compiler is done manually, at the moment!)
For now, I can show an image of one of the online compilers.
The web app has been written in Python, using the Django Framework
and a simple sqlite database.

![Online Compiler](/public/images/online-kompiler.png)

I am a bit lazy and I don't like to repeat myself, so I created a
deployment script (`fabfile`) that allows us to spawn new
servers (AWS), provision the server, deploy the application,
perform updates, manage the database and execute remote commands in
the shell. (Yay!)

The code will be available soon!

Repo: ...
