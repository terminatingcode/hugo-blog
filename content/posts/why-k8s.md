---
title: "Why Kubernetes?"
date: 2018-07-30T19:22:31+01:00
thumbnail : "images/k8s_banner.png"
draft: true
tags: ["kubernetes", "icons", "8bit"]
categories: ["kubernetes"]
---
In the world of DevOps, the new, cool kid on the block is definitely Kubernetes (or K8s if you're really cool). Written in Go and originally developed by Google, Kubernetes is an open-source project that essentially boils down to a container scheduler. Its main goal is to provide a platform to aid in the orchestration of deploying applications in containers on a distributed cluster of hosts.

While you may be thinking that by that description, Kubernetes may not sound glitzy or glamorous or necessarily game-changing. And to be honest you would be right. The concepts and ideas that Kubernetes builds upon are not new or innovative. The difference is that Kubernetes brings together a whole boat-load of really, good sound principles that the industry as a whole has been moving toward for some time. So what are these opinions and why should we care?

## Containerization

{{%img src="images/container_red_500px.png" caption="Docker Container"%}}

The most fundamental aspect of Kubernetes is that software applications should live and run on containerized systems. More specifically, Kubernetes integrates with [Docker](https://www.docker.com/) and [rkt](https://coreos.com/rkt/) containerization systems. Containers allow you to deploy an application to operating-system-level virtualization which is a fancy way of saying that containers are user-spaces that sit above the kernel level which are isolated from the rest of the system. The argument for containers over virtual machines is that there is far less overhead than a virtual machine because it makes use of the OS's system call interface. This allows you to have a small, neat little package containing your app. Even better, this means that you can fit far more containers on a machine than virtual machines.

## Immutability and Declarative Configuration

Because containers are smaller than virtual machines, they are also quicker to create and destroy - enabling users to easily employ an immutable system. For clarity, most systems have traditionally been mutable systems where servers are created and setup with scripts to download and install the desired dependencies to achieve the desired state. When this desired state changes, the existing server is usually updated by installing new versions and hoping the world doesn't fall over. The issue being that if it does, it can be a bit of a pain to revert these changes and go back to the previous setup.

Kubernetes, on the other hand, forces you to use immutable systems and declarative configuration objects. In a Dockerfile and a Kubernetes spec, you declare what your desired state of the world is and it creates that desired state.

{{%img src="images/spec_250px.png" caption="Kubernetes Spec"%}}

Therefore in order to do an upgrade in Kubernetes, a new image or replica is created. If all goes well with this new image or replica, the previous one is destroyed. Dockerfiles are easily version controlled and images can be stored locally and remotely to avoid having to rebuild an image. This makes it easy to restore a previous state and build or use that previous image.

<div class="flex-class">
<table style="width:100%">
<tr>
<th>{{%img src="images/container_red_250px.png"%}}</th>
<th>{{%img src="images/container_250px.png"%}}</th>
</tr>
<tr>
<th>{{%img src="images/container_exp_red_250px.png"%}}</th>
<th>{{%img src="images/container_250px.png"%}}</th>
</tr>
</table>
</div>

## Decoupling & Microservices (and how it helps you scale)

Another principle that Kubernetes supports is that of decoupling and microservices. Each layer of Kubernetes is separated in the Kubernetes stack and communicates via APIs. In addition, the intended design of a Kubernetes system is to have each Pod, commonly referred to as the "atomic unit" on the Kubernetes platform, contain all that is needed to run a microservice. This can be a single containerized application or a container and a shared storage and other tightly coupled containers. Everything contained within a container shares an IP and port space and information on how to run the containers within. Pods can be tied to a Node, a worker machine, that can be scaled up or down and created or destroyed.

Why should we separate the application logic into microservices? Well, typically, we create a new application with everything it needs. Normally this is because we are on a budget or low on time and just want to minimal viable product on a single server. If this is never separated out, this becomes a monolith.

{{%img src="images/cameraman_monolith_216_240px.png"%}}

I like to think of monoliths as a camera operator who is a production company of one. They deal with the camera, the sound and the lighting and can get by just fine doing wedding videos. However, once demand increases, the system does not scale and there is only one camera operator to be in any one place at one time and can only carry so many things. So they hire a second person and now they can tackle twice as many events.

But then they start getting demand for higher value gigs and the new requirements are multiple camera angles, better, multiple lighting types and different audio sources. The logical thing to do is to have the camera operator only handle the video camera and to hire a sound operator and a lighting operator and hire more or less based on the gig. That way the requirements are scaled up and down based on the desired state required and can be removed if not needed. Let's say a gig requires special effects. We would have the camera operator deal with the added special effects, rather it would be fairly logical to contract out the work for gigs here and there when needed rather than have to pay the camera operator more to acquire the skill. Think of this as requiring a larger server to accommodate a small feature that is only used occasionally and doesn't need to be scaled with the entire system.

<div class="flex-class">
{{%img src="images/reporter_96_240px.png"%}}
{{%img src="images/cameraman_152_240px.png"%}}
{{%img src="images/lighting_tech_176_240px.png"%}}
{{%img src="images/steady_cam_128_240.png"%}}
{{%img src="images/light_reflector_120_240px.png"%}}
{{%img src="images/boom_mic_240_256px.png"%}}
</div>

The downside of this is that in order for microservices to communicate, they require APIs or some other layer of abstraction. This does add a certain amount of overhead and size to each service. However, it should never be so much of an overhead as to surpass the benefits and if it does then that discussion is definitely worth having.

## Efficiency (or $$$)

Probably the most compelling argument, at least the one most operators use when speaking to higher-ups, is that having your infrastructure use Kubernetes saves you money. Here's a bullet point list of reasons as an easy summary:

- *Savings on machine use* as containers are smaller and Kubernetes optimises the distribution of containers over a cluster of machines
- *Reduced operator time* to maintain the system as Kubernetes is a *self-healing system* that ensures a certain number of replicas at all times.
- Separation of concerns as services are divided into microservices that can be easily scaled up and down. If done properly, this translates into *lower app developer overhead* as code should be more easily understood and modified. This should also translate to *less resources needed to scale* up and down as only the services needed are scaled rather than the entire system.

### For More Information
[Kubernetes Up and Running](https://books.google.co.uk/books/about/Kubernetes_Up_and_Running.html)

[Kubernetes Basics](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

[Creative Commons Icons](https://github.com/terminatingcode/k8s)
