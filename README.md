# JoyDX Wiki - Guided Tour

## Organisation specification

* Roles are tooling specifications that can be used to automatically prepare the system environment for a user
* Environments are collections that reproduce working systems comprising of one (or more) applications configured to work together
* The Wiki is custom content that will be used to render a technical documentation web site which can be used for onboarding and support

## Wiki Customisation

The wiki will automatically bake some useful content relating to environments and roles but, it is very likely you will want to customize the home page and maybe add some custom pages.

The technical wiki will consume directories and markdown pages in the following manner.

* `wiki/_index.md` is the site home page
* `wiki/about.md` (for example) will make a page available at `site_url/about`
* `wiki/test/first.md` (for example) will make a page available at `site_url/test/first`
* For displaying custom pages within the top navigation, include the following frontmatter `menus: main`
* Putting environment and role specifications within the respective paths will automatically create content pages and menu entries
