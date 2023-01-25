+++
title = "Docker Bytepods"
date = "2022-12-10"
author = "Bogdan Munteanu"
description = "Docker Bytepods and what they solve"
+++

### [DockerHub page](https://hub.docker.com/r/bogdanmnt/bytepods)

Nowadays, the configuration of things like the terminal and code editor have become a part of each and every developer's personality, but setting them up can be a huge pain and becomes such a chore at some point. The best solution that i tought of was to create a development enviroment which can be accesed by the developer anytime, anywhere.

'These things already exist', you might say, and it is true, you can subscribe to VPS's and stuff like that, but they can get really expensive, really fast if you want better performance or more storage. So what if you could acces a development enviroment that is hosted on your computer at home or at work from anywhere, even if you don't have a static IP address?

According to 'text-davinci-003', by OpenAI, Docker is a containerization platform that enables developers to package applications with all of their dependencies into a single, standardized unit for software development, deployment, and delivery. Docker allows developers to isolate applications into individual containers, enabling them to run on their own without affecting the underlying infrastructure. Docker also provides access to a vast library of pre-built images and containers, making it easier to quickly deploy applications in a variety of environments.

Thus, Docker proved to be the perfect tool to make my idea possible. I used it to automate the creation of a new development enviroment on your computer (which i later named Devpod), which can be easily accessed via SSH. The Devpod uses 'Alpine Linux' at its core, as it is lightweight and it can provide great perfomance no matter the hardware.

In order to make SSH access possible without a static IP, i used ngrok, specifically their SSH Tunneling service.

You can see in the following diagram how SSH tunneling works:

![SSH tunneling diagram](/img/ssh_tunneling.png "SSH tunneling diagram")

## How to use it

### Setup

First of all, create a ngrok account and get hold of your access token.

To start the container, execute the following command:

```sh
sudo docker run -itd --network=bridge -p 4040:4040 -p 22:22 -e NGROK_AUTHTOKEN=YOUR_TOKEN_HERE --name CONTAINER_NAME bogdanmnt/bytepods tcp 22
```

Relpace YOUR_TOKEN_HERE with your ngrok token and CONTAINER_NAME with whatever you want.

To start the SSH service, run:

```sh
docker exec -itd CONTAINER_NAME /usr/sbin/sshd -D
```

### Login details 👋

Use SSH to access the Devpod: SSH root@ADDRESS -p PORT You can find the ADDRESS and the PORT by going to localhost:4040 on the host machine (store the address and port somewhere, as they will not change for as long as the container is not restarted)

Example:

```sh
ssh root@7.tcp.eu.ngrok.io -p 14163
```

## Conclusions

This project represented my first experience with Docker and DockerFiles. It represented a major learning oportunity, as Docker is at the core of almost any backend in today's world, and it has also helped me understand SSH and Hole Punching better.

## Used learning resources

[Article on p2p NAT](https://bford.info/pub/net/p2pnat/) \
[Docker Documentation](https://docs.docker.com/) \
[Youtube Video on Docker Containers](https://www.youtube.com/watch?v=eGz9DS-aIeY&t=1169s) \
[Youtube Video on Docker Networking](https://www.youtube.com/watch?v=bKFMS5C4CG0&t=333s)
