# Pihole with unbound redis caching

## Before starting this podlet

You have to set your folder location inside the podlet before starting it. It has to be full path, **NOT** relative! Use the folder structure! Or create your own. <br />
To allow podman to use port 53, add this to sysctl.conf: ``net.ipv4.ip_unprivileged_port_start=53``. <br /> Source: https://github.com/containers/podman/blob/main/rootless.md <br/>
After you done all of that, copy pod-pihole.kube into ``~/.config/containers/systemd``.
If it doesn't exist, use this command: ``mkdir -p ~/.config/containers/systemd``. </br >
Then ``systemctl daemon-reload --user`` and ``systemctl start --user pod-pihole``. <br />
If it doesn't work, check the systemd logs. I use Cockpit to check the logs. <br />
Now open port 53, and optionally 80 for the pihole UI and try it out! Don't forget to set your server ip to a static address. </br >
It is worth mentioning that you can ignore unbound warning messages. Not sure what affects it has on the performance overall. Though if it bothers you too much then put this in sysctl.conf:
``net.core.rmem_max=4194304`` and ``net.core.wmem_max=4194304``. It'll remove some of the warning messages.

### Unbound

Unbound has remote control enabled by default. Please follow this instruction:
Furthermore, this unbound instance is **NOT** recursive, instead it just forwards requests to using TLS to Cloudlfare.
Why even bother with unbound if that's the case? Well, at least the cache doesn't disappear when the container reboots.
Because this version of unbound has redis support compiled into it, which connects through unix socket.

### Pihole

Please generate the web password before starting the podlet.
Perhaps you want to set your REV_SERVER, timezone and other configs as well.


### ~~Redis~~ Valkey

You don't really have to do anything to set this thing up other than check the config if it is okay for your specific use case
