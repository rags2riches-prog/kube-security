---
layout: post
title:  "Kubernetes Security: Our Simplified Security Model"
date:   2024-06-03
permalink: /kubernetes-security-model-intro.html
categories: security
author: Vincenzo Tagliavia (CKA, CKAD, CKS)
---

Kubernetes developments are inevitably complex. The complex intricacies of the platform coupled with OS Kernel dependencies and distributed microservices runtime issues, make Kubernetes environments susceptible to cyberattacks from different fronts, vulnerabilities and most ot the time, human-led preventable mis-configurations.

## Security Model: a Unique Approach

Security is a complex business. In order to capture the inherent complexities around setup, system hardening and maintenance, we adopt a security model that combines several principles and well-known frameworks into a single, easy-to-digest "context-driven" path to security.

![security model I](./assets/images/security-model(1).png)

Our security model quickly identifies the context where immediate actions are needed (more on this later). 
These "contexts" enviroments are as follows:

- Application and Microservice Layer
- Orchestrator Level and
- System Layer, which includes Kernel space components, Drivers and Hardware


The graph above is extremely simplified and still, it gives a good overview of the request-response cycles that go **unfiltered**, and that is, occuring at all time with no interventions and with the default configuration at runtime.
"Layers" are then placed redundantly across different contexts and components of our infrastructure.
What we want here is to apply security in depth and with finer granularity for each and every context / component.
We want to gradually restrict access from/to resources exactly as we want.


## How is our model different from others?

![security model (II)](./assets/images/security-model(2).png)

You may notice the above graph represents the same model presented previously except that we now add some additional layers and lay out the entire stack vertically.
You may also notice two intermediate blocks (our example "layers") between the user and the kernel space. 

KATA Containers, gVISOR, and Kernel MAC Modules are there as an example -- you do not have to implement the exact layers but the principle is exactly the same;
**restrict system call access** and provide various **isolation mechanisms** which reduce or eliminate altogether blast radius and platform escalations.

Now, we said before our approach to security is unique.
We also said we use several security principles combined together because this has a compounding effect in hardening and securing our whole infrastructure, not just our runtime applications and workloads.

- AAAA
- Principle of Least Privilege (POLP)
- Zero-Trust Security

The added "A" in the commonly used AAA model (Authentication, Authorization, Auditing) stands for Admission Controllers.
These are native built-in kubernetes objects, which could also includes third-party webhooks for mutating and/or validating a request.

If you take another look at the previous graph, you may notice an additional model of security there: the Cloud Native Compute Foundation (CNCF) Security Model.
The CNCF Security Model is an extention of the CISA Security Whitepaper and it represents a typical DevOps pipeline including four different but interrelated phases.

![CNCF Model](./assets/images/cncf-security-model.png)

The CNCF Security Model starts at the very first phase: Development.
Each phase depends on the previous one so if tests or policies applied during development fail, the distribution phase does not start. That's all well and good.
But this model by itself presents a number of different challenges:

1. It may not always be possible to start at the Dev phase for a number of different reasons (lack of capabilities, knowledge, organization policies, etc.)
2. The model suggests running things sequentially so that it may not be desirable to do that in enviroments where performance is an important requirement
3. You may not have access or control over the whole pipeline phases; for example, in multi-tenancy enviroments, an administrator may not even known the developers behind the workloads running in the cluster and this means that some horrors happening during a previous phase you have no knowledge about, will crawl into your cluster at runtime.

Since the bulk of security solutions in the market (SaaS, cloud-managed services) are concerned with the runtime phase, we use the CNCF Model as an additional guiding tool to uncover potential vulnerabilities in environments we may not have direct control over. It's like applying a tri-dimensional security suite where contexts and combined security models are our X and Y axis while the CNCF phases are together represented as the Z axis. This is a powerful, multi-dimensional, cost-effective supply chain solution for all your Kubernetes clusters.

## Which problems we want to address with Kubernetes?

We offer unbiased, independent, and no-frills services around security and more. 

We help diagnose vulnerabilities across different layers (e.g. cluster, microservice, image binaries, OS), using native built-in Kubernetes objects, and non-commercial, best-in-their-own-class open-source software. 

Furthermore, we can integrate workflows with your existing team as independent kubernetes admin / developers so that necessary changes to harden or improve your systems are implemented efficiently. This substantially reduces the attack surface and helps teams tapping into not well known Kubernetes features for free, rather than paying external providers for abstractions or wrappers around these objects. 


Email Us Now for A Quick and Free Consultation.
