# Declartive State Definitions

A declaritive state definition will determine exactly what state the machine executing the orcascript should be in.
These definitions, by design, allow for idempotent execution. By declaring the desired state, you can run and re-run 
the given script as often as necessary to ensure the machine stays in the desired state. If the machine is already in 
the desired state, no action will be taken. Any part of the machine that is not in the desired state will be reconfigured
to the desired state whenever the script runs.