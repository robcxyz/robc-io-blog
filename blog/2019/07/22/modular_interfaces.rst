Modular interfaces
==================

So I'm trying to modularize a bunch of terraform code and I get stuck on the idea of coupling.  To couple or not to couple is always the greatest question.
Right now I format my terraform based on a sort of hierarchy where I go something like this:

::

    ├── infrastructure
    │   ├── dev
    │   │   ├── terragrunt.hcl
    │   │   ├── us-east-1
    │   │   │   └── ec2
    │   │   │       └── terragrunt.hcl
    │   │   │   └── some other service
    │   │   │       └── terragrunt.hcl


**Note that both Resource Group and Service are optional.  Simple deployments would maintain one level**


So this hierarchy is critical to everything as when we use tools like Terragrunt, we persist the state in a remote object store based on a key structure
that is reflected from the naming of the folder hierarchy that we store the configuration files in and run from.  Thats a lot of information
that honestly, you are best off reading `this doc <https://blog.gruntwork.io/how-to-manage-terraform-state-28f5697e68fa#isolation-via-file-layout>`__
if you really want to dive and understand the justification to all of this.  Instead so lets just show an example.

Lets say we have a repo like this.

::

    ├── infrastructure
    │   ├── dev
    │   │   ├── terragrunt.hcl
    │   │   ├── us-east-1
    │   │   │   └── ec2
    │   │   │       └── terragrunt.hcl
    │   │   │   └── some other service
    │   │   │       └── terragrunt.hcl



.. author:: default
.. categories:: none
.. tags:: none
.. comments::
