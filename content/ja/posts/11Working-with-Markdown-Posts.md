---
title: "11. Working with Markdown Posts"
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

<iframe width="560" height="315" src="https://www.youtube.com/embed/8t0vNu2fCCM?start=7417" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Welcome back to `The Great Gatsby Bootcamp`.
Now that we have the `gatsby-source-filesystem`, plugin, set up.
We have pulled in files from the filesystem, allowing us to access them via Gatsby's `GraphQL` API.
In this video, we're going to take that to the next level.
What we want to do is target just are markdown posts and we want to parse them from a file like this into content that's actually useful.
I want to be able to pull out things like the `title` if the date end the post body so I can render them to the screen.
We're going to get started with that process in this video, and to start, we're going to use another that pairs with the `gatsby-source-filesystem` plugin.
So this is gonna load those raw files from the filesystem.
The plugin where about to use is going to.
Look for markdown files in there, and it's going to parse them into useful data.
We confined this by heading over to the right here.
If we go ahead and search for something like `remark`, we should find the one we're looking for it is `gatsby-transformer-remark`.
So we used a source plugin tool, pull content from an external source.
Now we're using one of the many transformer plugins to transform that content into something useful.
And this plugin could not be easier to use.
There is zero configuration.
We just install it, set it up, and we have access to our post data.
So let's see what this looks like in `Visiual Studio Code`.
I'm gonna shut down the terminal, use clear to clear that output, and we're going to install it.
That's `npm install gatsby-transformer-remark` at the latest version, which is `@2.3.8`.
Now, if you're wondering what `remark` is, that's a standalone `JavaScript` library for parsing markdown files.
So all we're doing here is using a `gatsby-plugin-react-helmet`.
Go ahead and run the installer and up above we can get set this up in our plugins `array` at the end of the array.
We're gonna add a new item and this is just gonna be a string with the plugin name `gatsby-transform-remark`.
There's no need for any options like we had up above as this plugin.
It doesn't require any configuration.
Now that we have this in place, we can save the config file.
The installation has completed down below and all we're gonna do is start up our Dev Server once again.
So `npm run develop`.
And once the servers up and running will actually be able to access are parsed markdown posts via the `GraphQL` API.
I'll be able to extract the `frontmatter` I want, as well as the `html` for the blog posts body.
So let's see that in action.
Over here we have `GraphQL playground` .
I'm going to give things a quick refresh.
And if we crack open the docs under our queries list, you'll notice down at the bottom.
We have two new ones.
I have `markdown Remark` and `allMarkdownRemark`.
The  first one is used for fetching an individual post.
The other one is used for fetching a list of posts.
And that would be useful for something like the blog posts page, where I might want to show all of the posts I've ever published with the most recently published ones up top.
So to get started, we're going to use this query to fetch some data about every single post we've created.
Now, in this case, we just have to I'll crack open a brand new tab.
We're going to set up the query.
We are going to use `allMarkdownRemark`.
Then we can take a look at what exactly we have inside of there.
And the structure is really similar to the general structure over here with `edges` and `node` in the docs down below.
All-Markdown-Remark, we have edges.
We have `node` and `node` contains things about our post.
We have the `frontmatter`.
This is where we can access the title and the date and anything else we choose to add.
And we also have access to things down below, like the `html` for the Post, the excerpt and all sorts of interesting information, like time to read, which is calculated based off of the posts length.
So let's go ahead and actually grab some of this data in our query.
Over here, that's `edges.node`.
And in there let's just start with the title.
So the title is in `frontmatter`.
We're going to grab the title.
I'm gonna fire off this operation and what? Oh, I see.
I can see I have two posts.
The first with the title of `React` and the second down below with the title of `The Great Gatsby Bootcamp`.
From here, we could grab additional information like the date outside of `frontmatter`, but still in Node.
I could also grab stuff like the `html` or an excerpt, depending on what exactly I needed.
In this case, let's grab both Al fire off the operation.
And right here we can see we have the parsed `html` for our post and an excerpt we could show in our list of posts.
Now, this post was pretty simple.
But if I scroll down, we can see there is a more complex `html` structure for our more complex post.
I have the paragraph.
I have my header.
I also have my order list with the list items that I set up.
So all of this markup is based off of what we put in those markdown files.
Now that we actually have access to this data via the `GraphQL` API we can get run queries from our components to pull this data in and use it to render a list of the posts available.
Getting that done is gonna be your challenge for the video.
So let's talk about what I'd like you to do over here.
We're gonna move into the pages folder in there.
We have the blog file.
This is where you're going to spend your time for the challenge, and I'll paste those challenge comments in just above.
So the big picture goal is to show a list of posts on the page.
Now, for the moment, we're not worried about linking to any other page where the whole post is showing and we're not even worried about rendering the post body.
All we want to do is render the title and date for each post.
So to start down below, you're going to need to query the `GraphQL` API, fetching the title and date for every single blog posts using what we just talked about Over and `GraphQL playground` .
Then in the page down below, you're going to render an ordered less, using the `<ol>` element from their inside of the `<ol>` element.
You want to render a list item for each and every post.
The list item should have a nested `<h2>` `<header>` tag for the title and a paragraph tag for the date.
Now, if you don't remember how to take an array of objects and convert that into a list of `JSX` elements.
You can google something like render array of objects `React` and that'll get you to the right place and get you the information you need to jog your memory.
Now there's no need to do all of this at once before ever testing things out.
Test it in stages.
Run the query.
Use `console.log` to print the data to the terminal.
Make sure that looks good and get comfortable with the structure of the data.
Then use what you've learned there to actually get stuff rendered to the screen.
Finally, test your work on the blog posts page of the site.
I should see my to Post Titles `React` and `The Great Gatsby Bootcamp` both with their dates just below.
All right, knock that out, test your work, and when you're done, come back and click Play.
All right.
How that go If you ran into any trouble along the way, The good news is, as always, we're gonna work through these solutions together.
Now, I said the solution more like a solution, as there are plenty of different ways you could have structured this.
Now, Step one is to query that data.
And we can't do that without importing a few things from Gatsby.
We need `graphql` and we also need  `useStaticQuery` grabbing those from the Gatsby Library.
And once we have both of those in place, we can move into the function for our blog posts page component and actually set up a query similar to what we have over here.
We need the title, and we need the date.
So `const date` is gonna equal will call `useStaticQuery` providing `GraphQL` along with our template string.
And in here we're gonna have essentially the same thing we have over here, but without `html` an excerpt which aren't needed.
So right here.
Let's knock that out.
We'll start with Query.
We're trying to use the `allMarkdownRemark` query.
Then we're going to go ahead and grab `edges` from there, `node` from there.
We need the ``frontmatter``, which contains all of the data were looking for.
And we want `title` and we also want `date`.
Perfect.
So now that we have the query in place, let's just use `console.log` and dump the data to the terminal to make sure this part is actually working as expected.
If we get the correct data, then we'll move on to steps two and three, actually rendering it on the page.
For now, though, I'm gonna head over to the blog posts page.
I'll crack open the `Chrome Dev tools ` right here.
I have the console and down below.
I have an object.
This is the data variable.
We have `allMarkdownRemark` and we have our `edges` array where each edge represents a post right here.
One of the posts as an example, has that `node` property.
We then have `frontmatter` and on their we have `date` and `title`.
So the structure were getting back.
Here is the exact same structure we got back over here.
Now let's actually use that to render some content to the screen.
So remember, Step two was to set up an ordered list, and I'm going to do that down below.
I'll remove the paragraph.
I'll set up the ordered list and inside of here we want to put a list item for each and every post we found.
That means we want iterating over.
That edge is `array`.
And we want to take the `edges` object, and we want to convert that to a list item.
So let's actually get that done right here, setting up some `{}` and we're going to access that array.
That's `data.allMarkdownRemark` exactly like we just saw in the terminal.
From there, we grab `edges` and that's an `array`.
Now we have an `array` of objects, and what we want is an `array` of `JSX` elements.
So I'm going to use the map function to convert the object over to `JSX`.
Now, in this case, our function gets called one time for each edge.
So one time for each blog posts and right here will get access to the individual object, which I'll just call an edge.
Now it's the job of the map function to return some `JSX`.
This is going to show up for each and every post.
So right here we start off with a list item and I mentioned in there I wanted a header to tag, and I also wanted a paragraph, so I'll set those up as well.
Now all we need to do is pull the title and the date off of edge and put them right inside of these two elements, so we'll start with the title over here.
We can see that for one of the `array` items.
We have the `node` property than `frontmatter`, then `date` and `title`.
So that means over here that would be `edge.node.
frontmatter`.title`.
And with this in place, we could test our work so far to make sure at least the `title` is showing up and it is right over here.
I have `React`, followed by `The Great Gatsby Bootcamp`.
Next up, we have that paragraph and I want to put the date right inside of there.
That will be `edge.node.
frontmatter`.date`.
Identical to what we had up above, just accessing something different from the `frontmatter`.
Now we can actually remove the `console.log` call as we're all done.
We have successfully fetched the data and used it to render a list to the screen.
If we check things out in the browser, we have our list item won.
The title is `React`, and the date was April 2nd.
And here we have `The Great Gatsby Bootcamp` post with the date April 4th.
With this in place.
We've made some really great progress towards what we're working towards now this page is not done yet.
We do need to link over to a blog posts page and eventually we're going to include some additional information here.
But this is a really good start.
Next up over in the terminal, all I'm gonna do is closed down.
Excuse me.
Delete the challenge comments, and that's where we're going to stop for this one.
We have our query which is fetching the markdown post data down below.
We're using some `JSX` and `JavaScript` to get everything rendered.
Now the question is, how do we create a new page for each and every post I mentioned? What we're not going to do is manually add new files to the pages directory.
Instead, we're going to use a Gatsby API that's going to allow us to dynamically generate new pages with dynamic content.
So we'll be able to generate new pages where the page content is the blog posts content.
I'm excited to get to that, and we'll be starting that in the next video.
So let's go ahead and jump right in
