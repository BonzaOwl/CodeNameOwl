---
title: Getting started with DBATools
date: 2019-03-21T16:00:06+01:00
author: BonzaOwl
layout: post
permalink: /getting-started-with-dba-tools
categories:
  - powershell
tags:
  - dba
  - powershell
---
I have never really got into PowerShell it is just something that I have never needed to use, however recently I have been reading more and more about the great things that can be done with DBATools so thought I would give the module a go and see what it could do.

### First thing is first

I needed to find out what version of PowerShell I am using so the correct method of installation for the module could be used. To do that I need to execute the following function;

<pre>  <code class="ps">$PSVersionTable.PSVersion</code></pre>

This returns the currently installed version of PowerShell

[<img class="alignnone size-full wp-image-234 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/PSVersion.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/PSVersion.png 857w, https://www.codenameowl.com/wp-content/uploads/2019/03/PSVersion-300x147.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/PSVersion-768x376.png 768w" sizes="(max-width: 857px) 100vw, 857px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/PSVersion.png)

As you can see my system has version 5 installed, so I can use one of two installation methods.

  * I can use PowerShellGet to download the module

<pre>  <code class="ps">Save-Module -Name dbatools -Path C:\Temp</code></pre>

  * I can invoke a web request to download the module

<pre>  <code class="ps">Invoke-WebRequest -Uri powershellgallery.com/api/v2/package/dbatools -OutFile C:\Temp\dbatools.zip</code></pre>

The web request method is a little bit slower but if PowerShell 5 isn&#8217;t available you will have to use it because PowerShellGet wasn&#8217;t introduced until version 5. That is it, there is nothing else to it the module is now available to use.

When installing the module, I was presented with the following, as the NuGet Provider is required, selecting yes is the only option to allow the installation to proceed

[<img class="alignnone size-full wp-image-238 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/PSNuGet.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/PSNuGet.png 1594w, https://www.codenameowl.com/wp-content/uploads/2019/03/PSNuGet-300x84.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/PSNuGet-768x215.png 768w, https://www.codenameowl.com/wp-content/uploads/2019/03/PSNuGet-1024x287.png 1024w" sizes="(max-width: 1594px) 100vw, 1594px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/PSNuGet.png)

&nbsp;

### Now what?

Now that I have the module installed there are so many functions that can be used, it is worth taking a look at the [Command Index](https://dbatools.io/commands/) or run this command to get a list of available commands right inside PowerShell

<pre>  <code class="ps">Find-dbacommand</code></pre>

[<img class="alignnone size-full wp-image-236 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand.png 856w, https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-300x255.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-768x653.png 768w" sizes="(max-width: 856px) 100vw, 856px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand.png)

As you can see, that returns a list of all the available commands that are usable within DBATools. But what if I want to find something more specific, let&#8217;s say I need to perform a backup but don&#8217;t know the command? Well, that is built into DBATools too, simply run this command.

<pre class="lang:tsql decode:true ">Find-DbaCommand -tag backup</code></pre>

[<img class="alignnone size-full wp-image-237 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-BackupTag.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-BackupTag.png 855w, https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-BackupTag-300x255.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-BackupTag-768x653.png 768w" sizes="(max-width: 855px) 100vw, 855px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/DBACommand-BackupTag.png)

As you can see that will return all the available backup related commands that can be performed in DBATools.

### Let&#8217;s Backup

Now that I know what commands I have available, let&#8217;s have a look at how to use one of them, I want to back up a database on my SQL Server but don&#8217;t want to have to load up SSMS, we can do that in DBATools.

<pre>  <code class="ps">Backup-dbadatabase -Sqlinstance localhost -Database StackOverflow2010 -BackupDirectory C:\Backups -BackupFileName Stackoverflow.bak</code></pre>

When we run this command, DBATools will back up our StackOverflow database to the directory we have specified with the filename we have specified.

[<img class="alignnone size-full wp-image-239 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase.png 856w, https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-300x255.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-768x653.png 768w" sizes="(max-width: 856px) 100vw, 856px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase.png)

&nbsp;

[<img class="alignnone size-full wp-image-240 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-Done.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-Done.png 856w, https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-Done-300x93.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-Done-768x238.png 768w" sizes="(max-width: 856px) 100vw, 856px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/BackupDatabase-Done.png)

So that is cool, but that is going to break my log chain! DBATools can handle that too just specify the CopyOnly parameter.

<pre>  <code class="ps">Backup-dbadatabase -Sqlinstance localhost -Database StackOverflow2010 -BackupDirectory C:\Backups -BackupFileName Stackoverflow.bak -CopyOnly</code></pre>

### Last Backup

So now we know how to backup databases from DBATools how can we find out when the database was last backed up? Sure we can.

<pre>  <code class="ps">Get-DbaLastBackup -SqlInstance localhost | out-gridview</code></pre>

[<img class="alignnone size-full wp-image-241 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupAll.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupAll.png 1179w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupAll-300x155.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupAll-768x396.png 768w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupAll-1024x528.png 1024w" sizes="(max-width: 1179px) 100vw, 1179px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupAll.png)

This is going to show us the last backup information for ALL databases on the instance, but what we want to just find out about one database, well just like the backup command, specify the database.

<pre>  <code class="ps">Get-DbaLastBackup -SqlInstance localhost -Database StackOverflow2010 | out-gridview</code></pre>

### [<img class="alignnone size-full wp-image-242 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupSO.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupSO.png 1183w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupSO-300x156.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupSO-768x401.png 768w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupSO-1024x534.png 1024w" sizes="(max-width: 1183px) 100vw, 1183px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupSO.png)

### Check it once, check it twice

So now I know how to backup my databases, I can find out when the last backup was taken what about checking the backup, well you guessed it, DBATools can help with that too.

<pre>  <code class="ps">Test-DBALastBackup -sqlinstance localhost | out-gridview</code></pre>

[<img class="alignnone size-full wp-image-243 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck.png 857w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck-300x256.png 300w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck-768x656.png 768w" sizes="(max-width: 857px) 100vw, 857px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck.png)

If I have a look in SSMS during the restore I will be able to see that the restore is actually taking place

[<img class="alignnone size-full wp-image-245 img-fluid " src="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck-SSMS.png" alt="" srcset="https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck-SSMS.png 415w, https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck-SSMS-300x200.png 300w" sizes="(max-width: 415px) 100vw, 415px" />](https://www.codenameowl.com/wp-content/uploads/2019/03/LastBackupCheck-SSMS.png)

&nbsp;

Just like the backup command, if I want to test a specific database I can specify that using the **-database** flag

<pre>  <code class="ps">Test-DBALastBackup -sqlinstance localhost -Database StackOverflow2010 | out-gridview</code></pre>

### Tip Of The Iceberg

This is just the tip of the iceberg, there is so much more that can be done with DBATools, not just Backups, it is worth checking out the [DBATools](https://www.dbatools.io) website which has a wealth of information on what the module can do and how you can use it.

<https://docs.dbatools.io/>

This is a great repository of commands with a detailed explanation of each and how they work, so if you wanted to find out how Test-DBALastBackup actually works you could look it up [here](https://docs.dbatools.io/#Test-DbaLastBackup).

### Let&#8217;s Upgrade

DBATools is constantly being developed so it is worth knowing how to go about keeping it updated. As DBATools was downloaded from the PowerShell Gallery the following command can be used to perform an update of the module, when running this command it is worth noting that the PowerShell command line has to be run as administrator.

<pre>  <code class="ps">Update-Module dbatools</code></pre>

### More Help

DBATools has a great community over on the [SQL Community slack](https://dbatools.io/slack/) it is a great place to get more help and advice when using the module, the developers are active there and are always on hand to help.