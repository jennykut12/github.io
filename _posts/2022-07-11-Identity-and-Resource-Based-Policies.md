---
layout: post
title: Possible Exam Questions
subtitle: explore the authentication options in AWS and Multi-Factor Authentication
categories: Markdown
tags: [Markdown, journaling, blog, AWS, IAM,IAMuser, IAMuseraccount]
---

## Identity Based Policies and Resource Based Policies.

### Identity Based Policies.

Remember that these are Jason based permissions, policy documents that control the actions and identity and performance. They're applied to an identity, and they control the actions that the identity can perform on resources and under what specific conditions. So let's say we have a user account, we might have a group and then we have a role. These are all different places that you can apply an identity based policy. Now there are a few ways that you can attach identity based policies.

Firstly, we have something called an inline policy. Inline policies have a one to one relationship with the user, the group or the role. So you create an inline policy for a specific user group or role. You can't share them, you can't use them across other roles. If you delete that user, for example, you'll delete the policy along with it.

We then have what are called managed policies. Manage policies can be either AWS managed or customer managed. As the name suggests, AWS managed are created and managed by AWS and customer managed are created and managed by you. So you can't modify an IWC manage policy. But you can use those policies in your account so we can attach a manage policy to multiple entities so we can attach the policy to a user, a group and a role at the same time if we want to and then known as stand-alone policies for that reason, because you can attach them to multiple identities in your account.

![datacamp certification](/assets/images/Identity%20Based%20Policies.pdf)

Next, we have resource based policies, so these are the JSON policy documents that you attach to a resource such as an S3 bucket or a Dynamo DB table, for example. And there are several different services to which you can attach a resource based policy.So let's say we've got an S3 bucket and we've got Paul on the left hand side. Here are user accounts, and Paul wants to place an object in the buckets. So in this case, we could apply a permissions policy to the the bucket itself. So a resource based policy. And in that policy, we can define the principle. So if we look at how this policy is written, it's a bit different to the policies that are applied to identity based policies. In this case, you get the principle.

So we have the effect allow the principle, which is the R.N of the user accounts, and then we have the action, which is as free star. So in this case, this user is allowed to perform any free API action and we then have a resource in this case, the origin of the specific bucket so he can perform any action, but only on this specific bucket.

The resource based policy will grant the specified principle the permission to perform actions on the resource. So in this case, the user is then able to perform the free puts object API action. It's also possible to attach a resource based policy to an iron roll. So remember, with I am, we have a trust policy and a permissions policy that we apply to the role.

Now, a trust policy is also an example of a resource based policy, whereas the permissions policy is an example of an identity based policy.

![datacamp certification](/assets/images/Resourse%20Based%20Policies.pdf)
