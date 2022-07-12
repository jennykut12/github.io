---
layout: post
title: IAM Policy Simulator
subtitle: Read me
categories: Markdown
tags: [Markdown, journaling, blog, AWS, IAM,IAMuser, IAMuseraccount]
---

## IAM Policy Simulator

There is a link attached to this lesson that you'll need to follow to open the IAM policy simulator [Click Here](https://policysim.aws.amazon.com/home/index.jsp)

As seen on the webpage, this is the main page for the policy simulator. On the left hand side, we can choose users, groups, or roles. Let's keep it on users.
You user account on the left. Now,

- choose your user. 
- On the right hand side, I can then select a service. So perhaps I'm going to type EC2 and select the EC2 service.
- Now there's lots of API actions associated with this service. As you can see, there's a few hundred of them in fact. What I'm going to do is select all. And I can check for which permissions I have. 
-So let's run the simulation. And very quickly it returns these results. And it's showing each of the individual API actions and the permission is allowed. If I have all administrative right, definitely am allowed all of the permissions.

#### Let's now create an IAM user who will have fewer permissions and see how useful this tool is. Back in IAM, I've chosen users and I'm going to add a new user.
I'll call this user Sara, enable management console access with an auto generated password because we're not actually going to log in as this user. Now what I'm going to do is rather than adding to a group for this particular use case, I'm going to attach an existing policy directly.
So let's search for EC2. And I'm going to scroll down to where it says EC2 read only access. Then after selecting that policy, click on next, go to review, and create the user.

Let's now close out of there,

- select the user, and we can see the permissions policies that are attached. Because we left the option selected to force a password reset, the user is being granted the permission there. The other policy that's applied is EC2 read only access. So let's now go and see what access this user has to EC2. So, back in the policy simulator, I'm going to choose back up in the top left.
The page might need to be refreshed, and now it's showing Sarah. We can see the policies applied to Sarah. Let's do the same thing again, and in the right hand side choose EC2. I'm going to select all permissions and then run the simulation. So this time we get lots of denies. So we're getting denied for things like assign an IP address or associate a DHCP option, all things that are involving changing, deleting or adding a configuration. If we scroll down quite a way, we should find some allowed permissions.

So here we go. For allow permissions, we can see things like describe addresses, describe bundle tasks, describe carrier gateways, et cetera. So anything that's just about viewing information.

So that's the policy simulator. It's very useful, especially when you have quite complex policies applied to users and you want to be able to view the results here rather than actually logging in as those users and testing the results. Its a really great tool for simulating the effects of the policies that you apply to your principals in AWS.