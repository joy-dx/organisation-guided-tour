---
menus: main
title: Collaborate with Organisations
weight: 4
---
In this guide, we will setup a new organisation tailored to your development needs so that by simply sharing a link with a colleague for them to be able to provision their system and launch services according to your instruction.

**NOTE** To follow this guide, it is a prerequisite that you have configured JoyDX to support a Github account with both API access and permissions to write to remote repositories. It is possible to manually create organisations without these permissions but, that requires understanding JoyDX specifications; see the [online documentation](https://joydx.com/docs/reference/organisation) for more information. There is also a more [detailed guide available online](https://joydx.com/docs/guides/create-an-organisation).    

## The Organisation Management Screen

Start by navigating to the Organisation screen by using the side navigation menu. This guided tour is a JoyDX organisation so, your organisation screen should already look similar to the following

![Organisation Management Screen](/organisation-management.png)

1. **High Level Controls** - Status of repository and local change monitor. You can also remove the organisation from your device.
2. **Organisation Selection** - Change the primary organisation context determining what environments, roles, and wiki content are used during operation. There is also a button which will launch the wiki.
3. **Artefact Selection** - Manage and utilise various artefacts defined within the organisation.
4. **Contextual Navigation** - Shortcut buttons for organisation actions

We are going to be defining a brand new organisation so, go ahead and click the "Create a new organisation button"

## The Organisation Creation Wizard

![Organisation Creation Base Definition](/organisation-create-new-base.png)

JoyDX needs either write access to an empty repository or the rights to create a new repository. Put in the repository address where you would like to host the organisation and click the "Check Availability" button. JoyDX will then check whether the repository exists and is empty or prompt you to create the repository. When a valid repository is defined, you will see a tick 

If you see a 404 error message when trying to create the repository, it likely means your Github account doesn't have high enough level permissions. This can be resolved by going to the [Github Application Settings Page](https://github.com/settings/installations) and configuring the JoyDX application accordingly. If your problem persists, please join the Discord channel where we can help resolve the issue (and in turn update the support material)

When you fill in the rest of the details and click the create organisation button, the foundation of the organisation is created and pushed to remote host automatically as a private repository.

At this point, you have created an organisation people could join but, an empty organisation isn't very useful so, JoyDX encourages you to define a first role and environment.

## Your First Role

For a more detailed information on defining roles, see the [online guide](https://joydx.com/docs/guides/define-a-role)

![Organisation Creation Role Definition](/organisation-create-role-definition.png)

Roles are light versions of environments that focus on tooling. As you can see from the screenshot above, when it comes to adding tools to a role, you can click the "Add Tool" button to spawn a tool selector dropdown. Once the tool has been selected, JoyDX will offer you the choice of defining what version is to be used.

* If you leave both the release and version constraint field empty, JoyDX will use the "latest" version
* If you define both release and version constraint, the version constraint field will take priority

## Your First Environment

Defining environments within JoyDX is made simple thanks to the intuitive builder. The process is split up in to expandable sections to keep the interface clean. For a more detailed information on creating an environment, see the [online guide](https://joydx.com/docs/guides/create-an-environment)

For demonstration purposes, in this guide we will briefly describe the full process of defining an environment but, only configure a [simple hello world backend API](https://github.com/joy-dx/go-hello-world). You are encouraged to create an environment relevant to your development needs instead.

![Organisation Creation Environment Definition](/organisation-create-environment-definition.png)

1. **General Information** - Define high level information about the environment, choose plugins to speed up configuration, and set some global variables that are customisable prior to launch
2. **Tools** - Similar to the tool selection procedure used within the role definition, you should define all tools that the environment depends on
3. **Containers** - Define support services such as Databases to be run within a container engine. You could run a Database as an actual application within your environment but, due to the complexity of setup and managing state you are encouraged to use containers for these services so that when environments spin up, it is simple to guarantee a clean state and similarly remove state at shutdown.
4. **Apps** - The main focus of your environment, apps are software projects where you have access to the source code and want to develop / test.

### General Information

Aside from the self-explanatory name and description, within the general section, there are two things of note

![Organisation Creation Environment Definition](/organisation-create-variables.png)

Variables defined with the general section are for use within the Containers and Apps section providing customisable options at runtime available through `{{ .SVar 'VAR_NAME' }}` interpolation; the value you provide is simply a default value to be used.

![Organisation Creation Environment Definition](/organisation-create-plugins.png)

Plugins provide a simple way to integrate predefined configuration data in to your environment. In the example above, the Postgres plugin provides some variables and its' container definition.

### Tools

![Organisation Creation Environment Tools](/organisation-create-tools.png)

The tools section should be familiar to you after the role definition. As mentioned previously, you should try and be exhaustive with the list of tools your environment requires to maximise environment portability.

If you are making use of the hello world app, include `Air` (a live-reloading utility for Go applications) and Go (a statically typed and compiled programming language); the versions can be left empty so that JoyDX will use the latest available version

### Apps

For more information on app definition and lifecycle, see the [apps - online documentation](https://joydx.com/docs/key-concepts/apps) 

![Organisation Creation Environment Reuse apps](/organisation-create-reuse-app.png)

Previously used apps can have their configurations reused to save time on definition. For simplicity in this guide, choose the Tudu Go Gin Backend that was part of the environment from the Launch Dev Environments guide.

* Rename the app to `Hello World`
* Change the repository URL to `https://github.com/joy-dx/go-hello-world`. This is important because when we leave the Sourcing instructions empty, JoyDX will automatically treat a GIT checkout as the sourcing instructions 

Next we are going to adjust the lifecycle actions for our simple hello world program. By default, the lifecycle section will be collapsed so, click anywhere within the title area to expand. Remove the "run migrations" and "setup test data" from the dev section by clicking the red rubbish bin icon and confirming. You should now have two actions in total looking similar to the screenshot below.

![Organisation Creation Environment Lifecycle summary](/organisation-create-lifecycle-summary.png)

1. **Source** - Action definitions to make source code available to JoyDX
2. **Build** - Action definitions to get program in a state ready for operation
3. **Dev** - Action definitions for running the program in development mode
4. **Staging** - Action definitions for running the program in a production ready situation useful for testing and QA
5. **Health** - Operations to run intermittently to check the application is in a working state
6. **Action Selection** - Choose from a list of available actions to perform
7. **Action Configuration** - Creates a dialog box with options for configuring the action. The dialog box will present different options depending on the action type chosen

For our demo application, we want to configure the actions for both the build and dev stages

![Organisation Creation action configuration](/organisation-create-action-configure.png)

For the build action:

* From the Command field, change `tudu-backend` to `hello-world`. This is artefact name output from Go builds. Notice the special `.SVar` (String Variable) template syntax making use of `.env.bin` (environment binaries) path.
* From the working directory, change `.apps.tudu-go-gin-backend.root` to `.apps.hello-world.root`. This is another automatically defined variable for use within environment playbooks. In this case, it refers to the app path (using the app reference) within the environment. App references are automatically calculated based on the name; you can check what the reference is in the description under the Name field

For the dev action:

* From the working directory, change `.apps.tudu-go-gin-backend.root` to `.apps.hello-world.root` just like in the build action. When you create new "Execute Program" actions for yourself, the working directory will automatically set itself to the equivalent

When you have completed the above, click the "Save Environment" button to proceed

## Testing your work

If you have followed the guide up to this point, you should find yourself back on the main organisation management screen with your newly defined environment and role selectable from the sidebar. For selecting the environment you created, you will be presented with a summary and a launch plan.

![Hello World environment summary](/organisation-environment-hello-world-summary.png)

After clicking the launch button, you will be taken to the environment dashboard. Once everything is reported as running, you can click on the dev hello-world node and will be presented with the output similar to running air from the command line as shown below

![Hello World app output](/organisation-environment-hello-world-output.png)

If you can visit [http://localhost:8080](http://localhost:8080) from your browser and see a payload containing the message "hello joydx" you have successfully created and launched your first working JoyDX development environment, great! Shutdown the environment and head back to the organisation page for the last part of this tour.

## Making your changes stick

From your organisation page, you should notice a new button in the shortcut area and also a button along the top of the screen informing you "Repository changes to review", click either one of these buttons to enter to organisation GIT management screen.

![Review Organisation Changes summary](/organisation-review-changes.png)

1. **Current Repository Status** - Informs you of current GIT status and intended procedure for handling changes
2. **Commit Information** - Commit message area to provide summary of changes and checkbox to determine whether JoyDX should automatically open a pull request on your behalf
3. **File Changes** - Provide a detailed breakdown of changes made that will be included in the commit. 

Fill in the branch name and commit message, the latter using a visual markdown editor for convenience and hit submit. At this point, if you have "Auto create PR" checked, you will be provided with a web link to go and manage / merge the pull request.

## Sharing your Organisation

With your organisation setup and your first environment defined, you only need to share the repository address (for example, [https://github.com/joy-dx/organisation-guided-tour](https://github.com/joy-dx/organisation-guided-tour) is the organisation for this tour) to someone who can use it as a join address from the organisation screen and you now have simple collaboration!

Please note that, by default, the organisation repository created through JoyDX is created as a private repository. Other users will either need to have permissions to read the repository or you should make it public.

That concludes the guided tour, thank you for your time! We truly hope JoyDX becomes a core and beneficial tool for your development life. If you feel otherwise, we'd love to hear from you and try to make amends.

If you are finished with the Guided tour organisation, you can remove all traces from your device by using the leave button located in the top right corner of the organisation screen.