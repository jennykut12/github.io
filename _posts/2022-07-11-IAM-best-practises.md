---
layout: post
title: IAM Best Practise
subtitle: Read me
categories: Markdown
tags: [Markdown, journaling, blog, AWS, IAM, IAMBestPractise, Exampoints]
---

## Best practices for using the IAM service.

![datacamp certification](/assets/images/Best%20practice.jpg)
![datacamp certification](/assets/images/Best%20practice1.jpg)

Now, really important to know these. Again, this is something that comes up in the exam. So it's a bit of a bullet point list, but it's really important to understand this. So the first thing is that you should lock away your AWS account root user access keys. So you remember I talked about the root user account and how it has so many permissions and you can't restrict them. Now, access keys are those keys that you can use for programmatic access. You should even delete them from that root user account or just make sure that they're very well secured.

Create individual IAM users. So that's what we've done in this section. We created our own user account and now we're logging in as that user account rather than root. Use groups to assign permissions to IAM users. Now you can assign policies directly to users. But remember, we looked at how you can do it through groups. So you'll assign the permissions to the group once and then everyone who gets put in that group gets those permissions. Much better way of doing it. Always grant the least privilege. So don't give people more access rights than they need to do their job. 

Get started using permissions with managed policies. Now, when we were adding a policy to our group earlier on, they were the AWS managed policies. They're predefined for you. Now, if you don't have a lot of experience with writing policies, you can make mistakes. So that's why there's a best practice to get started by using the managed policies. Once you really understand them and you've got more expertise, then create your own.

Use customer managed policies instead of inline policies.This is again talking about not assigning the policies directly to a user, that's known as an inline policy. Instead, create your own custom policies and use those.

Use access levels to review IAM permissions. What this means is that you should regularly audit the permissions that are assigned to all of yourusers and other principles in your account. Just make sure that they only have the permissions they need, that least privilege.

Configure a strong password policy for your users. You can enforce a password policy within IAM and that enables you to make sure that users have complex passwords that are difficult to guess.

Enable MFA. We did that in this section. Multi-Factor Authentication is a great way to add additional security to your account.

Use roles for applications that run on EC2 instances. It's a way of assigning the ability for an EC2 instance to assume a role rather than having access keys hard-coded into the code. This can be a security risk.

Use roles to delegate permissions. Great way to delegate permissions.

And do not share access keys. It's very important not to share them. These give people access to perform whatever permissions are assigned to your user account.

Rotate credentials regularly. So this means make sure you change your passwords, you renew your access keys. So if they do get compromised, then at least we're mitigating the amount of time that they can be used.

Remove unnecessary credentials. So only half the ones you need.

Use policy conditions for extra security. Now, you've already seen a few policy documents and you've got some JSON code in there. Now you can assign something called a condition. And that might say that the policy applies only to users coming from a certain computer IP address, for example. So that's a condition and that's an extra level of security.

You should also monitor activity in your account. Always monitor and try and know what is going on so that if there's any suspicious activity, you can identify it and then act upon it. So those are the AWS IAM best practices.