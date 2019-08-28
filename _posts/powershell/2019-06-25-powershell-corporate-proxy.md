---
title: 'PowerShell &#038; Corporate Proxy'
date: 2019-06-25T17:47:58+01:00
author: BonzaOwl
layout: post
permalink: /powershell-corporate-proxy
categories:
  - powershell
tags:
  - gallery
  - powershell
  - proxy
---
I have been having a problem at work where when I try to either install or update a module on my work laptop I get the following error message.

[<img class="alignnone size-full wp-image-500 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy.jpg" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy.jpg 886w, https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy-300x81.jpg 300w, https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy-768x208.jpg 768w" sizes="(max-width: 886px) 100vw, 886px" />](https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy.jpg)

A quick Google of the error will return a plethora of information on [how to fix](https://stackoverflow.com/questions/14263359/access-web-using-powershell-and-proxy) the issue, with the main focus being on the following two lines;

<pre>  <code class="ps">$webclient=New-Object System.Net.WebClient
$webclient.Proxy.Credentials = [System.Net.CredentialCache]::DefaultNetworkCredentials</code></pre>

For the majority of people, this seemed to resolve the issue and they could go about there business, for me however it didn&#8217;t resolve the problem, at least it wasn&#8217;t the sole fix.

[<img class="alignnone size-full wp-image-501 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy2.jpg" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy2.jpg 888w, https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy2-300x220.jpg 300w, https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy2-768x562.jpg 768w" sizes="(max-width: 888px) 100vw, 888px" />](https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy2.jpg)

#### Offline Installer

I had a little bit of time this morning so I thought I would have a go at Installing dbatools using the offline method, I loaded up PowerShell and typed the command

<pre class="lang:ps decode:true ">Invoke-WebRequest -Uri powershellgallery.com/api/v2/package/dbatools -OutFile c:\temp\dbatools.zip</code></pre>

However, I was presented with the following.

[<img class="alignnone size-full wp-image-502 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy3.jpg" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy3.jpg 885w, https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy3-300x218.jpg 300w, https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy3-768x558.jpg 768w" sizes="(max-width: 885px) 100vw, 885px" />](https://www.codenameowl.com/wp-content/uploads/2019/06/PowershellProxy3.jpg)

What actually appeared to be happening was [powershellgallery.com](https://www.powershellgallery.com/) had been blocked by an upstream web proxy policy, I requested that [powershellgallery.com](https://www.powershellgallery.com/)/* be white listed for the admin team, waited a little while and tried again.

[<img class="alignnone size-full wp-image-503 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/06/4.jpg" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/06/4.jpg 877w, https://www.codenameowl.com/wp-content/uploads/2019/06/4-300x45.jpg 300w, https://www.codenameowl.com/wp-content/uploads/2019/06/4-768x115.jpg 768w" sizes="(max-width: 877px) 100vw, 877px" />](https://www.codenameowl.com/wp-content/uploads/2019/06/4.jpg)

Wallah, it works now. I still need the two magic lines of code, which are in my PowerShell profile now.

Hopefully this helps someone else.