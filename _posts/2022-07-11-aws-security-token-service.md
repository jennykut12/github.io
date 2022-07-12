---
layout: post
title: The AWS Security Token Service(STS)
subtitle: explore the authentication options in AWS and Multi-Factor Authentication
categories: Markdown
tags: [Markdown, journaling, blog, AWS, IAM,IAMuser, IAMuseraccount]
---

## The AWS Security Token Service(STS).

This is the service that provides what are known as short lived or temporary credentials. So let's have a look at how STS works because it's important to understand this. So we have an EC2 instance. And in this case, this EC2 instance is running an application. And the application needs to write some files or read some files from an S3 bucket.
So how does the application running on EC2 get authorized to actually access S3?
What we can do is create something called an instance profile and attach an IAM role to the instance profile. We'll see how to actually do this later on in the course.
The EC2 instance will then attempt to assume the role by using the STS Assume Role API call. Now there's a couple of different types of policy that apply to the IAM role. You've got a trust policy and a permissions policy. We talked about permissions policies before. These define the permissions that are allowed or denied to this specific entity. But a trust policy actually controls who can assume the role. So who is allowed to assume this role and become that role and acts as if they are the role? And the policy document might look something like this. In this particular example, this policy is allowing the service ec2.amazonaws.com to assume roles using the STS Assume Role API action.
So the trust policy is going to allow the EC2 instance to assume the role. And the STS service gets involved and it will return temporary security credentials to EC2. And EC2 to can then access the S3 bucket with those temporary credentials.
The temporary credentials include an access key and a secret access key. They have an expiration and something called a session token as well. So these are provided to allow short term access. Remember, they expire after a short period of time. And it will be an automatic process to renew the credentials before they expire. And that happens using STS again.

Temporary credentials are used in several situations that includes Identity Federation, delegation, cross account access, and IAM roles.
STS is used in a lot of the operations that we're going to be looking into in more detail. So it's important to understand how it works. And hopefully, you've now got a good understanding.