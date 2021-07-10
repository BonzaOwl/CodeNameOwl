---
title: Installing Visual Studio SQL Intergration Services
date: 2021-08-09T09:00:00+01:00
author: Rich
layout: post
permalink: /installing-visual-studio-sql-server-intergration-services
categories:
  - sqlserver
tags:
  - SSIS
  - SQL
  - VisualStudio
---

In this post, I am going to show you how to install SQL Server Intergration services for Visual Studio 2019, SSDT or SQL Server Data Tools no longer exists for Visual Studio 2019 so installation is a little bit different for newer versions of Visual Studio. 

First we are going to need to make sure we have Data Storage & Processing installed, Open up Visual Studio and select Create New Blank Project, from the bottom of the template window select Install more tools and features as shown below; 

![](/assets/img/vs-more-tools.png){: .img-fluid}

One that Window has opened, you will need to scroll down until you come to Other Toolsets, from this category select Data Storage and Processing.

![](/assets/img/vs-data-storage-processing.png){: .img-fluid}

Tick the box and then select Modify from the lower right corner of the window. **You will need to make sure Visual Studio is fully closed**. 

One the installation has completed, you will need to load up Visual Studio, from the top menu select **Extensions**.

![](/assets/img/vs-extensions1.png){: .img-fluid}

Then select **Manage Extensions**

![](/assets/img/vs-extensions2.png){: .img-fluid}

A new window will open within this window is a search box to the upper right corner, enter **SQL Server Intergration Services Projects** and press enter, the SQL Server Intergration Services Projects extension should appear, click **Download**.

![](/assets/img/vs-extensions3.png){: .img-fluid}

Your web browser of choice will then open and a download will begin, save this in a location of your choosing, I selected my downloads folder.

![](/assets/img/vs-extensions4.png){: .img-fluid}

Once the download has finished, you going to need to locate the location which you selected to save the extension, once you have it double click the exe which in my case was **Microsoft.DataTools.IntegrationServices**

![](/assets/img/vs-extensions5.png){: .img-fluid}

Next you will see a series of wizard windows, stepping you through the installation process.

![](/assets/img/vs-extension-ssis-install-1.png){: .img-fluid}

![](/assets/img/vs-extension-ssis-install-2.png){: .img-fluid}

![](/assets/img/vs-extension-ssis-install-3.png){: .img-fluid}

![](/assets/img/vs-extension-ssis-install-4.png){: .img-fluid}

![](/assets/img/vs-extension-ssis-install-5.png){: .img-fluid}

Once the installation has completed, you can go ahead and load up Visual Studio, again from the window that appears, select Create new blank project. Clear anything that might be in the search box and enter **intergration** this should then bring up the option of **Intergration Services Project** which is what we want, click that and select Next. 

![](/assets/img/vs-extension-ssis-new-proj.png){: .img-fluid}

You should now be able to start creating your SQL Server SSIS package from within Visual Studio 2019.

![](/assets/img/vs-extension-ssis-new-proj-2.png)