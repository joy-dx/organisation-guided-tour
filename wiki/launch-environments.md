---
menus: main
title: Launch Dev Environments
weight: 1

---
In this guide, we will demonstrate the core features for managing environments using a [typical React app](https://github.com/joy-dx/tudu-ts-react-frontend) and a [Go based backend](https://github.com/joy-dx/tudu-go-gin-backend) to orchestrate an online managed Todo list.

The environment manager allows you to spin up complex environments in seconds with a single launch. It takes a simple spec, creates a detailed action plan, and executes it efficiently, including dependencies, no preparation required. For a detailed breakdown of environments, see [the online page](https://joydx.com/docs/key-concepts/environments) for more information.

For defining your own environments, you can follow the instructions within the "Your First Environment" section of the [Collaborate with Organisations guide](/collaborate-with-organisations) either as part of an organisation you are creating or for personal use from the Environments screen 

## Launching an Environment

If you have started the tour from the onboarding experience, immediately below the Start tour button you clicked is a drop down menu allowing you to select premade environments.

Opening the select menu, you should see a couple of listings entitled Tudu Stack, select the SQLite version. There is also a PostgreSQL version of the same stack but, if you didn't setup a container engine, this option will be disabled.

![Spin up a Stack](/landing-spin-up-an-app-stack.png)

After selecting the stack, JoyDX calculates an action plan which allows you to review what operations will take place. For an environment you haven't launched before, for both safety and orientation, it is recommended to check the action plan prior to launch. Once ready, click launch and you'll immediately be sent to the environment workspace screen. 

## The Environment Dashboard

The Environment Dashboard provides a high level overview of current operations and service status with the ability to control or drill down in to details with a single click. The screenshot below represents what you should see running the Tudu Stack for the first time

![the environment dashboard](/environment-dashboard.png)

1. **Presentation and operator controls** - Controls presentation and the dictates desired state for the environment. Zoom in, Zoom Out, Fit to area, control context, exit environment.
2. **Environment Status** - Provides an easy to view situation report of the environment. Clicking on any job node will show a popup with details of the job and any associated logs
3. **Status Toolbar** - For any active downloads / jobs, provides summary of activity with the ability to click through an pull up a detailed menu. Also provides a way to view activity message log 

## Using the Environment

NOTE - In an upcoming version of JoyDX, the environment dashboard will be enhanced allowing you to interact with services (or open a browser) and monitor GIT changes directly from the app.

At this point, if your system is in a similar situation to the depicted environment, you should be able to open your browser and visit [http://localhost:5173](http://localhost:5173) and log in to the app using a username password combination of `tester / development`.

With the environment successfully started in developer mode, let's make some live changes! Within your workspaces path (set up during onboarding, defaulting to `$HOME/joydx-workspaces`) you should see `tudu-stack-sqlite` and within this path an `apps` folder.

Open up `tudu-ts-react-frontend/src/index.css`, scroll down to the bottom of the file (line 141) and make the following change.

```
/* Original contents */
body {
    @apply bg-background text-foreground;
}
/* Remove bg-background and replace with bg-amber-600 */
body {
    @apply bg-amber-600 text-foreground;
}
```

As soon as you save the file, just like you were running the app using `pnpm dev` from the terminal, you should notice the entire app background has changed to reflect your update. That wasn't the most useful change but, has hopefully demonstrated how little effort it took to transform your device in to a developer machine!

That concludes the launching environments guide. Click the "Shutdown and Unload" button (which will send you back to the landing page) and move on to the [Analyse App Quality](/app-analysis) guide.