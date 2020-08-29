# Intro

This section will go over how we can use `orcascript`, along with `orcaem` to provide Event Management capabilities.

The `orcaem` agent allows you monitor your systems and automate responses to events as they occurr on the host.

### A Simple Example

Lets say that you want to watch the `/var/logs/nginx/error.log` file and when it reaches a certain size, you want to rotate the log. Using `orcaem` you would define a condition that says "when log file `error.log` is `<n> MB` in size, execute `rotate-error-log.orca`. 
When the condition is met, the response system within `orcaem` would automatically execute the `rotate-error-log.orca` script and the log would be rotated.

As you can see, this tool can be very useful for SRE related automation tasks, as well as security focused operations.
