ZSH Profiles
================================================================================

This project contains a simple module that facilitates sourcing different
`zsh` files on terminal start-up based on which projects you are working on.

Installation
================================================================================

1. clone this project
2. source `profiles.zsh` from your `.zshrc`

Usage
================================================================================

This projects adds the command `profile` to your shell. Using this command you
can activate or deactivate multiple _profiles_. For the purposes of this
project, a _profile_ is simply a `zsh` file that needs to be sourced when you
start your terminal. This is useful when you need to work on different projects
that require you to setup your environment in a specific way before being able
to work, but still want to keep your `.zshrc` clean.

Profiles are stored in `~/.config/zsh/profiles` and are expected to end in
`.zsh`. When specifying a profile on the command line, its name is the same as
the corresponding profile file, minus the `.zsh` extension. For instance, the
file `~/.config/zsh/profiles/example.zsh` will be referenced as `example` in the
command line.

You can activate a profile by typing:

	$ profile activate <profile name> [profile name...]

This will activate all the profiles that are specified on the command line. When
a profile is activated, the corresponding file in `~/.config/zsh/profiles` is
sourced in your current shell, as well as at start-up in all future shells.

Deactivate a profile by typing:

	$ profile deactivate [profile name [profile name ...]]

Passing no arguments deactivates all profiles. When a profile is deactivated, it
will no longer be sourced at start-up of new shells.

You can edit an existing profile, or create a new profile with the convenience
command:

	$ profile edit <profile name>

This will open your `$EDITOR` to the corresponding new or existing profile file.

To see the currently active profiles, type:

	$ profile ls-active

To see a list of installed profiles (files inside of `~/.config/zsh/profiles`),
type:

	$ profile ls-installed

This project ships with convenient tab completion.

FAQ
================================================================================

* **Q**: Why did you make this?
* **A**: I sometimes have to work on different projects that hijack my
  environment by introducing hundreds of new functions and variables inside of
  my `.zshrc`.  [ROS](https://www.ros.org) is a bit of an offender in this
  regard, but some projects go even further and add their own crazy wrappers and
  functionalities around this. Usually I do not want all of these things set in
  my terminals all the time, and often some of the settings in some projects
  tend to clash with the settings in other projects. The usual solution is to
  confine a project's additions to its own file and just source this in your
  `.zshrc` file. However, since my `.zshrc` file is tracked by `git`, I don't
  want to fill my history with a bunch of useless commits where I just change
  the files I sourced for my current project. This project decouples the
  sourcing of these projects from the files tracked in my git history.

* **Q**: Is this an over-engineered solution?
* **A**: Absolutely
