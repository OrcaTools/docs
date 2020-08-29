# Config Management Modules


### Config Management Categories

When you think about it, most config management task will fall within 1 of the following 3 categories.

- Packages
- Files / Directories
- Services

#### Packages

Automating the configuration of applications sometimes (ok, most times) requires installing some underlying packges. This is one of the primary use cases for other config management tools such as Puppet, Chef, Ansible, or SaltStack. They all handle it in slightly different ways, but being able to install, uninstall, and upgrade packages is a definite requirement of any configuration management system.

In order to handle all package related tasks, Orcascript has a `package` module that ships with the stdlib. This means that there is nothing to import, or configure for managing package related tasks directly within Orcascript. Below are some examples of the methods provided by the `package` module.

```go
package.install("<packageName>", "<pacakgeVersion>")
package.installed("<packageName>", "<pacakgeVersion>")
package.upgrade("<packageName>", "<pacakgeVersion>")
package.uninstall("<packageName>")
```

Simple, right? Orcascript also provides a common absstraction layer on top of the underlying differences between Linux distros.
So, no matter which (supported) version of linux you are running the script on, it will always run the same way.

!!! warning
    If you write your scripts in such a way that you are using package names that are specific to a given distro,
    then that particular statatement will fail on versions of linux that do not support that particular package name.

    **NOTE:** This only matters if you want the same script to run on multiple distros. If you are only targeting a single
    platform, then this warning can be safely ignored.

    In such cases where you would like to support multiple distros with a single script, while still using specific package names and/or versions, you can always use the included `host` module to determine the underlying os. Then, simply switch based on `host.family` within your script, and provide the statement specific to that platform.
    
    Here is a psuedo snippet of what that could look like:
    ```go
    switch(host.family) {
        case "debian":
            package.install("<specific debian/ubuntu pacakge>", "<specific version (optional)>")
        case "rhel":
            package.install("<specific rhel/centos pacakge>", "<specific version (optional)>")
        case "alpine":
            package.install("<specific alpine pacakge>", "<specific version (optional)>")
    }
    ```

#### Files & Directories

When configuring a box, it is almost always required to write a configuration file to a path eg.`/etc/someapp/somedir`

While other scripting languages provide this functionality, orcascript has went above and beyond to make this as easy
as possible, with as little code as possible. 
The orcascript stdlib ships with an `os` module that provides methods such as `isfile`, `isdir`, `mkdir`, `read`, `write`
and many, many more, that will handle all of the the operations that come with managing a filesystem.

In addition to the `os` module, the stdlib also ships with a `template` module that provides template related methods such as `render` that will allow scripts to easily render templated configuration files in their proper directories, with the desired contents in place. 

For example, if you needed to create a file, ie `/etc/some-app/some.conf`, you could use the `template` module like so:

```go
// read in our example template file to a variable called 'tpl'
tpl := os.read("/path/to/my/config.tpl")

// define some example vars, 
// NOTE: you can load vars from many different sources.
// NOTE: they don't have to be inline, like this.
vars := {
    "somekey": "someval",
    "someOtherKey": "someOtherVal"
}

// once you have a template, and some vars, you can use the render method.
// this will write the file to the specified path, with the desired values
// injected into the formatted template.
template.render(tpl, vars, "/etc/some-app/some.conf")
```

Orcascript strives very hard to make it easy to manage any file system related task that you might encounter while attempting to write automation.


#### Services

The final "general" category that configuration management tasks usually fall into are services.
You may need to start, stop, restart or check the status of a given service. Orcascript makes this easy!
Yep, you probably guessed it. The orcascript stdlib ships with a `service` module that exposes methods
for each of those common operations.

Orcascript also provides an additional abstraction layer across the various system managers.
This includes, System V, systemd and others. 

Here are some examples of the methods that the `service` module provides:

```go
service.start("<serviceName>")
service.stop("<serviceName>")
service.restart("<serviceName>")
service.status("<serviceName>")
service.enable("<serviceName>")
service.disable("<serviceName>")
service.isup("<serviceName>")
service.isdown("<serviceName>")
```