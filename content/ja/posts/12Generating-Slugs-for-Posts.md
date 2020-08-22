---
title: "12. Generating Slugs for Posts"
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

Now that we have a list of blog posts on the blog page, it's time to dynamically generate pages for each and every post.
So if I want to read this post, I click on the title.
That brings me over to a new page and that new pages dynamically generated using the markdown data from `GraphQL` and a blog post page template, which is nothing more than a `React component`.
And we're going to use that same blog post page template for every single blog post.
Sense as we saw in `GraphQL`, we have a standardized set of data.
I have a title, I have a date, and I have the body content for each and every post.
Now let's head over to `Visiual Studio Code`.
Close all open editors, and I'm just going to crack open a new file where I'm gonna outline what we're going to cover in this video.
The reason I'd like to outline things is that will be spending a little time working with the Internal Gatsby API.
And that can be a confusing topic.
So it's a good idea to have the big picture in mind.
Goal number one is to generate a slug for each post.
So let's say we have a post like Our Gatsby Post that is `gatsby.md`.
That is the markdown file.
What we want to do is generate a slug, which is nothing more than the file's name stored as a `String`, `Gatsby`.
That's going to allow us to set up the URL where someone will be able to view this post.
Now that URL could be whatever we like.
For example, it could be `/gatsby` or something a little more complex, like `/blog/gatsby`.
Either way, though, we need the slug from the file name in order to set up the correct `endpoint` where that particular post should be accessible.
So that's goal one.
Generate a slug for each post.
Goal two is an easy one for us.
We're going to generate the blog post page template.
That's nothing more than a `React component`.
And there's not a lot to say about that for now.
Pretty straight forward.
Next up and the final thing we're gonna do goal number three is to actually combine those two.
So we want to generate a new page for each post.
So in order to generate that new page, we're going to need a template, and we're going to need access to the file and the slug so we can set up the correct URL where someone will be able to view our new dynamically generated page.
So those are the three goals and to get started, what we're going to do is actually create a new file that currently does not exist in our project.
In the root of the project, this file is `gatsby-node.js`.
This is the `gatsby-node` configuration file, which allows us to tap in to a lot of the `Node API` that Gatsby exposes.
This is what we're going to use in order to generate that slug.
And in order to dynamically generate those blog post pages.
Before we start using these internal API, let's check them out over in the Gatsby docs.
So you know where you can learn more.
I'm gonna head over to the Gatsby website.
We're looking for the docs page here.
We need to scroll all the way down in the sidebar and go to API reference.
Once we're there, we're looking for the `Gatsby Node APIs`.
These are all the things we can define in that new file we've created.
And on that page, if we scroll down just a little bit, we get brought to a list of all of the different API we can tap into using that New Gatsby `node` file.
Now, in this video will end up using two of them, and the  first one we're going to use is `onCreateNode`.
This is what's going to allow us to attach some new data onto the individual Node.
And what we're going to do is attach the slug.
So we have access to the slug throughout the entirety of our application.
If you're wondering what a `node` is, remember, it's nothing more than a data structure for storing your Gatsby data.
And we already saw this in place with the `GraphQL` queries that we ran in the last couple of videos.
So right over here we have the `allMarkdownRemark` query.
We grabbed the `node` to grab individual data about the particular markdown `node` here we grabbed the ``frontmatter``, ``html`` and `excerpt`, and there were other fields which we didn't grab but were available.
So that is the individual node.
This API allows us to do something when that `node` is created.
So when a new `markdownNode` is created, all we're going to do is attach the slug field onto it, and that's nothing more than a `String`.
The file name without the `.md` extension.
So right here, we're going to take this code and bring it over into that file.
Now, this file is indeed a `node.js` file.
So right here, what we're going to do is set up `module.exports.onCreateNode`.
So that's how we use this file.
We export functions, and these functions get registered to Gatsby and run when they're supposed to.
In this case, our function runs when a new `node` is created.
Now, over in the docs, we saw we get access to an argument and we can get data structure that to get access to the `node` and to some actions which are destructured down below.
Now we don't need `createNode`, but we do need `createNode` field, so we're going to make sure to grab that as well right here.
Let's this structure this argument, grabbing the `node` and grabbing our actions.
Then, down below, I'll destructure the actions grabbing, `createNodeField` from actions.
And there we go.
We have our little boilerplate version of the function in place.
Now it's time to actually see what this is going to do for us and how we're going to use it to generate the slug field.
First thing I'd like to do is just use `console.log` to print the `node` to the terminal.
So we can see what exactly we get.
Now when we use just this, it's not going to print in a way that's easy to see, So let's pretty print the `node` instead.
With the following here, we're just going to use `JSON.stringfy()` to convert the `node` object over to a formatted string that will make it a lot easier to view things down below.
So right here how do we call `stringfy()` while we pass in the object as the second argument we provide `undefined`.
This is an optional filtering function.
In this case, we want to see everything so we'll leave that off, and the final argument is the number of spaces we want to use when printing it to the terminal in the formatted version.
Here, I'll just use four.
So now we're going to see a pretty printed version of the individual nodes when we restart the server because that's when on `createNode` runs.
So down below, let's shut down the terminal.
I'll use up and enter to restart the server.
And when we restarted, we're going to see our `console.log` call print a bunch of new objects to the terminal, which is exactly what we got.
The first object right here is quite large.
It runs from up above.
It contains about two dozen different properties, and it runs to down below.
Now the only thing we're concerned with about this object is internal, internal itself is an object.
And on there we have a type property.
This is the type for the current `Node`, and in this case, we can see the type is `SitePage`.
`SitePage` is a built in Gatsby type.
This is for new pages on our site and right here we can see this is four `index.js` in the pages directory, and that is our home page.
Now, if we continue to scroll up, we'll see `SitePage` nodes for the other pages we've defined so up above.
We have `SitePage` for contact.
Then we have `SitePage` for blog, followed by `SitePage` for `about`.
Then we have a page that's generated for us.
`SitePage` for Dev `404 page`.
No, don't worry.
You're gonna learn how to create a proper `404` shortly, but past that.
That's where things start to get interesting up above.
We have a new `node` and the internal type is `MarkdownRemark`.
These are the nodes that we actually want to tap into so `onCreateNode` runs for all of the nodes for our Gatsby site.
We don't want to do something for all of the nodes.
I just want to do something for the `MarkdownRemarkNodes`.
I want to take that entire file name.
I want to reduce it to a slug, and I want to add that as a new field onto the `node` so it's easily accessible throughout the rest of our app.
So that's exactly what we're going to do here we have the `node` for the `React` post.
Up above, we have the `node` for the `Great Gatsby Bootcamp`, which also has an internal type of `MarkdownRemark`.
So to take this to the next level, we're gonna set up an `if statement`.
We're going to look at the `node.internal.type` when it equals `MarkdownRemark`, then and only then are we actually going to do something.
Now, for the moment, we can just take `console.log` call and move it inside of there to make sure it's still running when expected.
So I'm gonna save the file, I'll restart the Dev server down below, and now I should still see some logs print.
But I should only get to one for each of those posts.
Right here I scroll up.
The first one is an internal type of `MarkdownRemark`, which is great.
Above that, we have our other post and above that there's nothing.
So no longer are we seeing the nodes for our `SitePage`s.
And that's what we want.
We've now successfully targeted just the nodes were actually trying to manipulate.
Now, if we head back to the `node` up above will see there's one particular field that does contain the entire file path that is file absolute path that's available on both of our nodes.
And this is what we're going to tap into.
We're going to take this.
We're going to remove the entire path except for the file.
Then we're going to remove the extension, leaving us with just the slug in this case, Gatsby or, in the case up above, just `React`.
Now there's actually a `node.js` module built in called Path, which allows us to manipulate the path.
And that has a function which allows us to extract the file name from a complex path like the one we've seen.
So we can find the documentation for this `@nodejs.org` here.
We want to go to docs.
Once we're on docs, we want to pick a version.
The API, where using is pretty standardized, so it'll be the same, no matter which one you pick.
We're going to scroll down to path.
These provide a bunch of different methods for manipulating string paths, and we're looking for one called `basename`.
`basename` takes an entire path like this one here, and it reduces it to just the file name and the extension.
We can use the second argument, however, to remove the extension, leaving us with just the file name.
And that is exactly what we're trying to do.
So let's go ahead and close down the documentation here and actually get that done.
Up above, I'm gonna load the built in path module.
Const path comes from requiring path.
There's no need to install it as it's a `node-core` module and down below.
What we're going to do is try to get access to the slug so constant slug is gonna equal will be using `path.basename` like we just saw in the docs.
We're going to provide the path and we saw that on `node.fileAbsolutePath` and then as the second argument, the `.md` which we're trying to remove.
And that should leave us with just the slug.
Let's actually see if that's the case.
I'm going to remove the old `cosole.log` call and adding new one into the mix right here.
All print a bunch of at signs to make this easy to find in the long list of terminal output.
Then, as the second argument, I'll print the actual slug.
So I'm going to save `gatsby-node`, I'm going to shut down things from the terminal and I'm going to start them up once again.
And hopefully we see our little message printing twice.
Once for each markdown post right here.
I did see them move by.
I have the first one with the slug of Gatsby and the 2nd one with the slug of `React`.
So we've successfully extracted the data to get the slug.
Now we have to call, `createNodeField` to, actually add the new field onto the `node` and this one really isn't too bad.
Down below will remove that `console.log` call.
We're going to call `createNodeField` and we need to provide an object with three different properties.
The first is the `node`.
We're trying to create the `node` field on now here I'm using the shorthand syntax to set the `node` property equal to a variable of the same `name`.
Then down below.
We need to set the `name` for our new field.
I'll go ahead and use `slug` for this and finally the value What is the value for slug while I have that stored in the slug variable and that is it.
This is all we need to do to achieve goal number one of adding these slug on to our `markdownNodes`.
Now, let's go ahead and test this out.
So I'm going to restart the project from the terminal for the final time.
And instead of looking at something from a `console.log` call, were actually going to try to grab the slug for our posts over in `GraphQL playground`.
Over in `GraphQL playground`, we can go ahead and check things out right here.
We have the `node` with the ``frontmatter``, ``html``, An `excerpt` based off of the new stuff we just set up.
We also have something called Fields and Fields has a single field.
That is the slug.
Perfect.
Now, if we actually run this, we're going to see that for each post.
We do get a slug right here.
We have `The Great Gatsby Bootcamp`.
We have these slug of Gatsby and down below.
We have the `React` post with e slug of `react`.
So there we go.
That is goal number one achieved.
We've successfully created a slug for all of those blog posts.
The next two goals are what we're going to focus on from here on out.
Now originally, I was gonna have this old as one video, but let's take a moment to take a break as this went on a little longer than I wanted to.
But I wanted to move through the individual steps using `console.log`.
So we could actually see what we were doing with this code over here.
So that's it for this one.
In the next video, we'll wrap things up by setting up the template and actually dynamically generating those new pages.
I'm excited to get to it, so I'll see you then.
