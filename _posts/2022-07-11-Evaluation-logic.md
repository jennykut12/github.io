---
layout: post
title: Evaluation Logic
subtitle: explore the authentication options in AWS and Multi-Factor Authentication
categories: Markdown
tags: [Markdown, journaling, blog, AWS, IAM,IAMuser, IAMuseraccount]
---


##  Evaluation Logic


There is a bit of complexity in how IAM evaluates whether you're allowed or denied from performing any particular action or operation.
Now, this is straight from AWS and this is their logical flow of how we go through the process of determining whether you are allowed or denied from doing something.

![datacamp certification](/assets/images/Evaluation.jpg)

Before we actually go through this, there's going to be a bit more background knowledge that you need. So let's firstly start with what are the steps for authorizing requests to AWS.

![datacamp certification](/assets/images/Stepfor%20authorising%20request.jpg)

And we've touched on this in a little bit of detail already. So we have the various methods on the left of how we might authenticate AWS. And in this example, we're trying to connect to an S3 bucket.

1. We first need to authenticate. So AWS will authenticate the principal that makes the request. In this case, it's a user.

2. The request context must then be formulated and processed. Now, this includes several attributes.

3. So we've got the actions. These are the actions or operations the principal wants to perform. The resources in this case, we're trying to perform those actions against an S3 bucket. The principal in this case, it's a user, it could be a role, federated user, or application. Some environment data. So it could be things like the IP address or the SSL status of the connection. And we then have resource data, which is related to the resource, the S3 bucket that's being requested.

4. Then identity-based policies and any resource-based policies must also be evaluated. And then the action in this case, the GetObject action will be allowed or denied. In this case it's allowed.

So that's the steps for authorizing a request.

### The several types of policy. 

![datacamp certification](/assets/images/Types%20of%20policy.jpg)

We're familiar already with quite a few of these policies. So identity-based policies that we attach to users, groups, or roles, resource based policies that we can attach to things like DynamoDB tables, S3 buckets, VPC endpoints.
And then we have IAM permissions boundary, which we've also been over. Then there's AWS Organizations, Service Control Policies and we haven't covered these yet. But understand that AWS Organizations is a way that you can centrally manage multiple AWS accounts and you can apply policies to those accounts which determine the maximum available permissions and those are called Service Control Policies, SCPs.
Lastly, we have session policies which are used with the AssumeRole API actions.

### So what is the process for evaluating policies?

Well, let's look at when we have a combination of identity-based policies and resource-based policies.

There are four allow permissions.

The effective permissions will be all available permissions here because it will be a combination of the identity-based policy allows and the resource-based policy allows, there's no denies being shown here. So the principal will get access to all four permissions. We then got an identity-based policy with a permissions boundary.
The effective permissions will be where there's that overlap between the two.
So you need to have both the identity-based policy giving you an allow, giving you the privileges for that particular action or operation. But you also need to be allowed through the permissions boundary as well.
Lastly, we have the identity-based policy with an Organizations SCP. This is very similar to a permissions boundary, but it's applied at the account level. And in this case, again, the effective permissions are going to be where the overlap is between the identity-based policies and the organizations SCP.
With both the permissions boundary and the organizations SCP, you need to be allowedin each of those policies as well as have the permissions through an identity-based policy as well.

### The determination rules.

![datacamp certification](/assets/images/Determination%20roles.jpg)

So by default, all requests are implicitly denied except for the root user who always has unrestricted access. But for everyone else, there's an implicit denial.And that means if you don't have and allow permission allowing you to do something, then you're just denied by default.
An explicit allow in identity-based or resource-based policies will override that default. If there's a permissions boundary, organizations SCP or session policy, that can override the allow with an implicit deny and think back to the last slide and you'll understand how that works.

And then lastly, an explicit deny in any policy will always override any allows.So let's have a look at the logical flow.

![datacamp certification](/assets/images/Evaluation.jpg)

Starting up in the top left hand side here, the decision starts with a deny, as always that's the implicit deny. So now we have to evaluate all the policies. If there's an explicit deny, then straight away it's all over. The deny decision is final. If there are no denies, then it checks whether the principal's account is a member of an organization an AWS Organization with a Service Control Policy. If not, then just carry on. If yes, it needs to check for an allow. Then it checks whether the requested resource has a resource-based policy. If it doesn't, then it moves on. If it does, again, it just checks for an allow. And if there is one, then the final decision is allow in this case.

Next stop, the permissions boundaries have to be checked. Is there an allow? If not, then the final decision is deny. And if there isn't a permissions boundary, then just move on and check for a session policy. Again, if there an allow, then it moves on. If there's a session policy present without an allow, then the deny takes effect.
The final step of the decision here is then to check for identity-based policies.
Now remember, if you had a resource-based policy and it had an allow, then the allow already took effect. So with everything else, with the permissions boundary, with the session policy, it needs to check whether there's an identity-based policy. So if there isn't one, then there's a deny because there is no privilege for any actions. If there is a policy, then it will check it and again, deny if there's no allow. That's the implicit deny taking place and then allow if there is an actual explicit statement that allows you that particular action or operation.

So that's the evaluation logic.