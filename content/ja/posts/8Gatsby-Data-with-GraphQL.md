---
title: "8. Gatsby Data with GraphQL"
description: "The Great Gatsby Bootcamp"
publishDate: "2020-08-20"
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

<iframe width="560" height="315" src="https://www.youtube.com/embed/8t0vNu2fCCM?start=5303" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Welcome back to `The Great Gatsby Bootcamp`.
In this video, we're going to turn our attention towards getting dynamic data into our Gatsby sites using Gatsby's `GraphQL` API.
Now, if you've never used `GraphQL` before, that's perfectly fine.
Will only be using a little bit of `GraphQL` with Gatsby, and we'll go over the basics as we use them.
So right now everything is shown in the browser is something that's only showing up because it's typed directly inside of the `JSX` for a `React component`.
All of the `<nav>` items, the site title, every bit of text showing on the screen.
Now, obviously, that's fine as we're getting started.
But as we do want to create more complex, dynamic sites, this approach is no longer going to scale.
As an example, let's say we were gonna introduce the blog to our Gatsby site without using anything new without using the `GraphQL` API.
Creating a blog posts would require you to add a new page to the pages directory for every single post, and he would end up with a lot of duplicate code, and you would end up writing your blog posts right inside of the `JSX` for the component, which is never ideal.
That's not an easy way to get your thoughts down on paper and organized when you have to manually maintain the `html` structure along the way.
The other downside is that you also have to update the blog posts page.
So your posts showed up here.
You would have to manually copy `titles` and `excerpts` all over to this page to create a list of all your posts so well, it's possible it's not ideal.
And it's not something we're even going to attempt instead will focus on getting data via the `GraphQL` API that Gatsby provides.
Now, the best way to visualize this is actually on the home page of the Gatsby site.
That's over at `gatsby.js.orgs` If I scroll down just a little bit, there's a section called `How Gatsby Works?` Now there's a chance this visualization changes over time, but I think this is a pretty great visualization for what's happening here.
Everything we're working with so far sits below this line of right here.
So, yes, we're using Gatsby and we're working with `html`, CSS and `React`, and we're also getting a version of our site up and running.
Now we're not deploying it to production.
We're running it in development, but it's the same idea, and we'll get to the deploy stage a little bit later in the bootcamp, the only thing we haven't touched on is what's up above the data sources for your Gatsby site.
So where does your data come from? When it's not typed directly inside of a `React component`? It could come from a CMS like `Contentful` or `Wordpress`.
It could come from files on the filesystem in the form of markdown blog posts.
It could come from any third party data source, such as a custom API you've created.
So this is what makes Gatsby really powerful.
We can pull in all of this data using Gatsby's `GraphQL` API, allowing us to create what is still a static site.
But that static site gets generated with dynamic data from third party data sources.
Now we will progress to more complex data sources like CMS is and markdown files, but we're going to start wit`<h1>` of the easiest built in ways we can set up dynamic data in our Gatsby sites and that is via what's known as site meta data.
It's nothing more than an object on their We can put key value pairs for whatever we'd like.
As an example, the site title, maybe the Twitter profile name and the author of the site, anything like that that would want to be able to easily adjust across the entire site.
Now to get that done, all we need to do is go into `Visiual Studio Code` and make a change to that `gatsby.config` file we've created.
So for the moment, I'm going to close all open editors and we're gonna open up.
Just be `gatsby.config` file, and we're gonna add another property onto this object just alongside of plugins.
And in this case, I'll call this `sitemetedata`, and the name here is important.
It needs to be exact.
Otherwise, Gatsby is not going to be able to find it.
Let's get started by setting up a title property for these site title.
I'm going to call mine something like `full stack bootcamp`.
Perfect.
You can choose whatever title you'd like for your own site.
Let's also set up one more property on `sitemetedata`.
I'm going to set up an author property, which I can use throughout the site.
And right here the value for that will just be `Andrew Mead`.
So there we go.
We have two pieces of data, and will ADM or onto `sitemetedata` later in the video.
For now, though, let's figure out how we can actually query this using the `GraphQL` API that Gatsby provides.
Once we've pulled these values into our components will focus on adding more and more data.
Now, let's actually fetch this data.
Using Gatsby is `GraphQL` API.
And to start, we're gonna head over to the browser opening new tab, and we're gonna pull up a your URL that's only available when our site is running in development mode right here.
That is, localhost on port `:8000` like we had before.
Then it's `/___GraphQL` So that's triple underscore `GraphQL`.
This is gonna pull up a tool called `GraphQL`, which is an in browser IDE for exploring a `GraphQL` API.
So if you've ever worked with a `restAPI` before, maybe you've used tools like postman or insomnia.
This is the same idea just for a `GraphQL` API.
So we type are query over here in the left hand side, we click that play button, it runs the query, and we get our data over here on the right hand side so we can use this to mess around with all of the data.
We have access to figuring out exactly what we need and where it lives.
Once we have our query and we're getting back the data we want, we can move that query into a `React component` to actually set things up in the Gatsby site for now, we're going to start by using graphic.
You well, to mess around with the basics of `GraphQL` once we know how to fetch the title and the author will actually bring that into a `React component` to wire that data up dynamically.
If you haven't worked with `GraphQL` API before, one of the great things about them is that they're self documenting.
`GraphQL` uses an explicit schema and tools like `GraphQL` can show you that schema letting you know exactly what data you have access to and how you can get it.
So for us, let's crack open this docs panel on the right hand side.
Now, in `GraphQL`, there are three main operations we can perform queries and mutations and subscriptions.
When it comes to `GraphQL` inside of Gatsby, we just use queries to fetch the data from those external sources.
So right here, let's go ahead and click on the query, and we can see a list of all of the queries we have access to.
There are quite a few, and this list is actually going to change as we move through the class.
Later on, they'll be new queries for fetching markdown pages or for fetching content from a CMS.
For now, the one query we're going to focus on is near the bottom of the list, and it's just called site.
So I'm going to click on site.
We can see a few different things about these site query.
I convey view the arguments we can provide.
We're not going to provide any, and I convey you the type definition, which is what we want.
So when we grab site, what do we get access to? Well, If I click that we get access to all of these fields, I have quite a few different fields.
The one that we're interested in is called site metedata.
No, if I click on site metedata, I can see that is of the following type.
I click on that and I can see what fields I have access to `title` and `author`.
The two things we defined over insight metedata over here.
So let's go ahead and actually run a query to fetch this data.
Now I know we click through a lot of screens, but once we see the query in action, it will be a lot easier to figure out what's going on.
So Step one is removing the comments over there and starting by defining our query.
We do this by listing out query.
Then we open and close a set of `{}`.
And inside of here we can perform which ever of those queries we wanted to in this case, we decided we wanted to use site.
So I set up site opening and closing a pair of `{}`, and in here we can list out everything from site we want access to for us it was `sitemetedata`.
Now this alone is not going to work.
We can't just grab everything from `sitemetedata`.
We have to be explicit, grabbing just the fields were actually going to use.
So we set up another pair of `{}` and I list out what I want access to in this case title and we can see we're even getting a little auto completion.
I can always use that to populate the final value.
And there we go our very first `GraphQL` operation.
We are performing a query called Site on site were grabbing site meta data on `sitemetedata` were grabbing `title` , and if I click that play button to run it, what do I get over here? I get my data back.
I can see full stack bootcamp showing up now.
One thing you'll notice about the response is that the structure of the response is dictated by the structure of the query.
Here we have site, `sitemetedata` and `title`.
Here we have site, site, metedata and title.
So we get back exactly what we put in.
Though the fields we requested are obviously populated with the correct values.
So Now that we've seen a basic query, let's go ahead and run in this exact same query from a `React component` so we can fetch dynamic data into our site.
We're going to focus on grabbing the site title like we're doing here, but we're actually going to populate it as the value that shows up in the header up above now for us, that means we need to make a change to the header component.
So right here, let's crack that open.
This data right here is gonna end up becoming dynamic.
And to get started, we have to grab two new things from The Gatsby library alongside of Link.
The first thing we're going to grab is called `GraphQL`.
And the second thing we're going to grab is called Use Capital `S` `Static`, Capital `Q` `Query`.
Using these two things will be able to perform a `GraphQL` query getting access to the data.
Then we'll be able to inject the data right in the `JSX` down below.
So let's do it.
Let's start by creating a variable called data to store.
The data were fetching from the `GraphQL` API.
Then we're going to call that `useStaticQueary` function.
This is going to allow us to query our `GraphQL` API.
Now we're going to call it as a function, and inside of there were going to provide a tag `template literal`.
So right here we're using a template stringfy.
But just before the template string were using `GraphQL`, which is a function So this is a sin tax called a tag `template literal`.
Essentially, it allows this stringfy to be processed by that function, and in this case, it's going to convert our string `GraphQL` query over to something that can actually be used a complex abstract state tree with all sorts of object properties and stuff that we just don't need to worry about.
So for us, what we type in this string is exactly character for character.
What we were typing over in `GraphQL`.
So it's a query in there were using the `siteQuery`.
I'm asking for these `sitemetedata`, and on that I want the `title`.
Now we're done.
We have access to that data and we can go ahead and use it in the link down below, or wherever else we might want to use that data.
So for us, I'm going to remove `Andrew Meat` in the `<h1>` in my header, and we're going to set up some `{}` so we can inject the value.
The value is on `data.site.sitemetedata` and it is `title` now.
If we save the program, we can actually pull our site up.
And what do we see? I see `full stack bootcamp` showing up in the header, which is fantastic.
We were able to create a `React component` that fetched data from Gatsby's `GraphQL` API to come up with something that's dynamic.
Now what's cool is that as that data changes, the site will also change.
So over here I'm going to alter that `title`, adding an exclamation mark on to the end.
I'll save things head over to the browser and I can see that change is already in place.
So this is one way we can access some dynamic data in our Gatsby sites using `sitemetedata`.
This is great for key value pairs like title, author, your email address, social media, your Els and that sort of thing.
So once again, inside of header What did wedo? We worked with used `staticQuery` to perform a query.
We got access to the data and we injected that somewhere in the `JSX`.
Now that we've done this once together, it's gonna be your challenge in the video to do it again on your own.
Just up above, I'm gonna paste in the challenge comments and your goal is to run another `GraphQL` query fetching the other site meta data we have.
So step one.
Use `GraphQL` in the browser to fetch the `author`, making sure you get the correct value back.
Once you know how to fetch the `author`, update the footer component to display the dynamic author value instead of these static one.
So right now, `Andrew Mead`, that's hard coated in the footer component.
I want this value to come from the `sitemetedata` instead.
Once you have that in place, you're gonna test your work.
So actually make sure that you can see the name show up.
And when you change the name in the `gatsby.config` file, you should see it change in the browser as well.
So take some time to knock that out.
Pause the video.
Test your work.
And when you're done, come back and click `play` how that go? Let's get to it with step number one.
So over here in the browser, we're gonna use `GraphQL` to fetch the `author`.
So once again, that lives on `sitemetedata` alongside of `title`.
So right here, instead of accessing `title`, I'll access `author`.
I'll run the `query`, and I can see that value showing up.
So this is what I need to run from the footer component.
Let's go ahead and get that done over in `Visiual Studio Code`.
I'm going to crack open the footer component, and we're gonna import those two things we need from Gatsby right here.
That was a graphic.
You well, and `useStaticQuery` grabbing both of them from the Gatsby `npm` library exactly like we were doing over here.
From there, we can actually use these in the footer `const data = ` I'm going to call `useStaticQuery`.
I'm gonna use `GraphQL` with a template string, and we're going to provide our `query` the `query` is using `site` from there were grabbing `sitemetedata` and on `sitemetedata`.
All I want access to is the `author`.
Now we should have access to the `author`, and I can use it down below.
So I'm going to remove these static `author` and swap it out with a dynamic value.
That would be `data.site.sitemetedata.author`, and we're done.
Now that we have this in place, let's test our work.
I'm going to save the footer component in the header component.
I'm going to remove those challenge comments and save that file to and hopefully I see `Andrew Mead` in the Footer right over here.
I do.
Now let's actually change that value in `gatsby.config` just to make sure it's showing up.
So I'll swap this out with something else like the `author`, save the file head over to the site, and that's what showing up in the Footer.
So now we have two dynamic pieces of data in the site, and we figured out how to use Gatsby's `GraphQL` API, which is a great step in the right direction.
All I'm gonna do to wrap up is revert that change back to a value that makes sense, and we're done in the next video What I want to do is take just a couple of minutes to show you an alternative to `GraphQL` that you can use with Gatsby.
In my opinion, it's a lot easier to work with and comes with a nicer user interface.
I'm excited to get to that, so let's jump right in to the next one.
