---
menus: main
title: Manage your system tools
weight: 3
---
In this guide, we will setup some development tooling to be made available system wide. Should you not want JoyDX to manage tooling for you, skip this guide and proceed to the [Collaborate with Organisations](/collaborate-with-organisations) guide.

JoyDX allows you to setup a special environment profile for your system for the purpose of managing tools acting as a universal package manager.

## Enable System Management

Start by navigating to the System Environment screen by using the side navigation menu and toggle the "Enable System Environment" switch.

In your shared assets folder, a `system` folder is created like a standard environment with the exception there is an extra `env` file. This env file provides a way to export extra environment variables and a command for launching the environment through JoyDX should there be any tools such as Podman which need to be launched at the same time.

For the purposes of setup, enabling the system environment will also insert a sourcing directive in to your default terminal (e.g. $HOME/.zshrc if zsh was detected) configuration to include the env file.

To check whether the system environment was successfully setup, from a new terminal window (or existing window where you have manually refreshed the terminal configuration), if you run the following command you should see some output referring to the version of JoyDX you have installed

```shell
echo $JOYDX_VERSION
```

If you don't see any output after running the above operation, it may be possible JoyDX incorrectly detected your default shell. In this case, along the top of the System Environment management screen, there is an "Manual Setup Instructions" button you can push which will provide full instructions for activating the JoyDX system environment. 

## Managing your tools

The following screenshot represents an already configured system for demonstration purposes

![System Environment Management Screen](/system-environment.png)

1. **High Level Controls** - The toggle allows you to enable / disable the system environment without affecting the underlying system profile. i.e. Once disabled a flag is set in your environment file which simply bypasses sourcing and loading the tools. If you want to completely remove the system environment (including terminal configuration) from your device, you can click the remove environment button
2. **Provision from Role** - If your organisation has roles defined, you can use the dropdown menu to select a role and rapidly setup numerous tools in a single click. This is useful for bike-shedding
3. **Manage existing tools** - For tools already installed within the system environment, you can use the dropdown menu to select tagged versions of a tool. If you would like to install a specific version, you will need to edit your profile manually specifying a [version constraint](https://github.com/Masterminds/semver?tab=readme-ov-file#checking-version-constraints).
4. **Available Tools** - Choose from a list of tools you have not yet installed to your system environment either on an individual basis using the install button or selecting multiple tools at once using the checkboxes. In the case you use the checkboxes to select a tool, a new button will appear when you are ready to submit changes. By default, the latest version of a tool is installed so, if you would like to control the tool version, you will either need to use a role where you have defined a specific version or install the latest version and then change version.

When you install tools (or change version), the binary will be immediately available for use but, due to the way terminals have their environment variables configured, it is recommended to either open a new terminal window or manually source your terminal configuration to make sure that any possible changes to the environment variables are also updated.

That concludes the System Management introduction. You can now move on to the [Collaborate with Organisations](/collaborate-with-organisations) guide.
