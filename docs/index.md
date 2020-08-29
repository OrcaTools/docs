# Welcome

!!! warning "UNDER ACTIVE DEVELOPMENT"
    OrcaTools is under active development. Any information here is subject to change without warning, until we reach our
    first stable release. Any binaries downloaded from this site are "as is" and you use them at your own risk.

## OrcaTools Use Cases

The outline below illustrates some high level use cases for OrcaTools.

#### Config Management
    - bootstrap machine configuration at startup
    - prevent misconfigurations on day N of the machine's lifecycle
    - automate and manage operations across a fleet of machines

#### Task Management
    - automated testing
    - automated deployments
    - remote task execution
    - any type of ci/cd pipeline work

#### Event Management
    - respond to host events in realtime
    - manage condition response policies across a fleet of machines
    - early intrusion detection capabilities

#### Secrets Management
    - manage hundreds of secrets inside of single encrypted file
    - easily export secrets as environment variables
    - can optionally require multiple passwords to unlock the lockbox
    - lockbox supports mfa

### Supported Operating Systems

OrcaTools officially supports the following **linux** operating systems:

| Operating System | Supported Versions |
| ------------- |------------- |
| Debian | Stretch, Jessie, Buster, Bullseye |
| Ubuntu | 14.04, 16.04, 18.04, 20.04, 20.10 |
| RHEL | 7, 8 |
| CentOS | 6, 7, 8 |
| Alpine | 3 |

**NOTE:** While our tools may work on other distros not mentioned here just fine,
we are only listing the distros we actively test against. As we add support for other distros
or versions, we'll update this table to reflect that support.