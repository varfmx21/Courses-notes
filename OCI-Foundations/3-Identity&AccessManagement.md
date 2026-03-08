# 3. Identity and Access Management
## 3.1 Introduction
### Transcript
Welcome to this lesson on OCI Identity and Access Management. In this particular lesson, we are going to look at very high level overview of OCI IAM. IAM stands for Identity and Access Management service. It's also sometimes referred to as fine-grained access control or role-based access control service.

There are two key aspects to this service. The first one is called authentication, or also referred to as AuthN. And the second aspect is referred to as authorization or also referred to as AuthZ. Authentication has to deal with identity or who someone is, while authorization has to deal with permission or what someone is allowed to do.

So basically what the service ensures is making sure that a person is who they claim to be. And as far as authorization is concerned, what the service does is it allows a user to be assigned one or more pre-determined roles, and each roles comes with a set of permissions. And that's basically what is shown on the screen here for authorization, as what kind of permissions do you have.

Now, there are various concepts which are part of this service or various features which are part of this service, starting with identity domains, principles, groups, dynamic groups, compartments, et cetera. And in subsequent lessons, we are going to cover these in more details.

Now I just want to talk about one such feature here, which is identity domains. Now identity domains is basically, as you see on the picture here, it's a container for your users and groups. So think about this as a construct which represents a user population in OCI and the associated configurations and security settings.

So how does this work in practice? Well, what we do first is we create an identity domain, and then we create users and groups within that identity domain. And then we write policies against those groups, and policies are scoped to a tenancy, an account, or a compartment.

And of course, the resources are available within a compartment. And again, compartment is kind of a logical isolation for resources. So this is how the whole service works. The part which is in a box here is identity domain. And users and the groups, authentication is done by common mechanisms like username and password, and policies is basically where you provide this role-based access control.

So you put these groups in one of the pre-determined roles, and then you assign some permissions against those roles. So this is how the service works in a nutshell. Now one thing which you would see in that previous slide was about these resources.

Now anything you create in the Cloud, all these objects, whether it's a block storage, it's a compute instance, it's a file storage, it's a database, these are all resources. And if these things are resources, there has to be a unique identifier for these resources, is how are you going to operate on these resources?

So what OCI does is it provides its own assigned identifier, which is called Oracle Cloud ID, OCID. You don't have to provide this. We do this automatically for all the resources. And the syntax is as shown on the screen here. So it starts with ocid1, there's a resource type, there is a realm, there is a region, and there is a unique ID here.

So what this means is ocid1 is just the type of resource, realm is basically set of regions that share the same characteristics. So there's a commercial realm, there is a government realm, et cetera. Resource type is kind of the type of the resource. It's a compute instance or it's a block storage device or et cetera.

And then region is basically the region code here. It used to be a three-character code, now it's much longer string. And then there is a unique ID here, which is unique to the resource you create. So what are some of the examples? Well, your account also has an OCID, so you see that here tenancy and you can see the syntax here starting with ocid1.

Now, of course, account is across multiple regions. So you don't have a region identifier here. Its realm is ocid1, and then there is the unique identifier. In case of block volume, you see the region, because block volume is specific to a particular region. So you see the region key here, and then the unique identifier.

So this is hopefully a quick kind of a couple of examples to show you how OCIDs work. If you are working on a management console, you're not going to interact with the OCIDs. But if you are using the CLI or the SDK, you would be using these OCIDs. And remember, Oracle generates these unique identifiers. You don't have to do anything as far as these OCIDs are concerned.

Hopefully this was a quick lesson on OCI IAM. Remember the two key aspects for the service are authentication, basically which deals with identity or who someone is or who someone claims to be, and authorization, which has to do with permissions or what someone is allowed to do.

And in subsequent lessons, we are going to dive deeper into some other concepts like compartments and identity domains and authentication and authorization. I hope you found this lesson useful. Thanks for your time.
## 3.2 Compartments
### Transcript
Welcome to this lesson on OCI Compartments. Compartments are a unique feature within OCI. And these are really powerful, so let's explore.

So what is a compartment? When you open an account in OCI, you get a tenancy. That's another fancy name for an account. And we also give you a Root Compartment. So think of Root Compartment as this logical construct where you can keep all of your cloud resources. And then what you could do is, you could create your own individual compartments, like you see here.

There is a network compartment. There's a storage compartment. And the idea is, you create these for isolation and controlling access. And you could keep a collection of related resources in specific compartments. So the network resource has-- a network compartment has network resources, and storage compartment has storage resources.

Now, keep in mind, Root Compartment, as I said earlier, can hold all of the cloud resources. So it can be sort of a kitchen sink. You could put everything in there. But the best practice is to create dedicated compartments to isolate resources. You will see why. Let me just explain.

So first thing is, each resource you create belongs to a single compartment. So you create a virtual machine, for example. It goes to Compartment A. It cannot go to Compartment B. Again, you have to move it from Compartment A, or delete, and recreate in Compartment B. Keep in mind, each resource belongs to a single compartment.

The reason why you want to compartmentalize your resources is exactly shown on this slide. Why you use compartments in the first place is for controlling access and isolation. So the way you do that is, you have the resources, let's say in this case a block storage, kept in Compartment A. You don't want those to be used by everyone. You want those to be used only by the compute admins and storage admins.

So you create those admins as users and groups, write these policies, and they can access these resources in this compartment. So it's very important. Do not put all of your resources in the Root Compartment. Create resource-specific compartments, or whichever way you want to divide your tenancies, and put resources accordingly.

Now, how do resources interact if they are in different compartments? Do they all have to be in the same compartment? Absolutely not. As you can see here, resources in one compartment can interact with the resource in another compartment. Here, the Virtual Cloud Network is-- the compute instance uses the Virtual Cloud Network, but these are in two different compartments. So this is absolutely supported. And it keeps your design much cleaner.

Keep in mind that resources can also be moved from one compartment to another. So in this example, Compartment A had a virtual machine. We can move that from Compartment A to Compartment B. Another concept, which is very important to grasp is the compartments are global constructs, like everything in identity. So resources from multiple regions can be in the same compartment. So when you go to Phoenix, you see this compartment existing. You go to Ashburn, you see the same compartment.

Now, you can write policies to prevent users from accessing resources in a specific region. You could do that. But keep in mind, all of the compartments you create are global, and they are available in every region you have access to. Compartments can also be nested. So you have up to six levels nesting provided by compartments. You would do this again because this can mimic your current design, whether it's your organizational design or whether it's your ID hierarchy. You could create nested compartments. It just helps keep your design cleaner.

And then, finally, you could set quotas and budgets on compartments. So you could say that, my particular compartment, you cannot create a bare metal machine. Or you cannot create an Exadata resource. So you could control it like that. And then you could also create budgets on compartments. So you could say that, if the usage in a particular compartment goes beyond $1,000, you'd get flagged, and you get notified. So you could do that.

So that's Compartments for you. It's a very unique feature within OCI. We believe it helps keep your tenancies much better organized. And it really supports your current ID hierarchy and design. Thanks for watching.
## 3.3 Demo: Compartments and Identity Domains
### Transcript
Welcome to this demo on compartments and identity domains. So as you recall from the theory lesson, compartments are nothing but logical containers for your resources. And identity domains you can think of them as containers for your users, groups, and security configuration.

So in this particular demo, we are going to create a compartment named sandbox, and then we are going to create an identity domain call it sandbox domain. And we will put some users as part of that identity domain. So let's get started.

As you can see here, I am logged in to my OCI console. And to bring up identity compartments and identity domains, I'll click on the navigation menu and click on Identity and Security. And you will see all the Identity Services listed here. And some of the security services are listed here as well.

So to bring up compartments, I'll click on Compartments here. And from this place, I can go ahead and create a compartment. So I can see here that I have a root compartment, which is also my tenancy.

And within that compartment, I have a couple of other compartments which exist and development. And there is another compartment which is used for our platform services. So you can see here all the compartments which are available in my account are subcompartments for the account, for the root compartment itself.

So you can see here it says two subcompartments because this compartment, the account has two other compartments existing. And also this development compartment also has a subcompartment. So you can see here.

So you can nest these compartments up to six levels deep. So that's what you're seeing here. So let's go ahead and create a new compartment here. We'll call this compartment sandbox.

And right here, I have an option to create this as a security zone. We actually discussed security zone later in the course. So I'll skip it for now. And you can click this is all it takes can click Create Compartment, and now you will see that a compartment called sandbox gets created. It will take a couple of seconds to do it. So let me just refresh the page.

And now you can see that the sandbox compartment is created. And if I click on the sandbox compartment, I can see that I can rename it. I have certain other actions I can take. And I can create a child compartment here up to six levels deep. I can nest compartments.

So the thing which I really want to see is if I go to governance and administration and bring up tenancy management, I can actually look at what resources exist within my tenancy. So right here I can see in my root account, my tenancy, I have a few resources which are existing. I have Cloud Guard enabled here and so on and so forth.

You can see there are some users. There is a Virtual Cloud Network, et cetera, which exist. If I click on the sandbox compartment, you can see that there are no resources which are found in this compartment because we just created this compartment.

So this is a nice way to see what resources exist in your compartment. You can-- because as you are creating resources you might not be keeping track on where these resources exist. Using the Tenancy Explorer, you can actually figure out which resources exist as part of your compartments. So let's-- having created compartment, let's go and create an identity domain.

So similar to compartments, identity domains exist within the identity menu here. And you can access them by clicking on domains. So if you click on domains, this will bring up the menu to create an identity domain. You can see that there is a default domain, which exists, which is the current domain.

So to creating-- to create a domain it's pretty straightforward process. So click on the domain-- create domain button there. And let's provide a name for this domain. So we'll say this is the sandbox domain.

And right here I can see domain types. So I can choose a free option or I have other SKUs which I can get into this as a foundational course. So we're not getting into a lot of details there.

And I can create an administrative user for this domain. I'm going to skip this for now. I'm not going to do that.

And then it asks where do I want to create this domain. I can actually create this domain in the root, or I could actually create it in the sandbox compartment we created. So I'll go ahead and create this in the root compartment.

And I'll click Create here. And I have to choose the SKU here. I'll say it's a free SKU. And I'll create the domain.

And that's how simple it is to create an identity domain. And remember, again, similar to compartments, identity domains are containers for your users, groups, and security configuration. So the way it is used is let's say I have a sandbox compartment where I'm using this compartment for testing purposes. So I could have a select Setup of users and groups, which are involved with this testing, and I could keep them in this sandbox domain identity domain.

And once I no longer use them, I can delete all these user subgroups. It's a nice way to segregate your users, groups, and security configuration. So let me just refresh this page and see if the identity domain is created.

And as you can see here, took a few seconds and the sandbox domain is created. So if I click here, you can see in my default domain, I have six users and four groups. But in the sandbox domain, if I click here, I can see that there are no users.

So in the next demo, we are going to create a user here, and also going to create a group here. And as you can see here, it's just more than users and groups. It's also all your security configurations like MFA dynamic groups, et cetera.

So this was a quick demo on how to create compartments and create identity domain. I hope you found this demo useful. Thanks for watching.
## 3.4 AuthN and AuthZ
### Transcript
Welcome back to this lesson on authentication and authorization. Before we get into more specific details, let's look at what is a principal. A principal is an IAM entity that is allowed to interact with OCI resources. There are two kinds of principals primarily in OCI. One is your users. Think about people who are logging on to your console or using your CLI or SDKs. Users, human beings, actually using your cloud resources.

And then the resources themselves can be principals. So a good example of a resource principal is an instance principal, which is actually an instance which becomes a principal, which means that it can make API calls against other OCI services like storage.

Also, when we talk about principals, we have groups. And groups are basically collection of users who have the same type of access requirements to resources. So you can have a storage admin group where you could group all the human beings who are storage administrators and so on and so forth.

So let's look at some of the details, starting with authentication. Authentication is sometimes also referred to as AuthN. And as we recap from the previous lesson, authentication is basically figuring out are you who you say you are? And the easiest way to understand this is all of us deal with this on an everyday basis. When you go to a website and you provide your username and password to access some of the content, you are being authenticated.

There are other ways to do authentication. The one common for cloud is API signing keys. So when you are making API calls, whether you're using the SDK or the CLI, you would use the API signing keys which use a public-private key pair to sign these APIs calls and authenticate these API calls.

It uses an RSA key pair, as you can see here, with both a public key and a private key. There is also a third way to do authentication. And that's based on authentication tokens. And these are Oracle-generated token strings. And the idea here is you can authenticate third-party APIs which don't support OCI authentication model.

So in this example, we are showing an ADW, calling an ADW, Autonomous Data Warehouse API call, where we are using these auth tokens. Till your identity is being followed, these auth tokens can be used for this purpose.

Now, let us very quickly look at authorization. So authorization deals with permissions and figuring out what permissions do you have. In OCI, authorization is done through what we call as IAM policies. And policies, think about these as human-readable statements to define granular permissions. So you have a couple of examples here. And the policy syntax is always something similar. In the next slide, I'll talk a little bit more about what this statement means.

Remember policies can be attached to a compartment or they could be attached to a tenancy. If they are attached to a tenancy, it applies to everything within that tenancy. If it's applied to a compartment, it applies to only the resources within that compartment.

So how is AuthZ done in OCI? We talked about policies. What does the syntax look like? As you can see here, the syntax is always-- always you have to start with an allow. Everything is denied by default. So you don't really have to write a deny statement. So you say allow, group name, group is basically a collection of users. So you cannot write a policy on individual users. You always operate at a group level.

To do something, there's a verb. On some resources, there is a resource type. And there is a location. Location can be a tenancy, location can be a compartment. And you can make these policies really complex with adding conditions. And again, foundations course. So we are not getting into a lot of these complex topics. But you could really write complex policies.

So just to give you an idea of what the verbs might look like. There are four levels of verb. There is a manage, there is a use, there is a read, and there is a inspect. So manage basically means you can manage all resources. Use basically means you can read, but you could not do things like update and delete, and so on and so forth. And you can read more on the documentation.

Resource type basically can be all resources, meaning everything in your account. Or it could be compute resources, database resources, whatnot, all the resources you have. Now, you could operate at a family level, which is meaning all the entities within that resource family, or you could even go very granular. So you could say that in compute, I just want somebody to operate on the instances, but not work on the instance images. So you could actually do that.

So this is how you would write a policy. There are some exceptions to this rule. There are policies you would write for services and such. But again, it is a foundations course. So we're not getting into those advanced details. This is typically how you would do authorization in OCI.

To wrap up, we looked at how you do authentication in OCI. The three mechanisms-- username/passwords, API signing keys, authentication tokens. And then we looked at how you do authorization in OCI through policies. Policies are really powerful. They are very easy to understand human readable. But at the same time, they give you a lot of advanced capabilities to implement really fine-grained access control. I hope you found this lesson useful. Thanks for watching.
## 3.5 Demo: AuthN and AuthZ
### Transcript
Welcome to this demo on OCI authentication and authorization. As you recall from the theory lesson, authentication is all about your users, who your users are, and what they are requesting. And authorization is all about permissions. Once your users are authenticated, what level of access they have, what permissions do they have to which resources? So let's look at both of these in action.

I am in the OCI console here. And in the previous demo, we had created an identity domain. So let's leverage that. So click on Identity and Security. And right here, I can see Compartments and Domains. So we created a domain, identity domain in the previous demo called Sandbox Domain.

So if I hover over here, I can see there are no users here. So let's go ahead and create a user. So I'll click on Sandbox Domain. Click on Users. And you can see there is no user which exists right now.

So let's create a user, and let's give a very creative name-- OCI Admin. The username could be what we choose, or it could be an email ID if we choose an email ID here. And we also need to specify an email ID here so the user can access their passwords, reset their passwords, et cetera. So we'll provide an email ID here.

And I'm not going to add the user to any of the groups here. So let me just go ahead and create this user. Now, in OCI, the policies are defined at a group level, not for individual users. So let's go ahead and actually create a group as well.

So if I click groups here, you can see there are two groups which are existing by default. Let's go ahead and create another group here. So we'll call this group OCI Admin group. And as you recall from the theory lesson, it's a good practice, best practice to create separate administrators and not use the root user for day-to-day operations.

So I create this OCI Admin group. And here, I can specify which user should be part of this group. So ociadmin is fine. I'll click Create.

And now, what I have done is I have created a user, and I've created a group to which the user belongs. But right now, first, what I need to do now is to activate the user so the user has access to the system. That's authentication. And then we need to write some policies so the user can perform some actions in OCI. So let's go ahead and log into my email account, and I'll activate the user.

As you can see here, I got an email asking me to activate my account. So I'll click here, and it'll prompt me to-- first thing you see here it's prompting, it's prompting that identity domain is sandbox dash domain. It's no longer giving this as the default domain. So you see the difference there?

And now, it's asking me to set up a password for my username. So I'll go ahead and choose a password which actually will work here. And I'll reset my password here.

And then it says, continue to sign in. So I can sign in here. But instead of doing that, let me actually open an incognito window and actually sign in through the incognito window.

So I'll access the URL for OCI console. And it will ask me to enter my tenancy name. And ocifoundations, that is the tenancy name, so click Next. And then it will ask me to provide username and password. This is how you would access OCI console.

So right now, I get a choice of identity domain, whether it's default or sandbox domain. So I'll pick sandbox domain because that's where my user belongs. And click Next.

And it will ask me to provide a username and a password. So I'll provide ociadmin. That's my username. And I'll provide the password, which I just reset.

And now, I'm logged in as ociadmin to the OCI console. So if I click on the right-hand side, you can see my profile. You can see here, right now, my identity domain is sandbox domain, and my username is ociadmin. So this is authentication.

Now, I can authenticate to the system, meaning I have access to the system. So I can see all the services. I can see the console, et cetera.

But can I do anything? Actually not because I really don't have any authorization. No permissions have been given to me. So if I click here and I see my compartment, you can see that I'll get an error message saying, I do not have authorization to perform this request.

And it's not just for storage buckets. If I go to Compute, I'll see that I cannot do anything on Compute because I have no authorization here, and so on and so forth, right? It's basically, I have just created a user and put that user in a group. And I have logged into the system, so that's authentication. But beyond that, there is nothing else which I have done because authorization is still to be done.

So to do that, what we'll do is we'll go back to the OCI console. And here, I'm logged in as my tenancy administrator. And you see, if I go back out of domains, the policies are defined actually outside the domain. So I'll click on Policies, and we'll create a policy for OCI Admin group.

So I'll click on Create Policy here. And it's rather straightforward to create policies. So I'll say this is-- what is this for? OCI admins.

And right here, there is a Policy Builder which I can use. I'll show you in a second. Or I could actually manually write policies here. And these are human-readable formats and not complex JSON, et cetera. But it's actually quite simple to use this Policy Builder.

So because we want to create a storage bucket, I'll click a policy use case as storage management. And right here, it gives me all sorts of policies I can write for storage. So I'm interested in object storage, so I'll click on that.

And right below that, it's asking me, what groups, what identity domains, et cetera, I want to leverage? So my identity domain which I want to use is sandbox domain. And the group which I have is the OCI Admin group. And it also gives me a location, which is whether it's for a compartment or it's for a tenancy.

So I'll choose the sandbox compartment. And that's all it takes. And now you can see it spits out the policy statements. It says, allow group, sandbox domain, OCI Admin group to manage buckets and manage objects in this compartment. So outside that compartment, I still don't have access. But within that compartment, I should be able to create buckets and upload objects.

So I'll go ahead and create these policies. Quite straightforward to create these policies. And if I come back here, now, in the same login as ociadmin here, if I go back to if I go to compute and refresh the page here, you will see that I still don't have access to compute resources. So I cannot create any compute resource because we didn't write to policy for compute. So it'll kind of error out as is shown here.

But if I go to storage now and bring up object storage, I should be able to create an object storage bucket, not in the root compartment, but in the sandbox compartment. So if I click here, first thing is I see sandbox compartment here. And I can click Create Bucket.

The default name is fine. Click Create. And here, you can see that my bucket can be created.

But if I go to the root compartment and I try to create a bucket here, you will see that the bucket it says it already exists or you're not authorized to create it. It's of course not authorized to create because our policy is only operating at the sandbox compartment level.

So this is exactly what authorization does where we write specific policies giving access to a set of users to specific resources, whether it's in the compartment or in the entire tenancy. I hope you found this demo useful. Thanks for your time.
## 3.6 Tenancy Setup
### Transcript
Welcome back. In this particular lesson, let's quickly look at how you can set up your tenancy or your account. Well, so until now, we saw that there is a tenancy administrator. This is the person who creates an account and is kind of responsible for day to day operations of this account.

But a best practice is to not have tenancy administrator do kind of day to day operations, but rather have somebody who is an admin for your particular account. And this can be a set of users, not just one person. And you can group all of them under this, like a group such as OCI admin here. And then you write policies for this particular group, and let them operate on their own specific compartments.

So let me talk about some of these things which are shown in the graphic here. So the first thing here, kind of a best practice is what I just said, don't use the tenancy administrator account for day to day operations. You should not be doing that.

The second best practice is to create dedicated compartments to isolate resources as is shown here. So there's a sandbox compartment. It could be a compartment for a production, or development, or a business unit, or it could be a region based compartment, or whichever way you want to isolate your resources.

These compartments are available across all regions. So when I say region based, meaning you could say North America uses this compartment, and Europe uses this compartment, et cetera. So you could isolate your resources in kind of a geographically based on where your users are. But you should have individual compartments. You should not put everything under the root compartment.

And then the third best practice is to enforce the use of multi-factor authentication. And the idea with multi-factor authentication, it's a method for authentication that requires the use of more than one factor to verify a user's identity. So it would be something like a password, something you know, and a device, something you have.

So these are the three best practices you should definitely enforce as you set up your tenancy. So what are the policies you need to write if you have a setup like this where there's a tenancy administrator, but you are not using this account for day to day operations?

So what are some of the policies you need to give to these OCI administrators, so, in fact, they could be a proxy for the tenancy admin, and you could swap out the tenancy admin with the OCI admin?

There are some policies which you absolutely need to provide. So the first thing is you should provide access to manage all resources. I'm showing these policies in tenancy here, but you could scope them to a compartment as well. So you could say compartment ABC. You could have that name here. But you should provide access for the OCI admins to manage all resources, like a tenancy admin would do.

And then there are resource types for the IM service itself, which you need to use in policies so that the admins which are available in the OCI admin groups can use OCI Identity resource types. So for example, in IM, you don't have any aggregate resource type. So you have to use them individually.

So there is a resource type called domains. There's a resource type called users, groups, dynamic groups, policies, compartments. And there are some more identity providers, network sources, tag, defaults, tag namespaces, et cetera. I'm not listing to a whole set of resource types here.

But you have to write these policies, otherwise, OCI admins cannot create users. They cannot create groups. They cannot create policies. So if you have to give them access to manage policies, being able to create users, groups, et cetera, you should actually write these policies.

So this is the least amount of policies you need to write for the OCI admins in order for them to be kind of day to day admins for your tenancy. So hopefully, this is a quick lesson on how you can set up your tenancy following these best practices. I hope you found this lesson useful. Thanks for your time.