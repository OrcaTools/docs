# Intro

Orcascript was specifically engineered for Config Management tasks.

There are several other tools available, and some that are quite popular, for config management operations.
As of this writing, probably the most popular of those tools is Ansible.

In this brief intro, I'd like to outline some of the key differences between Ansible, and Orcascript.

Ansible playbooks are written in YAML. Ansible does try to provide some logical operations within it's specific flavor of YAML, but its not a scripting language. It does lack some control that many would find very useful. 

Orcascript, on the other hand, is a full blown scripting language, designed for automation tasks! Check out the <a href='/Syntax Guide/'>Syntax Guide</a> to see all of the features!
This means when you need a if statement, its there. When you need a for loop, its there. When you need to easily interact with REST APIs, its there. Some of these basic things that we take for granted, just arent available in YAML, and require additional overhead within a YAML processor (like Ansible) to address these issues. Limitations such as this do cause intersting issues, and in part, is what helped inspire Orcascript to begin with. Orcascript, bypasses all of these issues because it's not designed around YAML.

Ansible playbooks / roles are often times organized in a mutli-directory structure. Standardization is great, but sometimes having to dig through multiple directories, or comb through *way too many* yaml files isn't ideal. Orcascript has a single file approach to help reduce the directory & file sprawl.

Ansible is agentless, and it connects to target machines via SSH to execute playbooks.
This approach is ideal, as it doesn't require any setup to run against a known set of targets. It's one of my favorite things about Ansible.

Because at the end of the day, it is just a script, there are many ways one could execute an orcascript. The only underlying assumption is that the `orca` binary has been installed to the path on the machine that will execute the orcascript. The same is true for Python, Bash, Node, etc.
The difference is that the `orca` binary would not be installed on the machine by default.

Assuming that `orca` is in the path, for cloud environments, where userdata (cloudinit) is readily available, one could simply download the desired script and execute it on the machine at startup to bootstrap it into a desired configuration. Orcascript has a unified scripting interface, so that no matter which supported distro you choose to run on, typically, the same script can run across any supported distro.

For more advanced use cases, the `orca` binary can also connect to target machines over SSH (similar to Ansible) and execute a given orcascript on remote machines.

Continue reading about <a href='state'>Declaritive State Defintions</a> to better understand some of the differences between Orcascript and Ansible.