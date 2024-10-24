# Workstation configuration

This document aims to provide information how to setup your workstation
to access to the resources in the project. You already should have SSH
public and private keys in place created by using the command
`ssh-keygen` on your workstation and also one on the bastion workstation
VM. If not done yet, please follow the [Red Hat
documentation](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/9/html/configuring_basic_system_settings/assembly_using-secure-communications-between-two-systems-with-openssh_configuring-basic-system-settings#generating-ssh-key-pairs_assembly_using-secure-communications-between-two-systems-with-openssh)
to generate one with elliptic curves like ECDSA.

## Configure SSH Access

Please add following configuration on you SSH Config file which is
usually `~/.ssh/config`.

``` bash title="File ~/.ssh/config"
# Bastion Config
Host <bastion_vm_fqdn>
    HostName <bastion_vm_fqdn>
    IdentityFile ~/.ssh/id_ecdsa
    port 22
    ServerAliveInterval 300
    ServerAliveCountMax 2
    User <your_username>
    UserKnownHostsFile /dev/null

# SSH Clients
Host *.<project_fqdn>
    ProxyJump <bastion_vm_fqdn>
    User <your_username>
    IdentityFile ~/.ssh/id_ecdsa
    ServerAliveInterval 300
    ServerAliveCountMax 2
    UserKnownHostsFile /dev/null
```

This configuration will allow you to access all the resources in a
protected environment over SSH using Bastion Jumphost VM like in your
local network.

## Configure WebUI Access

The following configuration will help you to configure your workstation
access to the project resources with WebUI using a proxy on the Bastion
Jumphost VM. When configured you can access to the resources using their
local IP addresses or fully qualified domain name.

It is recommended to use a browser extension for automatically switching
between the proxies or direct access based on the rules for not
affecting your existing access definitions. The web resources in the
project could not exposed on Internet which you can not directly access
without using the configuration steps below.

1. Deploy browser extension named [`Switchy Omega Extension`](https://github.com/FelisCatus/SwitchyOmega).
2. Open the extension Options to configure a new profile with a name `rhis-bastion` and `Proxy Profile` option.
3. Navigate to the newly created profile and add `_<bastion_vm_fqdn>_` to the servers list with a proxy port number `3128` for HTTP access in default scheme.
4. Navigate to the ˙auto switch˙ profile and add add switch rules to use with `Condition Type` equal `Host Wildcard`, `Condition Details` equal `_<project_fqdn>_` and `profile` equal to `rhis-bastion`.
5. Ensure from the browser extension that `auto switch` profile set as default.

This setup will allow you to access WebUI's of the any application on the project.
