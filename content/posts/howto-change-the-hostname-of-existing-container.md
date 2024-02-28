---
title: "How to change the hostname of existing container"
date: 2024-02-28T09:58:00Z
subtitle: ""
slug: ""
tags: ["english", "docker", "container", "hostname"]
aliases: ["/2024/02/howto-change-the-hostname-of-existing-container.html"]
type: post
---

Hello every body, welcome to my blog!

This time I will share with you, how to change the hostname of existing container.

Ok, without further ado, let's get started.

First, we need to find the id of container which we would like to change its hostname.

Run this command at terminal to list the available containers:

```bash
docker ps -a
```

, and press ENTER.

![container list](/images/container-list.png)

In this example, I will change the hostname of `alpine` container, so that I copy its container id, the first-12-characters-of-container-full-id.

To check the default hostname of `alpine` container, just run this command at terminal:

```bash
docker exec alpine sh -c 'hostname'
```

, and press ENTER.
![old hostname of alpine container](/images/old-hostname-of-alpine-container.png)

AS you can see above, the hostname of alpine container is the first 12 characters of its container full id (`5fcce8e72c1f`).

For running subsequent commands which need `root` access, it would be helpful if we switch to user `root` by running this command at terminal:

```bash
sudo su
```

, and press ENTER (current user must belongs to sudoers).

Next, we check the status of docker service by running this command at terminal:

```bash
systemctl status docker
```

, and press ENTER.
![docker service status is running](/images/docker-service-status-is-running.png)

If docker service is running, then we must stop it.
As you can see in this example, docker service is triggered by `docker.socket`,
Therefore, we just need to stop `docker.socket` by running this command at terminal:

```bash
systemctl stop docker.socket
```

, and press ENTER. Please wait for about a minute to let the process finished.

After that, we recheck the status of docker service by running this command at terminal:

```bash
systemctl status docker
```

, and press ENTER.
![docker service status is inactive](/images/docker-service-status-is-inactive.png)

See, docker service is now inactive aka dead.

Next, we change directory to `/var/lib/docker/containers/` by running this command at terminal:

```bash
cd /var/lib/docker/containers/5fcce8e72c1f
```

, press TAB and then press ENTER. That container id will expand into full id. See below image:

![cd-into-var-lib-docker-containers](/images/cd-into-var-lib-docker-containers.png)

Next, we will change the hostname by running this command at terminal:

```bash
nano config.v2.json
```

, and press ENTER.

Next, search for the default hostname (first-12-characters-of-container-full-id), by pressing
`Ctrl + W`, then type `"5fcce8e72c1f"`, and press ENTER.

That's it, we already found the old hostname. Then we just need to change the default container hostname to the new hostname. In this example, I change it into `alpine`.

Then, search again for the default hostname, by pressing `Ctrl + W`, and pres ENTER (we don't need to type the search term again, because we search the same term). If an instance of the old hostname is found, just rename it to the new hostname.

Repeat the above step until an instance of the old hostname is not found.
![the-old-hostname-has-been-replaced-with-the-new-one](/images/the-old-hostname-has-been-replaced-with-the-new-one.png)

Then, save the update by pressing `Ctrl + S`, next, exit from nano by pressing `Ctrl + X`.

After that we must start docker service to enable us to see the result of hostname update, by running this command at terminal:
`systemctl start docker.service`, and press ENTER. Please wait for about a minute.

Next, we exit from root access by typing: `exit`, and press ENTER.

Next, we start the container, in this example, it's `alpine` container, by running this command at terminal:
`docker start alpine`, and press ENTER.

Next, we need to recheck the hostname of `alpine` container, by running this command at terminal:
`docker exec alpine sh -c 'hostname'`, and press ENTER.

![the-new-hostname-of-alpine-container](/images/the-new-hostname-of-alpine-container.png)

See, the new hostname has been applied. Congratulations!

OK,

I think that's all for now. Hopefully this tutorial will be helpful for others.

Thanks a lot for watching. Have a great day. See you.
