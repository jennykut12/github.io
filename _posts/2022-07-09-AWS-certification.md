---
layout: post
title: AWS certification
subtitle: Introduction to AWS
categories: Markdown
tags: [Markdown, journaling, blog, AWS, IntroductiontoAWS]
---

## THE 4 DOMAINS IN THE SOLUTIONS ARCHITECT ASSOCIATE EXAM

    Domain1: Design Resilient Architectures
    - 1.1 Design a multi-teir architectur solution
    - 1.2 Design highly available and/or fault-tolerant architectures
    -1.3 Design decoupling mechanisms using AWS services
    -1.4 Choose appropraite reslient storage
    Domain2: Design high Performing Architectures.
    - 2.1 Identify elastic and scalable compute solutions for a workload
    - 2.2 Select high performing and scalable storage solutions for a workload
    - 2.3 Select high performing networking solutions for a workload
    - 2.4 Choose high-performing database solutions for a workload
    Domain3: Design secure Applications and Architectures
    - 3.1 Design secure access to AWS resources
    - 3.2 Design secure application tiers
    - 3.3 Select appropriate data security options like file system access and encryption
   Domain4: Domain four is design cost-optimized architectures
    - 4.1 identify cost effective storage solutions
    - 4.2 Identify cost effective compute and database services
    - 4.3 Design cost-optimized network architectures

    ##Overview of the IAM service, the Identity and Access Management Service.

IAM is the identity and access management service, and it's a way that we can authenticate and be authorized to access services on AWS.
So let's say we're connecting to an AWS service via either the management console, the command line interface or the API. We'll connect to AWS IAM and we can then authenticate and all principles must be authenticated to send requests.

What is a principle?

A principle is a person or an application that can make a request for an action or an operation on a resource. Now, actions and operations are both where we're using the API to interact with an AWS service.
We have users roles, federated users and applications.
We then have a couple of types of policy so we can assign permissions to users and then we can use policies to control access to resources.

We have identity based policies and resource based policies, and these determine whether to authorize the request, whether to allow or to deny the request to the resource. Once you've got an allow or deny, assuming as a deny in this case, you're then able to run an action against a resource.

Note that everything in AWS is an API call. So when you're trying to launch an issue to instance, you're basically executing the run instances command.

If you're trying to get information about an S3 bucket, you're running the "getBucket" API action. And if you're trying to create a user in IAM, you're running the create user action.

So whatever resource you're interacting with in AWS, an API action is actually being executed and you need to have the permissions assigned to your accounts and you need to be allowed for a policy to be able to actually perform that specific action. So that the actions are then authorized on the AWS resources.

 Quick overview of what this service does.