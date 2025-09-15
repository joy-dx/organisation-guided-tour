---
menus: main
title: Analyse App Quality
weight: 2

---
In this guide, we will demonstrate the core features of app tracking and analysis using a simple [Hello World backend](https://github.com/joy-dx/go-hello-world).

JoyDX allows you to track changes to GIT repositories, automatically reporting changes and creating quality reports. Once an app is being tracked, JoyDX will periodically (configurable in settings) check for updates. See [the online page](https://joydx.com/docs/key-concepts/apps) for more information.

## Start Tracking an App

Start by navigating to the Apps screen by using the side navigation menu and click the "Add an App" button; you should be seeing the form depicted below.

![Start Tracking an App](/add-new-tracked-app.png)

Enter `https://github.com/joy-dx/go-hello-world` in the "Repository URL" field and optionally a reference of your choice; if you leave the app reference empty, JoyDX will attempt to create a human readable identifier for the app based on the repository address.

Once you click start tracking, JoyDX will clone the repository to your shared assets path as a repository root and start performing the first analysis for you.

## The App Screen

**NOTE** Depending on the quality of your internet connection, the first time you run the analysis service, it may take a while. This is because JoyDX needs to download some additional tooling. You can track the progress by clicking the "x Active Downloads" button in the bottom right corner of the window.

![App Analysis](/app-analysis.png)

1. **App Controls** Visit repository in a browser, manually synchronize with remote, and remove app tracking
2. **In-page Navigation** View analysis results, manage reusable  environment profiles, view contents of the README, and review history


## Analysis Results

When the app analysis service has finished, you will be presented first with information split in to the following sections:

* **High level analysis** gives you a summary of the application to reflect structure and quality. For more information on the metric, you can click on the information icon to open a browser 
* **Code Issues** contains the result of language specific checkers; in this case JoyDX detected a Go project.
* **Security** as the name suggests lists possible security issues such as packages with known CVEs or possible credential leaks within the app

That concludes the app analysis introduction. You can now move on to the [Manage your System Tools](/system-management) guide.