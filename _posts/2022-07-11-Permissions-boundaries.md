---
layout: post
title: Permissions Boundaries
subtitle: Read me
categories: Markdown
tags: [Markdown, journaling, blog, AWS, PermissionsBoundaries]
---

## Permissions Boundaries

Permissions boundaries are a really useful tool for controlling the maximum available permissions for our user accounts.

Here is a diagrams to show you how this works and use the diagram to understand the situation below.

So let's look at a situation. We've got Joanne here and she wants to access an S3 bucket and she wants to create a user in IAM. So she actually has a policy applied to her, which is a developer policy and that allows full control of S3, cloudWatch, ES2 And IAM. She should therefore be able to perform any actions she wants on free or IAM.

![datacamp certification](/assets/images/Permission1.jpg)

But there's also a permissions boundaries set. The Permissions Boundaries sets the maximum available permissions that Joanne can have. So we can see here we have an allow. The action is S3, CloudWatch, and EC2 and then a wildcard for the resource.
These can be applied to users and roles. So let's say that now Joanne attempts to list buckets on Amazon S3. She's going to be able to because she has two things she has S3 full control permissions here, and the permissions boundary also allows all actions on S3. So what happens now if Juyuan attempts to create a user in, IAM. Well, that gets denied. And the reason being is, even though she has a policy here which allows her full permissions to IAM. It's not allowed in the permissions boundary. So therefore it will fail, so it restricts the permissions available. Now you do still need the permissions in a policy. So in the case of free here, she does need to have free permissions.
You don't get granted permissions through the permissions boundary. But it controls what permissions you're able to use.

Privilege escalation is one of the use cases for why we implement permissions boundaries. It's something we want to prevent and you'll see why.
So let's say we have a user called Lindsay, and Lindsay is not a good user. She's got some bad intent and she actually has a permissions policy assigned to her that gives her full access to IAM.
However, she doesn't have any other permissions. So yes, she can do whatever she wants and IAM, but she's not actually able to launch AWS resources.

But let's see how Lindsay might be able to get around that restriction. She can create a user in IAM. And let's call this X user. And then she can apply the administrator access permissions policy to that particular user account.
So Lindsay is now able to get full administrative privileges by logging in as the account she just created. And then she might do something bad, like using a AWS Batch to mine some bitcoin. So not a good situation.

![datacamp certification](/assets/images/Privilage%20escalation.jpg)

Let's look at how we can prevent privilege escalation.
So we've got the same situation with Lindsay. She has the same IAM full access policy. But in this case, there's also a permissions boundary.
The boundary ensures that any users that are created by Lindsay have the same or fewer permissions, so she cannot create a user account that has more permissions than she does. So she might run create user. She can create X user again and attach the administrator access policy. But in this case, when she logs in as a user account, it won't have more permissions because those permissions will be restricted because of the permissions boundary.

![datacamp certification](/assets/images/Prevent%20previlage%20escalation.jpg)

So Permissions Boundary has really averted a serious situation here, and that's why it's really good to think about how you might use these when you assign permissions to your users.
