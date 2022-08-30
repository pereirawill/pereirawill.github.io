---
title: "Vagrant"
linkTitle: "Vagrant"
weight: 100
description: >
  Vagrant is a utility for managing the lifecycle of virtual machines.
---

Vagrant is a very powerful tool to manage and create virtual machines and development environments! You can easily create a virtual environment by defining a Vagrantfile that can be shared across your team or anyone. 

You can test deployment tools, scripts and configurations in a disposable environment. 

It can a be a cheaper and quicker way to test deployments and Infrastructure as code config.
## 1. Getting Started
To install vagrant check Hashicorp documentation [here](https://www.vagrantup.com/docs/installation).
You will also need to install a provider such as [virtualbox](https://www.virtualbox.org/wiki/Downloads) or Hyper-V.

Once you have  vagrant installed, type `vagrant` and see the list of available commands.

{{% alert title="Note" %}} Make sure you are in the same directory as the Vagrantfile when running these commands!.{{% /alert %}}

## 2. Autocompletion
Vagrant provides the ability to autocomplete commands. Currently, the bash and zsh shells are supported. 
These can be enabled by running `vagrant autocomplete install --bash --zsh`.

## 3. Creating a VM
- `vagrant init`           -- Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image. Before you can do vagrant up, you'll need to specify a base image in the Vagrantfile.

```bash
 $ vagrant init

A `Vagrantfile` has been placed in this directory. You are now
ready to `vagrant up` your first virtual environment! Please read
the comments in the Vagrantfile as well as documentation on
`vagrantup.com` for more information on using Vagrant.
```

- `vagrant init <boxpath>` -- Initialize Vagrant with a specific box. 
To find a box, go to the [public Vagrant box catalog](https://app.vagrantup.com/boxes/search). Choose a box according to your provider, hyperv, virtualbox, libvirt. Once you found a box you like, just replace it's name with boxpath. 
For example, `vagrant init ubuntu/trusty64`.

## 4. Setting your provider
If you work with multiple providers you might need to set/change the default provider when using vagrant up.

You can set a provider when running vagrant up or using an environment variable.
- `vagrant up --provider=hyperv`
- `vagrant up --provider=virtualbox`
- `vagrant up --provider=libvirt`

### Setting provider with an environment variable
#### on linux/MacOs
`export VAGRANT_DEFAULT_PROVIDER="virtualbox"` <br>
`export VAGRANT_DEFAULT_PROVIDER="vmware_desktop"`<br>
`export VAGRANT_DEFAULT_PROVIDER="libvirt"`

#### on Windows
`[Environment]::SetEnvironmentVariable("VAGRANT_DEFAULT_PROVIDER", "hyperv", "User")` 

## 5. Starting a VM
- `vagrant up`                  -- starts vagrant environment (also provisions only on the FIRST vagrant up)
- `vagrant resume`              -- resume a suspended machine (vagrant up works just fine for this as well)
- `vagrant provision`           -- forces reprovisioning of the vagrant machine
- `vagrant reload`              -- restarts vagrant machine, loads new Vagrantfile configuration
- `vagrant reload --provision`  -- restart the virtual machine and force provisioning

## 6. Getting into a VM
- `vagrant ssh`           -- connects to machine via SSH
- `vagrant ssh <boxname>` -- If you give your box a name in your Vagrantfile, you can ssh into it with boxname. Works from any directory.

## 7. Stopping a VM
- `vagrant halt`        -- stops the vagrant machine
- `vagrant suspend`     -- suspends a virtual machine (remembers state)

## 8. Cleaning Up a VM
- `vagrant destroy`     -- stops and deletes all traces of the vagrant machine
- `vagrant destroy -f`   -- same as above, without confirmation

## 9. Boxes
- `vagrant box list`              -- see a list of all installed boxes on your computer
- `vagrant box add <name> <url>`  -- download a box image to your computer
- `vagrant box outdated`          -- check for updates vagrant box update
- `vagrant box remove <name>`   -- deletes a box from the machine
- `vagrant package`               -- packages a running virtualbox env in a reusable box

## 10. Saving Progress
-`vagrant snapshot save [options] [vm-name] <name>` -- vm-name is often `default`. Allows us to save so that we can rollback at a later time

## 11. Tips
- `vagrant -v`                    -- get the vagrant version
- `vagrant status`                -- outputs status of the vagrant machine
- `vagrant global-status`         -- outputs status of all vagrant machines
- `vagrant global-status --prune` -- same as above, but prunes invalid entries
- `vagrant provision --debug`     -- use the debug flag to increase the verbosity of the output
- `vagrant push`                  -- yes, vagrant can be configured to [deploy code](http://docs.vagrantup.com/v2/push/index.html)!
- `vagrant up --provision | tee provision.log`  -- Runs `vagrant up`, forces provisioning and logs all output to a file

## 12. Plugins
`vagrant plugin install`
`vagrant plugin install my-plugin`
`vagrant plugin uninstall my-plugin`
## 13. Notes
- If you are using [VVV](https://github.com/varying-vagrant-vagrants/vvv/), you can enable xdebug by running `vagrant ssh` and then `xdebug_on` from the virtual machine's CLI.
