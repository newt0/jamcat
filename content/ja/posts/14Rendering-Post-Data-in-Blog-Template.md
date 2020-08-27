---
title: "14. Rendering Post Data in Blog Template"
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

<iframe width="560" height="315" src="https://www.youtube.com/embed/8t0vNu2fCCM?start=10328" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

In this video, we're finally going to render the post content on the post page, replacing our little placeholder text with actual data about the post like the title ,the date and the post content.
Now to get this done.
What we need to figure out how to do is how we can set up a dynamic `GraphQL` query.
This query needs to accept the slug, and it needs to give us back the data for the associated blog posts.
So over here in our template file, what we have access to is the slug, and we can't just have a `staticQuery`.
We need a dynamic query that actually takes that slug value into account.
So to get this done, let's start in `GraphQL playground` .
I'm gonna crack open a new tab will figure out how to use `GraphQL` variables and arguments.
And once we know how to use them, well, actually, integrate that into the blog posts page template.
You can view the docs to see exactly which query we're gonna use down below.
We've already used `allMarkdownRemark` to get a list of posts here.
We're going to use `markdownRemark` to get a single post now up above.
We have the call signature.
We have the query name followed by the list of arguments followed by what we get back, which is `markdownRemark`.
And here we can see the type details of that.
And we've already used this sort of stuff, fetching things like the `frontmatter`, the `html` or the Fields.
And that stuff we're gonna end up grabbing if we keep scrolling down, though to the arguments list.
This contains all of the different ways we can target the post we're trying to fetch, and in our case, we're going to target it by its fields.
So I'll be using the Fields argument.
And in there the only field we actually have is slug, and there are a few different ways we can target it.
We're going to use `eq`, which is short for `equality` that will allow us to target a post by its slug value.
Let's actually get that done.
I'm going to collapse the documentation and will set up a sample query right here.
Let's get started with the query.
In this case, that is `markdownRemark` from there.
We're going to provide our selection set.
What exactly do we want to grab.
In this case, let's just grab the `title`.
So that's  accessing the `title` when we actually wire this up in the component will grab more data so we can render it.
For now, though, we actually have enough in place to run this.
If I run it, what do we see? We see we're getting back an individual post, `The Great Gatsby Bootcamp` being the title.
So by default, if we don't provide any search criteria, it's just going to return the first post it finds now.
That's not particularly useful for us.
We want to target it by the slug value.
And to do that, we have to set up arguments for our query.
The arguments come right after the query name, and you could list them out right here on the same line.
But it's common to break those out into separate lines like so and inside of `()`.
we can specify the arguments we want to provide in this case, the only one we want to provide is fields.
So that's fields colon space, followed by the value.
Now, in this case, the value is an object because we want a target by slug.
That's also an object.
And in there we want to target by equality.
Now, this is just a `String` right here.
We can target by any of our slugs, for example, `React`.
So now we're fetching data about an individual post, but it's targeting a specific one.
And if I run the operation,  I can see I'm getting the data for that post back, which is great.
Now, I could change this over to Gatsby, and I could run that and we get that data and I could change it to `gatsby` with two `y`s, which does not exist.
And in that case, we get null as there is no post with that slug.
So this is the basic idea of what we're trying to accomplish.
Now that we know about arguments for our queries, the one other thing we need to talk about is query variables.
Query variables is nothing more than a set of data passed into your query.
Your query can then use that to populate things like argument values.
So when we type out our operation in the component, we don't want this data in the line.
This is static.
We want it to be dynamic.
So down below.
When we're using `GraphQL playground` , we can provide query variables by just clicking that item at the bottom and setting up some `json`.
So right here, I'm going to set up one key value pair.
I'll have the key, be slug, and the value will be the `slug` value like `react`.
This is exactly what Gatsby is going to do.
So it's important to understand how these work now what we need to do is set up our query to, actually accept that variable slug, and we define that right here after the query keyword inside of `()`s.
In this case, like we did down below, we start with the variable name prefixed by a dollar sign.
So that would be dollar slug to match up with what we have down below.
Then we define the type four slug.
So we have to be explicit about that.
And in our case, that would be string That's capital `S` string dollar sign.
Now, I'm not going to dive into the details about all of the other types that `GraphQL` supports.
There's a lot of great content out there on `GraphQL` and I also have a you Timmy `GraphQL` course if you're interested.
But with this in place, we now have enough to actually use this variable down below as the argument value.
So right here, instead of a static string, it is dollar signs slug.
We run it and we get our `React` data.
So this is exactly what we need to do from our component file.
We can get started by grabbing this entire query and copying it to the clipboard.
Then over in `Visiual Studio Code`, we can focus on getting this set up.
The first thing we need to do is import something from Gatsby right here.
I'm going to import `GraphQL` from Gatsby now(`import 'GraphQL' from 'Gatsby'`).
In the past, we would have also imported `useStaticQuery`, but our template files work a bit differently.
Instead of calling `useStaticQuery`, we will instead define our query separately and export it.
And the reason for this is that currently, there is no way to access the `context` which contains our slug.
If we were to work with `useStaticQuery`, So this alternative approaches gonna work really well just for our template files.
And this is the only one so right here.
We're going to create a new `const query`, and we're going to set this equal to right here will use `GraphQL` along with a new template string like we've done before.
And then we're just going to paste the entire query end now by default.
It's getting reformatted, and that's okay.
It just put all of our arguments and variable definitions on a single line down below.
We're still grabbing the `title`.
In addition, I'm going to grab the date from `frontmatter` and just outside of `frontmatter`.
I want to grab the `html` for the post as well.
Now, to ensure that Gatsby can actually access this query and run it.
We need to export query as a named export by just tossing export right up front.
So Gatsby is gonna grab this `GraphQL` query.
It's going to run it now.
The variable slug is going to come from the `context` we set up when we created the page.
Then it's going to take the response all of the post data, and it's going to provide that as a prop to our component down below.
So we're actually old done up above and down here.
We can set up our `props` and start to use them.
The first thing I'm gonna put inside of layouts is an `<h1></h1>`.
We're going to render the title right inside of there.
Now, here's the structure for that.
Right here.
It's `props.data`.
This contains the response.
So that means on there we have a `markdownRemark` property.
Let's grab that.
And once we have that, we can grab `frontmatter` and title and there we go.
That's all we need to get our header rendered to the screen.
Now let's actually test things out by heading over to the browser.
And right here I see `The Great Gatsby Bootcamp`, which is excellent.
So next up, we have our paragraph.
I'm gonna use the paragraph to render the date.
That's `props.data.markdownRemark.frontmatter.date`.
I'm going to render that to the screen and make sure it shows up right here we have it, which is great, and then from there will continue on with the last thing which is going to be a container, a `<div>`.
Now we already have access to the `html` and to render an `html` string inside of a component.
We set up a `<div>` and we used the following proper.
It's called `dangerouslySetInnerHtml`.
I type `da` and I see it showing up in the auto completion options.
This is the one we need to use in order to set our mark up from an `html stringfy`.
Now, right here we provide as that prop value an object.
So inside of `{}`, I set up another set of `{}` for the object itself.
And the property is underscore.
`_html`.
We set this equal to the `html` string we want to render in our case, that's `props.data.markdownRemark.html` and we're done.
Now, if we actually save things, we can check it out over in the browser.
And what do we get? We get our post, we have a paragraph for our text.
We have a `<header>` for the header we created in markdown.
And we have a nice list down below for the list we set up.
So there we go.
We have our complete blog posts structure.
I have the blog posts page with the list of all of our posts.
I can click one to go over to that post.
I could then go back to the blog posts link on another one.
Now that we have the basics of a Gatsby markdown blog in place, there's just one other feature I want to add to our markdown blog posts is the ability to set up images in our posts.
Once we're done with that, which is the topic of the next video, we'll start to focus on sourcing our content from a CMS.
I'm excited to continue on with the bootcamp, so let's explore how we can work with images in our posts.
