+++
date = "2017-04-18T10:40:56-05:00"
draft = false
title = "Serverless Architecture"
image = "/img/thereisnocloud-chriswatterston.jpg"

+++

<div class="row">
    <div class="col-md-5">
        <img class="img-responsive img-rounded" src="/img/thereisnocloud-chriswatterston.jpg">
        <span class="attribution">'There Is No Cloud' by Chris Watterston (<a target="_blank" href="https://www.chriswatterston.com/">www.chriswatterston.com</a>) - Used with permission.</span>
    </div>
    <div class="col-md-7">
        <h1>Tyler Explains... Serverless Architecture</h1>
    </div>
</div>
<div class="row">
    <h3>Why Am I Explaining Things?</h3>

    <p>In my experience from company to company, I've found significant numbers of people (developers up to mid-level managers) who haven't had the time in their careers to follow the riot of new ideas, terms, and principles in the software world. I'm starting a chain of posts as a glossary of sorts, to clear the air on some of these topics that I think are important. My intent is for these to be as digestable as possible for people who are curious, but may not be ready to necessarily dive in.</p>

    <h3>So What <i>Is</i> Serverless Architecture?</h3>

    <p>Serverless architecture is a term arising from the more advanced cloud services that AWS and Azure have developed. Originally, these services took the leap of removing your VM hosting needs offsite and allowing you to focus on more systems and software, without worrying about hardware needs. </p>

    <p>Now, cloud providers have taken an additional step and abstracted away the systems management portion as well, leaving you to focus solely on the application. No web application is truly serverless, there is still definitely a virtual machine running your web app. The “serverless” term is just referring to the fact that you no longer control the hardware, operating system, webserver, or anything else beyond your application. </p>

    <h3>What Should I Watch Out For?</h3>

    <p>For people just entering the cloud space after working in the local server paradigm for so long, this can be a rough transition. When a server is abstracted, not only are many things inaccessible to you, but some things become unsafe or unusable by your application itself. For example, files on disk become a risky business once you’ve transitioned to a serverless model. Applications shouldn’t be allowed to write log files or temp files, they shouldn’t be able to open or close network ports, they shouldn’t be able to access the system registry or anything else OS related. I say “shouldn’t” because they can often still totally do those things - but you’re running the huge risk of your service provider changing something and blowing your application up. </p>

    <p>Beyond changes to your application, the way your teams work will also have to change. Inspecting local log or config files is no longer (easily) possible - diagnostics must now be done via specialized tools. It’s also not (easily) possible to install programs or dependencies, as there is no shell or UI access, which means SDKs, libraries, runtimes, etc must be packaged and distributed as part of your application itself. Serverless architecture also brings new challenges the team needs to learn to tackle. Security paradigms and networking in particular can change substantially. </p>

    <h3>What Can I Get Out Of This?</h3>

    <p>So why yield all this control? Why hide things from ourselves? First, as with many practices that feel painful in software development, it’s really steering us towards better design practices and the pain will gradually give way to convenience. Moving to a serverless architecture will drive toward making fewer assumptions of the underlying system, and splitting components into smaller units. Things we know we should be doing anyway, serverless infrastructure forces us to do. Second, going serverless removes the obvious overhead work of VM maintenance. This not only includes patching, upgrades, power management, etc, but the simple act of expanding the server count or size as your business scales up. Third, once your team and your application become accustomed to the new model, many tasks become simpler, such as deployments. And finally, once your infrastructure has been abstracted, it can be recorded, maintained, and versioned as code or configuration files - a larger topic for another post. </p>

    <p>So can you get started? Fortunately, it probably doesn’t need to be an all-or-nothing transition. Even moving applications onto cloud VMs can be a big leap forward, and allows you to begin leveraging “serverless” infrastructure for everything surrounding it, such as firewalls, DNS, AD authentication, databases, etc. When it comes to the server itself, you’ll need to spend some time redesigning anything that used to interact directly with the underlying system, before you can make it “serverless”. And lastly, it’s important to discuss with your team how your workflow will look in the future - how are we going to perform deployments? How do we troubleshoot problems? </p>

    <p>Finally, I’ll leave you with a little table that will hopefully clarify some of the terms thrown around in the Azure and AWS ecosystems, as they can daunting for newcomers. This list is by no means extensive, and there are of course many subtle differences between the product offerings. </p>
    <table>
        <thead>
            <tr>
                <th>Azure Term</th>
                <th>AWS Term</th>
                <th>What is it?</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>Azure VMs</td>
                <td>EC2 (Elastic Compute Cloud)</td>
                <td>Virtual machines</td>
            </tr>
            <tr>
                <td>Storage Accounts</td>
                <td>S3 (Simple Storage Service)</td>
                <td>Super flexible disk drives</td>
            </tr>
            <tr>
                <td>Azure AD, IAM</td>
                <td>IAM (Identity Access Management)</td>
                <td>User and permissions management for your infrastructure</td>
            </tr>
            <tr>
                <td>Azure DB</td>
                <td>RDS (Relational Database Service)</td>
                <td>“Serverless” databases</td>
            </tr>
            <tr>
                <td>Azure App Service</td>
                <td>Elastic Beanstalk</td>
                <td>“Serverless” web applications</td>
            </tr>
            <tr>
                <td>Azure Logic App</td>
                <td>Lambda</td>
                <td>Small, simple functions that are run on time-based or external triggers.</td>
            </tr>
        </tbody>
    </table>
</div>

<!-- Footer -->
<footer>
    <div class="row">
        <div class="col-md-12">
            <p class="attribution">
                Copyright Chris Watterston. All rights reserved -- Resale, distribution, intension to gain profit, or usage in or out of context of the artwork 'There Is No Cloud', in any format, is forbidden without written agreement by Chris Watterston.
            </p>
        </div>
    </div>
</footer>