---
title: Install Jekyll On Windows Using Linux Subsystem
date: 2020-04-19T08:00:00+00:00
author: BonzaOwl
layout: post
permalink: /jekyll-windows-linux-subsystem
categories:
  - personal
tags:
  - windows
  - linux
---

I recently moved to a new development workstation at home, still using Windows 10 but it was a fresh install. All of the previously installed dependencies were gone, including Ruby & Jekyll for which this site is built. 

I tried installing Ruby from the official binaries but kept running into dependency errors when trying to serve the site locally, I couldn't figure it out, so I decided to see if I could get it working using the Linux Subsystem for Windows, TL;DR it worked perfectly, but wanted to share how I went about setting it up.

First you're going to need to enable Microsoft Windows Subsystem Linux, you can do this with one command from Powershell

<pre>
    <code class="powershell">
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
    </code>
</pre>

Your computer will reboot and once it has started again, you are going to need to head to the Microsoft Store and install a Linux distribution of your choice 

![Linux in the Microsoft store](/assets/img/microsoft-store-linux.png)

I went with Ubuntu! 

Once that has installed you can load up the command prompt (as admin) and punch in a few commands to ensure the environment is ready to go

<pre>
    <code class="powershell">
bash
    </code>
</pre>

Update all of the software already installed and ensure ubuntu is running the latest version

<pre>
    <code class="powershell">
sudo apt-get update -y && sudo apt-get upgrade -y
    </code>
</pre>

Install the latest full version of Ruby

<pre>
    <code class="powershell">
sudo apt-get install -y build-essential ruby-full
    </code>
</pre>

Ensure that all of the gems for the system are up to date

<pre>
    <code class="powershell">
sudo gem update --system
    </code>
</pre>

Once all of the above is done we can then go ahead and install Jekyll

<pre>
    <code class="powershell">
sudo gem install jekyll bundler
    </code>
</pre>

You can check to see if Jekyll is installed by running 

<pre>
    <code class="powershell">
jekyll -v 
    </code>
</pre>

From the bash session you have open in the command prompt, next I need to get to the files that were stored on my local computer for which I use to build the site, to do that you can use the following command 

<pre>
    <code class="powershell">
cd "/mnt/v/development/Web Developments/CodeNameOwl"
    </code>
</pre>

This is going to change the directory to V:\development\Web Developments\CodeNameOwl, I then tried to serve the site and ran into an issue where some dependencies were missing, running;

<pre>
    <code class="powershell">
bundle update
    </code>
</pre>


will install only the dependencies that are referenced in the GemFile also as I have my files on the local file system when you come to serve the site locally you have to run that command as sudo like so;

<pre>
    <code class="powershell">
sudo jekyll serve
    </code>
</pre>

If you don't do this, you will be met with issues relating to permissions, if you are still running into issues after running that serve command 