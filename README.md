# bob.embedded.systems

To check out this project, clone with submodules (for basement layers):

```
git clone --recurse-submodules https://github.com/sbixl/bob.embedded.systems.git
```

As the environment for Bob, a Vagrantfile is provided which will create a
virtual machine with ubuntu 23.10 and install bob. The git repo is shared
between the host and the virtual machine and the Bob project is built in the
home directory but the recipes are in the shared folder (see `bob init`).
Install Vagrant and VirtualBox and then run (if a password is required, it is `vagrant`):

```
vagrant up
vagrant ssh
```

You should get a shell in the VM and be able to run any bob commands on the project immediately.

*Note: Ubuntu 23.10 is required because glibc > 2.36 is required by the basement
layer of bob.*

Build the project with:

```
bob dev sbc/board::rpi/board::rpi-variant-4-b-64-bit -v
```
