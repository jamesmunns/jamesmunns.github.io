---
layout: post
title:  "Learning Django and Docker... At the same time - Part 1"
date:   2015-10-07 02:55:00
categories: django postgres docker
---
In order to explore django, I wanted to look at what was necessary to get a basic Django installation up and going. Based on that, I found a digital ocean post for setting up Django with Postgres, NGINX, and Gunicorn on Ubuntu.

Perfect! I thought. Why not use the chance to learn a little about Docker at the same time? This is pretty much the basic use-case.

Well, after a bit of learning, and a bit of fighting with a Docker Script I wrote (I was using RUN and not CMD, oops), I managed to get it up and going.

Achieved so far:
* Installed all components in a Docker Container
** Ubuntu 14.04
** Virtualenv, Python3.x, pip
** Django
** Postgresql
** Gunicorn
** NGINX
* Checked that some of the next steps work

Still to be done:
* Configure Postgres with initial config
** Initial install
** Users? DB contents? It says 'postgres' user already exists?
** Best Database security practices? Maybe go read OWASP?
* Configure Django with initial config
* Customization, maybe go through with a practice "production push"
* Figure out how to automate the non-installation parts, such as database setup, configuration, etc. May be part docker, part python script
* Figure out how to pre-load sensitive data into a docker image, so that a dockerfile can be source-controlled, but things like SSH keys aren't exposed
* Figure out how to deactivate a virtualenv inside of a dockerfile

Issues I ran into:
* Getting the initial Docker setup to work
** Ran into issues possibly related to an old version of VirtualBox, or my recent upgrade to OSX El Capitan
** Solution: Use Kitematic to initialize the base docker-vm
* Learning dockerfile syntax, especially CMD vs RUN.
** Solution: Use RUN, not CMD except for a single run-time item
* Getting the docker terminal to "work". 
** (temp) Solution: Launch terminal from Kitematic
* Activating a VirtualEnv in Python in a Dockerfile
** Delete /bin/sh in the dockerfile, and map /bin/bash to /bin/sh
* Getting Postgres installed/setup
** Ran into path issues, as well as possible old instructions
** Add the Ubuntu Postgres installed binary path to bash path

I'm sure there will be more soon, but its nearly 3am, and I have work in the morning.
