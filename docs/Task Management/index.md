# Intro

This section will go over how we can use `orcascript` & `orcasrvr` as a Task Management System.

The `orcasrvr` provides a task management and execution system over a REST API. For clarification, a task is simply an `orcascript` that you would like to run. Anything you can write within Orcascript can be a Task. There are 2 methods to trigger a TaskRun within `orcasrvr`.

The first trigger is REST API invocation. Sending a POST request to `/tasks/:id/runs` will run the given task.
The second trigger is Scheduled invocation. You can also manage a Task's schedule via the REST API.