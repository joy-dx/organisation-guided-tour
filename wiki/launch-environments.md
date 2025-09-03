---
menus: main
title: Launch Dev Environments
weight: 1

---
In this guide, we will demonstrate the core features for managing environments using a [typical React app](https://github.com/joy-dx/tudu-ts-react-frontend) and a [Go based backend](https://github.com/joy-dx/tudu-go-gin-backend) to orchestrate an online managed Todo list.

The environment manager allows you to spin up complex environments in seconds with a single launch. It takes a simple spec, creates a detailed action plan, and executes it efficiently, including dependencies, no preparation required. For a detailed breakdown of environments, see [the online page](https://joydx.com/docs/key-concepts/environments) for more information.


## Launching an Environment

If you have started the tour from the onboarding experience, immediately below the Start tour button you clicked is a drop down menu allowing you to select premade environments.

Opening the select menu, you should see a couple of listings entitled Tudu Stack, select the SQLite version. There is also a PostgreSQL version of the same stack but, if you didn't setup a container engine, this option will be disabled.

![Spin up a Stack](/landing-spin-up-an-app-stack.png)

After selecting the stack, JoyDX calculates an action plan which allows you to review what operations will take place. For an environment you haven't launched before, for both safety and orientation, it is recommended to check the action plan prior to launch. Once ready, click launch and you'll immediately be sent to the environment workspace screen. 

## The Environment Manager
