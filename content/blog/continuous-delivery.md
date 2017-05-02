+++
date = "2017-05-02T09:11:33-05:00"
title = "Tyler Explains... Continuous Delivery"
slug = "continuous delivery"
image = "/img/blog/continuous-delivery/cd-1920.jpeg"

+++

If there’s a buzzword more popularized and misunderstood than Agility or DevOps, it’s probably Continuous Delivery. As with many complex ideas, it’s difficult to understand at a glance, easy to make guesses about, and takes awhile before misconceptions become evident. My hope is that this post will allow some people to get a better understanding before vaulting into the unknown. <!--more-->

Let’s start by clearing up some terms:

- *Continuous Integration* (CI) refers to the process of automatically incorporating changes from any and all team members into a central source of truth, and ensuring some level of baseline quality.
- *Continuous Deployment* goes a step further and automatically deploys the updated product to running environments, perhaps the production environment itself.
- *Continuous Delivery* (CD) involves both and more. It’s the process of making changes, validating quality, presenting to the client/customer, and gathering feedback for the next change - at very high frequencies.

In true agile fashion, they can be tackled one at a time for incremental benefit, while the sum of the parts creates the most value. Next I’ll go front-to-back and explain exactly what each piece provides. 

### Continuous Integration
First, the purpose of a CI system is to provide a constant, reliable window into the health of the product. One of the most basic ways this is done is simply having another machine, not a developer’s workstation, that can successfully build the system - guarding against compile errors. Hosted CI providers, such as VSTS or Travis will even dynamically provision fresh environments for each build, which ensures that there is no reliance on the state of the machine.

The CI is also the first line of defense against merge conflicts. While source control systems are excellent at forcing team members to handle direct line conflicts, sometimes automerged code produces something that doesn’t even compile. Teams will also run their unit tests in the CI build, providing an excellent first gauge on whether the product behaves as expected. And lastly, if desired, many CI systems will perform some form of analysis of the code - evaluating style conventions, common red flag patterns (such as null parameters), comment standards, code coverage, duplicated code scanning, etc. 

It’s important when putting the effort into building a CI system that the team is ready to adopt it as the standard of quality. The attitude of the team should be “if the CI is red, our product is broken”. If the CI is simply perceived as convenient tool, or annoying side-show, or “the tech lead’s thing”, the CI will get neglected. Tests or code analysis checks will get disabled because “we know it works and we just need to get it out there”. Or the CI will just sadly sit at red for months at a time while everyone works around it. The CI should be considered the conceptual holy gates of code, and everyone should regard a failed CI build as a valuable catch or rallying cry, not a hassle.

Combined, these features make the CI server a mascot of the product and the team - something they can rally around, protect, and celebrate. Quality can be (roughly) measured, and the team can gain satisfaction from watching it rise over time. Simple bugs or issues are caught sooner, and thus resolved more quickly.

### Continuous Deployment
Continuous Deployment extends the bar on how product quality is gauged. The key assumption is, software that hasn’t made it to a user is a sunk investment that hasn’t begun returning. The sooner we can carry something from “it probably works” (i.e. the CI signed off on it) to “it’s making money” (a production environment), the better. Continuous deployment achieves this by speeding up the process, making sure it happens as soon as the CI has a new successful build, and making it far more reliable and resilient than humans copy-pasting. Continuous deployment also provides quick quality feedback on the most basic and important aspect of your software - *does it run*. Combined with a few automated integration or UI tests, this can be a very powerful second level of quality certification and convenience. 

### Continuous Delivery
Finally, Continuous Delivery (CD) exposes the ability to be more deliberate in how features are launched. This can include things like 0-downtime deployments, feature toggled deployments, A-B testing, dynamically scaling infrastructure, etc. When your automation gets advanced enough, technology stops getting in the way of business decisions. This is the real meaning of CD. It can seem confusing at first since there’s nothing concrete that can be pointed to…. A CI server is definitely a CI server, and a continuous deployment tool is definitely a continuous deployment tool. Continuous Delivery isn’t a single tool or process; it’s a governing set of tools and processes that fulfill the idea of using automation to gather data, make decisions, and conduct operations with little or no effort.

### The Real World
So what does CD look like in practice? Here’s a quick diagram showing an example of how CD is normally done at my current employer, Centare:

![Centare CD Diagram](/img/blog/continuous-delivery/centare_cd_pipe.png)

And here’s how I do it with my Moodboard project:

![Moodboard CD Diagram](/img/blog/continuous-delivery/personal_cd_pipe.png)

In both diagrams, the top half roughly encompasses the process of continuous integration - constantly aggregating code changes into a common build system that certifies quality. The bottom half roughly encompasses continuous deployment - smoothly, quickly, and reliably moving code changes to the customer. And the entire system creates a continuous delivery pipeline, where changes are fast, accurate to what the customer needs, and rigorously validated. 
