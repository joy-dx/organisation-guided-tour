# JoyDX Wiki - Guided Tour

This repository represents a [JoyDX Organisation](https://joydx.com/docs/reference/organisation) for getting started with the main app. It is primarily delivered in the form of a wiki driven tour which helps the user get acquainted. For more information about the tour itself, read the [wiki home page](/wiki/_index.md) as markdown.

## Organisation specification

* `./environments` are collections that reproduce working systems comprising of one (or more) applications configured to work together
* `./roles` contains tooling specifications that can be used to automatically prepare the system environment for a user
* `./wiki` represents custom content that will be used to render a technical documentation website which can be used for onboarding and support

## Wiki Customisation

The [JoyDX Wiki](https://joydx.com/docs/reference/wiki) will generate custom pages based on the following:

* `wiki/_index.md` is the site homepage
* `wiki/about.md` (for example) will make a page available at `/about`
* `wiki/test/first.md` (for example) will make a page available at `/test/first`
* `wiki/test/second.md` (for example) will make a page available at `/test/second`
* For displaying custom pages within the top navigation, include the following frontmatter `menus: main`
* Putting environment and role specifications within the respective paths will automatically create content pages and menu entries. 
