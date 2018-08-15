The ```git config``` command is a convenience function that is used to get or set Git configuration values on a global or local project level. These configuration levels correspond to .gitconfig text files. Executing git config will modify a configuration text file.

## Task

### Reading git config values / git config

The most basic use case for git config is to invoke it with a configuration name, which will display the set value at that name. Configuration names are dot delimited strings composed of a 'section' and a 'key' based on their hierarchy. For example: user.email

```git config user.email```{{execute}}

To list all variables set in config file along with their values, use;

```git config --list```{{execute}}

The name is actually the section and the key separated by a dot, and the value will be escaped.

### git config levels and files

Before we further discuss git config usage, let's take a moment to cover configuration levels. The git config command can accept arguments to specify which configuration level to operate on. The following configuration levels are available:

    --local

By default, git config will write to a local level if no configuration option is passed. Local level configuration is applied to the context repository git config gets invoked in. Local configuration values are stored in a file that can be found in the repo's .git directory: .git/config

     --global

Global level configuration is user-specific, meaning it is applied to an operating system user. Global configuration values are stored in a file that is located in a user's home directory. ~ /.gitconfig on unix systems and C:\Users\<username>\.gitconfig on windows

### Writing git config values / git config

Expanding on git config, let's look at an example in which we write a value:

```git config --global user.email "your_email@example.com"```{{execute}}

```git config --global user.name "My Name"```{{execute}}

This example writes the values to the configuration name user.email and user.name. It uses the --global flag so this value is set for the current operating system user. Go ahead and inspect the new configuration:

```git config user.email```{{execute}}

```git config user.name```{{execute}}

## Protip

* The user.name and user.email is the information of the author which will be recorded in any newly created commits.