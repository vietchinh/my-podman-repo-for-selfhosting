# my-podman-repo-for-selfhosting

This is my cobbled together podman podlets over the years, now public for anyone who is eager to join the podman ecosystem.


My personal reasoning for podman below, if you are interested, maybe it'll convince you to switch:

I chose podman for a few reasons. First is obviously the rootless nature of podman, improves security, which they, as in I think Red Hat claims(I need to fact-check this).
Secondly is the daemonless nature and its integration with systemd. While some may scoff at systemd, you cannot argue that it's pretty handy to set and forget a container with auto-update. Auto-update that doesn't require a watchtower container! Thirdly, my usage of Red Hat ecosystem, as in using Cockpit and Fedora CoreOS. Most if not all my podman management is through Cockpit, with the added bonus that I can also manage my server! And the funny bit is that I run Cockpit rootful via podman, ain't that great. (I find it great, though I must specify that I run Cockpit-ws rootful, the other packages like Cockpit-podman has to be installed separately).
