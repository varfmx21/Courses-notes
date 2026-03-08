# 8. Security
## 8.1 Pricing
### Transcript
Welcome to this module on governance and administration. As part of this module, the first lesson we are going to look at is around pricing. Now pricing is a complex topic. A lot of pricing with a lot of Cloud providers is complex. Oracle's pricing is simple. It's transparent. And it's lower pricing than our competitors. So let's look at some of these in this particular lesson.

The first thing is what kind of pricing models do we support? So we definitely support pay as you go pricing where you charge only for the resources you consume. There is no upfront commitment. There is no minimum service period. And the usage is metered for. This is Pay as you go for most of the resources.

But for some resources like our managed serverless platform called Functions, it takes you to the next level. So you have this concept of consumption based pricing, where you are charged only when you consume the resource which is different than pay as you go, because you have to pay for the VMs, even though you might not be using them or they might be running idle.

So we support pay as you go and consumption based pricing and all sorts of models in between. And then the second model we support is called Annual Universal Credits. And the idea here is you commit to an annual pool of funds. In return because of this commitment, you get significant savings. But the thing is you have to use these credits within 12 months.

If you end up with more resource usage, then you pay for them on a pay as you go basis. And the discounts here vary based on the size of the deal and term of the deal. There's also something called Monthly Universal Credit. And you should read more about that on our website.

And the last option is bring your own licenses. This is for customers who are running on-premises licenses if they want to reuse that in the Cloud. Why would you do it? It reduces your overall cost, and you could reuse those licenses in the Cloud.

Now let's look at factors that impact pricing. The first factor which impacts pricing is the size of the resource. So bigger resources are going to cost you more. That's just natural, because the service pricing is based on consumption and the type of resource you use. So the bigger resources will cost you more.

Data transfer is a big part of the pricing. And we'll talk about some of that on the next slide. The resource type you choose also determines your pricing. So virtual machines versus bare metal have a different price points versus serverless has a different price point. If you bring in your own licenses, they have a completely different pricing model. So keep all that in mind.

One thing to keep in mind with OCI is we have the same pricing across the world. So all the OCI regions have the same pricing. This is very different than the typical traditional Cloud model where the pricing is very local. So you pay a different place in the US. You pay a different place outside the US in different countries where the Cloud regions operate.

Let's look at the data transfer cost and why it is so important. Well, the thing is data transfer can be up to one fourth of your bill or even higher. And the reason is your applications are always communicating, whether they are communicating to the end users or they are communicating internally.

So to give an example, if you look at the OCI Region 1, we have 2 availability domains. You have an application which might be running in a high availability mode across two availability domains. Now in case of OCI, you don't really pay for any data transfer happening between these two ADs as you can see on the graphic here. In case of some other Cloud providers, they charge you for data transfer between ADs.

In a way, this is penalizing customers for achieving high availability, which is one of the goals of Cloud computing. So it doesn't make a lot of sense that way. Also with Oracle, incoming traffic is free as it's the industry standard. But outgoing traffic is 10 times lower than some of the other Cloud providers. And you heard me right. It's 10 times lower. It's not 10% lower. It's nearly 10 times lower.

So you save a lot of money, particularly if you have applications which have high data transfer usage. You end up saving significantly by using OCI. And that's it. We wanted to keep it very high level, very simple-- the three pricing models we support.

And then the highlight of our pricing is it's simple. It's transparent. And some of the elements like data transfer cost you 10 times lower. So it's definitely a lot cheaper than some of the traditional Cloud pricing out there. Thanks for watching.
## 8.2 Cost Management
### Transcript
Welcome to this lesson on Cost Management. Let's look at what tools OCI provides to you to manage your costs. So the first option you have are these things called OCI Budgets. You can use budgets to track costs in your tenancy. After creating a budget for a compartment, you can set up alerts that will notify you if a budget is forecast to be exceeded or if spending surpasses a certain amount.

As you can see here on the screen, we have two kinds of budgets set, one for $1,000, one for $100. And you could look at the forecast and other things and get notified if you are close to exceeding that or if you have exceeded it. It's an important way for you to manage your cost and be notified if the cost surpasses your forecast or your plans.

The second tool, which is available to you, is around cost analysis. And this, as the name indicates, you could analyze your cost after you have spent it, but it's a nice way to look at your past cost and then make changes for the future. If there are elements you want to change, this is a great way to do that.

There are also usage reports. Today, currently the usage reports get downloaded in form of these CSV files, and these are generated daily. And they show usage data for each resource in your tenancy. The CSV files are stored in an object storage bucket that is accessible using a cross-tenancy policy, so you could look across not just your tenancy, you could look across multiple tenancies if there are multiple tenancies being used.

Now, a couple of other tools in this area include service limits, the tool to set your limits, quota, and usage. So as with any Cloud, we limit how many resources you can run in a traditional tenancy to prevent things like fraud and misuse. But you can always-- for legitimate cases, you can always change your limits for a particular service, and there is a way to look at your current limits and change it. And you could submit a support request to do that, but that tool provides you at a glance what kind of limits you have broken down by things like your availability domain so you can dive deeper and get more details here.

Then, finally, as we talked about, compartments are these logical entities, which you can use to isolate resources and have better access to these resources, so if you are using these compartments, you have ability to set up compartment quotas. And the way it works is you have these different policies you could write, where you could set the maximum number of Cloud resources that can be used for a compartment. So you could say that, in this particular compartment, you can only use, let's say, 10 virtual machines. You could unset that and go back to the default service limits, or you could zero it out. So as an example, here, you could say, this particular compartment should not have any Exadata resources. And you could do that to prevent misuse and also save on your cost.

So recapping, that's your Cost Management-- many tools available, including budget, including usage reports, cost analysis, ability to set quotas, ability to increase your service limits, and many more. You should check out our documentation to learn more about all the ways you could manage your cost in OCI. I hope you found this lesson useful. Thank you for watching.
## 8.3 Demo: Cost Management
### Transcript
Welcome to this demo on OCI Cost Management tools. Let's get started. I am logged on to my OCI Console and to bring up cost management tools, click on navigation menu and click on Billing and Cost Management. And as you can see here, all the cost management tools are listed here.

Well, we have separate tools for cost management. The first tool is called Cost Analysis. And Cost Analysis can help you visualize and track your spending based on your preferred parameters. And then you see those other tools here, Cost and Usage Reports.

Cost Reports basically give you a breakdown of your invoice line items at resource level granularity. This allows you to make better informed cloud spending decisions. And Usage Reports provide a detailed breakdown of resources in OCI for audit or invoice reconciliation. And there is also a tool called Budgets where you can track spending for your compartments and your tenancy. So we'll look into that.

So let's first look at Cost Analysis. And the first thing you see here is it's giving me a cost breakdown by service, and this is the current month. And if I scroll down, I can see that for this particular month I have spent $23. And if I scroll down, I can see a granular breakdown, day-by-day breakdown for different services. So as you can see here, majority of the cost is for compute and then there is some cost for database. So it's very clean, very kind of detailed report where I can see how much cost I have been incurring this month.

Now if I want to change the filter and go all the way to January 2023, I can actually do that. And now I can see cost over the last four or five months. So you can see that the cost has been around $380 for the last five months, and I can still see a breakdown of cost by services, so block storage, compute, database, et cetera. Majority of the cost is still coming from compute and database resources.

Now if I want to change this view and I want to see which are the regions where I have been incurring these costs, so I can apply that filter. And now you can see that the majority of the cost as shown by these blue bars are coming from Ashburn, and then there is some cost which is coming from Phoenix. So again, we provide several grouping dimensions so you can use those. And there are several filters as well, so you can filter based on compartments, tags, et cetera.

Let me show you a couple of these in action. So if I go back to just for the month of May, I can apply the report and I can see the dimensions. I see the same report we were seeing earlier. Now I can change the view to go from region to a compartment name. And I can go, let's say level 2.

And if I click Apply now, you can see the cost breakdown. But I can see now the cost breakdown by compartments. And the first thing which appears here is networking compartment has been incurring a majority of the costs. So I knew that I was spending $23 this month. Now I know that out of that $23, $21 is coming from that networking compartment. And I have seen earlier that the majority of this cost is coming from the Ashburn region.

But if I want to select that filter, I can provide the filter here. And now I can see the cost breakdown by region. So if I scroll down here, I can see that the networking compartment had around $6 of cost and so on and so forth. Ashburn region had around $8 of that cost. So majority of the cost is not coming from Ashburn. It's coming from some other region.

And I can come here, I can remove that filter, I can put a filter again, and I can select Phoenix. And I think Phoenix is where I'm incurring the majority of the cost. So if I scroll down, now I can see that, yes, that's correct. $15 of that is coming from Phoenix, and most of the cost is still from the networking compartment.

So I went from $23 cost to figuring out two compartments are incurring that, majority coming from networking, around $21. And then I figured out of that $23, $7 was from Ashburn and then the remaining was from Phoenix. So it's very handy, very easy to do this kind of analysis and it's very powerful.

Now I can also go and do this analysis based on the tags. So if I click on Tags here, I have a tag namespace, which is shown here, and I have a tag key. So as soon as this report appears here, we can see that the cost breakdown by the tags. And we can see things like who is incurring those costs. If we have created by, basically that will indicate the person who is creating these costs.

So it's taking some time. Let me just kill the filter there. And refresh this one more time. All right. All right. So I'll go here, and I'll put tags. Something was going on there.

So if I bring up tags now, once this report comes, you can see the cost breakdown by various tags. As this is-- all right. So now you can see that if I hover over these, I can see that all these costs is incurring for the compute instances, and I can see that Sergio is the one who has created these compute instances.

So if I want to drop him a note or something, I could do that. I can also save this as a report, as a new report. So I can click Save As a New Report, and I could say this is my tag-based report and save this. And now this report is saved. And now next time I can come here and I can just bring up this report, and I can see what's going on with the different resources. So very handy tool which definitely you should use.

Now let me quickly show you how to use budgets. Now you can use budgets to track cost in your tenancy. Now once you create a budget, you can also create alerts and alarms for those budgets. So the way you do that is you can set up the budget at a compartment level or you can also do budgets on cost tracking tags.

So let's say you choose compartment. You can provide a name for your budget and you can choose a compartment. You can say this is for the sandbox compartment, what's the day when the budget starts, and you can set budget alert rules, and you can set what is my threshold. And threshold basically says the alert will trigger when the budget reaches either a specified percentage of the total budget or a specified amount. So it could be 90% or you can specify, explicitly specify an amount here.

And you need to provide an email ID and an email message optionally, and that's it. And then you can set up budgets. And as you are using your account, let's say you set up a budget for $100 and the threshold is 90%, at $90 spent it will send you an email saying that your spend is $90. So you can go and check which resources are incurring these costs. So those are the two things I wanted to quickly touch on, cost analysis and budgets. I hope you found this demo useful. Thanks for watching.
## 8.4 Demo: Cloud Advisor
### Transcript
Welcome to this demo on OCI Cloud Advisor. Cloud Advisor is a service that analyzes OCI cloud resources and provide recommendations to maximize cost savings and optimize your tenancies, performance, security, and availability. Let's look at Cloud Advisor in action.

I am logged onto my OCI console. And to bring up Cloud Advisor, click on the navigation menu and click on Governance and Administration. And Cloud Advisor is listed right here. So I'll click on Cloud Advisor, and it will bring up a dashboard which will have four major categories-- cost management, high availability, performance, and security. And we'll look at each of them in a lot more details.

So the first dashboard here is around cost management. And basically, you can read the text here. Cost management provides you recommendations which help you reduce costs by finding and adjusting resources that are underutilized. So we'll look into this in a little bit more detail.

High availability recommendations help you improve system resilience. And again, we'll look into what this entails. And then the dashboards down here are for performance and security. And performance basically helps you improve-- you can read here. Performance recommendations help you improve performance by finding an adjusting resources that are overutilized. So we'll, again, look into what that means.

And here, you can see security. And the Security Dashboard you see is as blank here because Cloud Advisor actually redirects customers to Cloud Guard. And using Cloud Guard, we can look at the security posture management. And you can read here the details on Cloud Guard. So we'll look into each of these in a little bit more detail.

So first, let me click on Cost Management. And you can see this dial here, which says details. And when I click on that, I can see several recommendations, right?

It says delete unattached block volumes because they are incurring costs, and you can see the cost listed here, right? It says delete unattached boot volumes. And there's a cost which is there, right? And says, delete idle compute instances. So there is the cost listed here. And so on and so forth.

And it's quite straightforward to work on each of these recommendations. So for example, if I click on Delete Idle Compute Instance, it just shows me that there is a compute instance running in UK South region which is incurring this cost. So I can click on implement selected, and I can click Implement here.

And what this will do is it will delete this idle compute instance because it's been running and incurring costs. And maybe it's a leftover compute instance which nobody is tracking right now.

Similarly, I can click on Delete Unattached Boot Volumes. And sometimes when you delete your compute instances, you can keep the boot volumes running. So I can see here in Sandbox, there's a boot volume running, again, in UK South.

I click on Implement Selected. And what this will do is it will delete unattached boot volume, this particular one here. So I'll click Delete, and now this will be deleted. So it's that simple to get the recommendations and work on these recommendations.

So if I go back to the main dashboard, it shows me these major recommendations which are incurring costs. The two of those I just kind of-- you can see those six implemented. And a few of those are remaining. So you also get good visibility into how some of these are still open, right?

So down below, you can see another dashboard, which is on performance. And if I click on Details here, you can see what kind of performance parameters or recommendations Cloud Advisor is recommending. So you can see here, it's saying that I need to enable autotuning for block volumes. And autotuning is a feature which we covered in our block volume lesson where using autotuning, you can save some costs.

So I can see here that I have several block volumes where autotuning is not implemented. So I can just click, similar to the previous example, and click implement here. And now, what it would do is in the back end, it would go and implement autotuning for these block volumes.

And the idea is, again, it will save cost, and it will help in the right sizing the performance of those block volumes. So it could do that.

Similarly, if I click on the third dial here on high availability, click on Details, you can see that it'll give me recommendations around things like improve fault tolerance. And if I click on this, basically, it is saying that in these compartments, we are running too many instances in one fault domain, right?

You can see here. Too many instances are clustered in one fault domain. And it can be an issue. And every availability domain has three or fault domains. So I can leverage the other two fault domains, and I can spread my instances across fault domains. So I could actually do that.

And finally, you can see there are recommendations around security. And you see nothing listed here because we redirect customers to another service in OCI called Cloud Guard, which, again, we covered in a lot more details in this course.

And if you see this, basically, Cloud Guard is a service which helps you maintain a very high security posture. And basically, Cloud Guard, what it does is it looks at your whole tenancy or individual compartments, and it can tell you if there are any kind of misconfigurations or any kind of activity which are suspicious. So you can see here, if I click on sandbox, I can see there are lots of activities which are critical, high, medium, ranking.

And if I click on the details, I can see that there are things like public IP address probably should not be there. NSG allows disallowed IP port, et cetera.

So the idea being, again, with the Cloud Advisor that you get these recommendations around saving costs, saving money, improving performance, strengthening system resilience, and improving security. So I hope you found this lesson useful. Thanks for your time.
## 8.5 Tagging
### Transcript
Welcome to this lesson on tagging. Tagging is a very, very important capability within OCI, and you should definitely leverage it. Let's talk more about it. So at the core, what is tagging? Tags are basically these key value pairs, which you could use to better organize your resources.

So as you can see here, this particular instance, I have put two different tags. So there is a tag which is environment with a value of production. And there's another tag which is project and has value of alpha. And I could do multiple tags. You should always check service limits as to how many tags I could put on a particular Cloud object. But in this case, I'm putting two tags here.

And these again, just to recap, are simple key value pairs or name value pairs where the key is the key for the tag, and then the value is the value you want to assign. So the idea here is you are going to run hundreds or thousands of Cloud resources. And as you are creating applications, you're creating this complex architectures, you could tag them. And you could identify your applications, your resources by using these tags.

So that's the first reason why you would use your tags, because your accounts and your resources-- you're going to use many, many resources. And tags is a very easy mechanism to better organize your resources.

The second reason you would use tags would be for cost management. Now imagine all these resources you're tagging, you could pull them up by the tag. And you could find out what is the cost usage for those resources. And that's a very important way to figure out how much your application is consuming.

Remember Cloud is all about pay as you go pricing. And you could pinpoint it down to a particular set of resources as to what kind of cost you are incurring. So second reason why you would use tags are cost management.

You could also do this thing called Tag based access control. So you could control the access based on the tags for the resources, not the users and the groups. So in a way by using tags, it becomes even more powerful, the ability to do write policies based on tags. So those are some of the use cases. And there are many, many more. But those are some of the reasons why you would use tags.

So as we talked about in OCI, there are two kinds of tag. There is free form tags. And there is defined tags. So first let's look at the free form tags. As you can see on the graphic here, there is a key and a value. So for this particular tag, the key is environment. The value is production. It's a very simple key value payer. There's no defined schema. Or there is no kind of access restriction.

Then we have defined tags. And these have more features and control. And the first thing to note here, as you can see on the graphic, is these tags now are contained within this thing called a namespace. So you specify a namespace saying, in this case, it's operations. And then you can put as many tags as you want in those namespaces. So you are defining a schema.

And other thing you could do it also supports policies. So defined tag support policies to allow you to control who can apply your defined tags. So not everybody could just use these defined tags. You could write that in the policy. And the tag namespace is the entity to which you apply this policy. So you could say a particular group of operations admin can only apply this particular tag, because the namespace has operations in that. So you could write a policy against that.

So how does it really look in practice? So as an example here, there is a namespace which is operations. And within, that I'm defining a key value pair. So the key is environment, and the value is production. And you could take it to the next level. So as you can see here, operations is the namespace. Environment is the key. And production is the value.

Now as we talked about, namespace is a container for a set of tags with tag key definitions. Tag key definitions specifies the key like it is here. And you could also specify the type of values allowed. You could say the type is a string. And it allows any value, or it is blank. Or you could set a specific set of values. And when the users come to apply this particular tag, they can only choose from those particular values.

So it is another way for you could first determine who applies the tag by writing the policies. And then you can also specify what kind of values are allowed. So this is really is that defined schema along with policy makes the resources even more better organized.

One thing to keep in mind is tag namespace once you define, cannot be deleted. But you can always retire them, and you don't have to use it. This is more for governance purposes. So whatever namespaces you have, you can keep an audit of the namespaces you had in your account. So that's it.

Tagging-- a very important feature, useful feature in Cloud. And in OCI, we take tagging to the next level using these defined tags. I hope you get to use defined tags. Thank you for watching.
## 8.6 Support Rewards
### Transcript
Hello, and welcome. In this lesson, let us look at Oracle Support Rewards. Oracle Support Rewards is a program that provides additional value to Oracle's on-premises customers who also consume OCI services. So based on their consumption of OCI services, customers can earn Support Rewards that are then applied as a form of payment for their software update licenses and support for Oracle technology programs.

Oracle customers save $0.25 for every dollar spent on OCI, while Oracle ULA-- ULA stands for Unlimited License Agreement-- customers can save $0.33 per dollar spent on OCI. So the idea here is the more customers use OCI, the more the savings are, and eventually, they can decrease the tech license support spend to as low as zero.

So let us look at an Oracle Support Rewards example. Let's say you have a spend on tech support for on-premises licenses and software of $450 per month. So you can see there the old support payment of $450 per month. Now let us say you decide to add some workloads to OCI, which leads to OCI consumption of $1,000 per month.

Hence, if you spend is on the $1,000, then if you are a ULA customer, you would earn $330 as part of the Support Rewards. If you are not a ULA customer-- remember you save $0.25 for every dollar spent on OCI-- you would get $250 as part of the Oracle Support Rewards. So you can see the math on the screen.

Now in the if you're using the leveraging the Oracle Support Rewards program, your new support payment would be $120 instead of $450 if you are a ULA customer. And if you are non-ULA customer, your new support payment will be $200 instead of for $450. So this is, again, a fantastic program to, as you consume more OCI services, you can decrease your on-premises support cost.

And the way the total monthly consumption is calculated, as you can see on the screen, is as follows. So you take the unit net price of the services consumed, and then we multiply that by actual usage of OCI services over a month. And almost all OCI services are included, as you can see here, including Compute Autonomous Database, et cetera, and you can always check the FAQs to see which services are included.

And this is, again, a fantastic way to save cost on your on-premises licenses. So we also make it very seamless and easy to see what your Support Rewards are. And you can redeem your Support Rewards also through the console. So you see this OCI Console here, and you can see this is available under Billing and Cost Management.

And as you can see on the screen here, again, my Support Rewards are shown here, and it also shows how much Support Rewards I have redeemed until now and some of the details you can again look up on documentation on some of these details. So just to summarize, this is a fantastic program to reduce your on-premises support cost as you are using OCI. I hope you found this lesson useful. Thanks for watching.