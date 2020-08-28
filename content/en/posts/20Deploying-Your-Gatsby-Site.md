---
title: "20. Deploying Your Gatsby Site"
description: "The Great Gatsby Bootcamp"
shorttitle: ""
publishDate: "2020-08-19"
series:
- The Great Gatsby Bootcamp
tags: 
- Transcription
- Tutorial
- Youtube
categories: 
- Gatsby.js
image: 
draft: false
hideToc: false
enableToc: true
enableTocContent: false
copyright: "All rights reserved"
---

<div style="position: relative; padding-bottom: 56.25%;">
  <iframe 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=15938"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## Transcription text

We've got a site and now it's time to get it live.
And that's exactly what we're gonna do in this one.
Now the first thing we need to do is to get everything up on a github Repo.
We're gonna end up using nettle if I to deploy our static site and nettle if I can pull the assets right from github.
So that's a really good solution for us over here in the editor.
We can close all open editors and we can collapse all expanded directories.
And the only thing we're gonna do before we make a commit is make sure that our environment variable file does not get committed.
This can contain sensitive information.
And it's something that we don't want to commit as part of the repo.
Because right here, this is not stuff we want to expose to just anybody.
So to do that, what we're gonna do is actually rename this file right here.
We're just going to call it.e NV.
Originally, I thought I would create multiple environment files, but that's not the case.
We just have this one locally, and we can see that by default.
It's already ignored, based off of the getting nor file that comes with Gatsby.
The only other change we need to make sense.
We rename that file is over here in the developed script right here.e n v.development just becomes.e N V.
Now we're ready to commit our changes and push them up to get Hub.
Let's get started by actually creating a github repo for our new project.
So right here, I'll go over to github.com.
I'm going to create a new repository, and we're going to set this up.
I'll call it Gatsby bootcamp, and I'll leave this one as private down below.
We can create it without customizing any of the other settings.
And once we have it created, we're going to take our existing repository and pushed that up from the command line.
So let's take this first command, which adds the correct remote, and we'll head over to the terminal now by default.
All of your Gatsby projects already have a git repository created.
So we need to do is make sure that our changes and all of our new files actually become part of the repository.
I will use get status to take a look at the status of the repo right here we can see we have a bunch of untracked files that we're gonna want to track and up above.
We also have some changes to existing ones.
I'll use get add.to move all of those to the staging area and then get commit to create a commit right here Final Gatsby site.
And now that we have this in place, we can push the code up to github.
I'll start by pasting in that first command which sets up the correct remote that all we have to do is used.
Get push you.
We're going to push to origin and we're gonna push up the master branch.
And once this command is done, will be ready to connect our github Repo to the Natl.
If I hosting service to host our Gatsby site.
All right, I'm seeing everything right here.
So let's pull up a new tab.
It is nettle.
If i.com This is a great hosting service for static sites.
It's an increasingly popular choice when working with Gatsby because there is direct integration so it's super easy to manage, and once again, everything we're doing here is completely free.
There is no credit card required for any of this.
Let's take a quick moment to create an account and I'll work through this process with you.
Just so we're seeing the exact same stuff, I'm going to sign up for a new account.
Now, once we sign up, we do have to confirm our email before we can deploy our site.
So I'm going to take a quick moment to pull that up off screen, then we'll continue on with the set up.
All right? When I click that verification link, this is exactly where I was brought.
There's a little quick start guide with some information about how we can get started.
We're gonna go ahead and close that down and work through this process together.
What we want is right here.
New site from get and we're going to connect with our github account.
Now, this is going to require us to give nettle.
If I permissions to read some of our data and right here we can see we have the option to pick select repositories or all of our repositories.
We could go ahead and just pick one so I could crack that open and I could find the new one.
I created Gatsby bootcamp, giving it limited access to just that and down below.
We can see we have access to all of the repository features, and we're going to install that as part of our github account.
Now, once that is installed will actually be able to select our repository from a list.
And once we have that, it's going to set up the build options down below.
We have the owner That is me.
This is the name automatically generated for me.
We have the branch to deploy.
I'm just going to deploy Master.
The only branch we have and down below.
We have other things like the build command and this is correct.
We want to leave this and this in place.
The public directory is where the static site is going.
to live when the Gatsby build, command is executed.
Now we also want to go to show advanced right here.
We can set up environment variables for our environment and we do need to do that.
We have those environment variables locally.
And those were the only things getting our site working right here.
We don't have to worry about setting up `GraphQL playground`  as the `GraphQL` API is not even available in production.
But we do want to set up the space i d.
So let's start with that.
I'll grab the variable name and I'm also going to grab the value pasting both in.
We're gonna add the other variable as well.
For the access token, I'll set up the name, Then I'll go ahead and grab the value, making sure not to grab the equals sign.
And now we're actually ready.
So it's gonna grab.
The code is going to run the build command and serve up that public directory, and it's going to make sure it can actually get our `Contentful` assets.
Since we have these values defined from here, all we need to do is click Deploy Site.
This is gonna work through the deployment process, and especially for the first time, this can take a little longer, contain upwards of maybe 60 seconds to get everything up and running.
So what I'm going to do is just cut the video.
So when the deployment is complete.
The deployment is now finished and we have our You are l up above.
Let's go ahead and open that up in a brand new tab.
And what do I see? We have our site live on the web right here.
All of our pages are working, and we also have our `Contentful` data.
I have our first post in our second post.
Now, when it comes to deploying a new version of your site, you have a few different options.
So let's go ahead and make some changes and get a new version up.
We're going to change.
Not just the site code were also going to change some data in `Contentful` so we can see what that process looks like to.
And I actually want to start with a change to the `Contentful` data.
Let's go ahead and just alter the title of one of our blog posts right here.
We have `Contentful`.
I'm gonna go ahead and change a `Contentful` blog posts over to something else.
My new post and I am going to publish those changes.
Now this alone is not enough to have the new content showing up.
Remember, this is a static site.
So when Nell if I first ran the build command, that's when it fetched the data and populated things.
If I refresh, we're never going to see that new content.
So if I just change the content and I want to show that new content on the site, we can indeed get that done right over here.
What we're going to do is go to the deploys tab for our project.
And right here we have a few different options.
What we want to do is trigger a new deploy.
We're going to clear cash and deploy site.
So this is going to go through the process of re creating our site once again.
And here it's just bringing us over to the deploy logs.
Once this is done, will be able to see our new `Contentful` data, and this is actually a nice thing.
We could make changes to our data, and once we're ready, we explicitly deployed a new version of our site to view that new data.
Now let's go ahead and go back to the overview page for our site.
And once that deployment is done, actually, let's stick on the deploys page.
We can see it's building down.
Below old were going to do is refresh the site once again.
So I'm going to cut the video to win.
The new build is done.
Alright, Right here I can see my new build has been published and if we head over to the site so we need to do is give things a refresh and we see the new data showing up.
So that's the workflow for changing just the content.
We update `Contentful` we trigger a new deploy manually and then we see our new changes.
Now let's actually make a change to some code for the site.
So I'm gonna close all open editors and we're just going to change something on the home page.
So I'll go to source pages `index.js` right here.
I'm just going to remove this paragraph where I link over to the contact page as I already have that link in the navigation.
With that change in place, all we need to do is commit our changes and push them up to github.
So right here, get status and we can see the Onley changed file is the one that we changed.
Then we're going to run, get commit once again providing our commit message cleanup home page links.
Once the commit is in place, we have to use get push to push.
Our code changes up to github.
And when this is done, we're going to see that over in nettle.
If I a new deploy is triggered, so by default it is going to deploy changes from master.
It's going to generate a new build, and it's going to publish it, so we'll see that start in just a couple of seconds here.
There's no need to manually trigger a bell when we're making code changes.
We really only need to manually trigger a build when working with nettle.
If I I'll give the page a quick refresh just to see if anything new has been pulled in.
And here we have it.
We have a new build in progress, so this is starting up, and once it's done, we should be able to see our changes over on the site.
So I'm going to take a quick moment to cut the video to win.
This build is finished, all right, that deploy has finished, and now we should be able to see our changes on the site.
Here I have the home page.
I'll give things a refresh end.
My paragraph is gone.
So that's as easy as it gets working with nettle if I allows us to deploy our site, managing our `Contentful` data and managing changes to our code.
And now you know how to work with both of those now Natl if I can do so much more than we're gonna have time to talk about in this video, if we go to overview, you can easily set up a custom domain and enable https and up above.
There are a ton of great features for managing your site.
For now, though, that's all we need to get Gatsby up and running.
That's where we're going to stop for this video, and that's also where we're going to stop for the bootcamp.
We've gone through the process of creating, customizing and deploying our very First Gatsby project.
We can now continue to work with Gatsby and build off of this to create anything we might want to build with `React` that is it for `The Great Gatsby Bootcamp`.
If you want to check out other content I've created.
I have more videos right here on YouTube.
And I also teach premium classes on you, Timmy, covering topics like `JavaScript`, `React` `node.js` and `GraphQL`.
I'll include links to all of that and more in the description down below.
Once again, I'm Andrew Meat from meade.io and I hope to see you in another video sometime soon.

## Info

{{< alert theme="danger" >}} 
本書き起こしはgithubレポジトリで管理しています。
**If you find a mistake, please let me know via Github issues.** 
[Issues on Github](https://github.com/newt0/gatsbybootcamp-transcription/issues)
{{< /alert >}}

{{< alert theme="info" >}}
Andreaw Mead's Udemy Courses are  {{< color "#FF0000" >}}90%OFF{{< /color >}} now!
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Freact-2nd-edition%2F" target="_blank" rel="nofollow">The Complete React Developer Course (w/ Hooks and Redux)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fgraphql-bootcamp%2F" target="_blank" rel="nofollow">The Modern GraphQL Bootcamp (with Node.js and Apollo)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fmodern-javascript%2F" target="_blank" rel="nofollow">The Modern JavaScript Bootcamp</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fthe-complete-nodejs-developer-course-2%2F" target="_blank" rel="nofollow">The Complete Node.js Developer Course (3rd Edition)</a>
{{< /alert >}}

