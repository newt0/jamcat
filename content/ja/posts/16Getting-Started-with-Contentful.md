---
title: "16. Getting Started with Contentful"
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

in this video, we're going to start the process of connecting our Gatsby project to a content management system.
Now, in this bootcamp will be working with the `Contentful` CMS.
But the exact same principles would apply if you wanted to use another content management system like `Wordpress` or Drew.
Paul Gatsby has plugins to support all of those CMS is and more.
But once again, we're gonna end up using `Contentful`.
It's my personal favorite of those options.
It's really easy to work with, and we can get started for free.
You can find it over at `Contentful`.com, and right here we're just gonna go ahead and create a free account.
Everything we're going to do in this bootcamp is completely free and doesn't require a credit card, just a free account.
So let's create that account and once we have it created will get some content into the mix.
Right here.
I'm going to create a new account with you, so I see the exact same stuff that you're seeing.
So let's fill out those basic account details when it comes to choose your development platform.
We're just gonna pick `JavaScript`, though, honestly, this choice doesn't matter, and down below will toss a password into the mix.
Now we can go ahead and actually create the account.
And when wedo, it's gonna bring us over to a little welcome screen trying to get us to pick one of the tutorials to work through over here for content creators like a copywriter And over here for developers, honestly, we're not gonna work through either of those as well.
Be discussing things together in the video.
And the quickest way to get what we want is to just click explore content modeling.
This is going to create an example project for us.
And that's not a project we're going to work with.
This comes pre populated with models and data, but what we want to do is figure out how we can set things up from scratch for our needs.
So once the example project is created, we're just going to create a brand new one and start there.
All right, let's explore the example project and we're done exploring it.
Let's create our own from the menu.
We can click, create space.
A space is like a new project, and we're gonna go ahead and use our second free space.
We get to on a free plan, and right here I'll just call this something like `The Great Gatsby Bootcamp`.
Though the name is not important.
And right here we want to create an empty space that we can populate with our own content.
In this case, the blog posts content we want to show in our Gatsby site.
So let's actually create this new space right here, a confirmation screen.
And once it's created, what we need to do is focus on defining the type of data we want to track.
So there are two main tabs I want to talk about up here.
We have content model, and we have content.
Content model allows us to define models for the content on our site.
This could be a model for a blog posts where we have a title, a published date and a body.
It could be a model for an author where we have the author's name, their Twitter profile link and a profile picture.
So over here we're creating structured data under the content tab.
We actually create instances of those things.
So this is where we would define our six blog posts and our two authors and whatever other content we wanted to create.
So let's see this in action Under content model, we're going to create our first content model for a blog posts.
So right here we have a required name field.
I'll just use blog posts and down below.
It's creating an API identify air for us, which will end up using a bit later.
There's no need for a description, so we'll leave that blank, although you could come back and edit it later.
And now we're just going to create the model now.
The motto, by default isn't tracking any data whatsoever.
It's up to us to configure the fields that makes sense for a blog posts.
Now we already have some structure data over here in our to markdown post for both, we have the title.
We also have the date, and finally we have the actual post content.
So those are three distinct fields and we're going to be adding three fields to the blog posts content model.
Let's go ahead and add our very first field right here.
We can see that with `Contentful`, we have a lot of field options.
This could be a text field, a complex, rich text field with formatting images and mawr.
It could be a simple text field.
It could be a number, date and time location, media, a Boolean like a check box and a whole bunch of other options.
Now, in our case, we just want a simple text field for the title.
So let's pick that and give it a name right here.
We type something to show in the `Contentful` forms, in this case Capital T title.
And behind the scenes, it generates a field i d.
And this is how will access our data from the `GraphQL` API a bit later.
Down below.
We have a few options, none of which we need so we can create our first field.
Let's go ahead and add our second field, and it's actually one I forgot about.
This is also going to be a text field, and the name for this one is going to be slug.
So there's no longer a file name that we can use to find the slug.
So we're gonna have the Post creator pick a slug for that post.
Next up is the published date right here will use their date and time field for this, giving it a name like published date will create that field.
And from there, there's only one more field.
We need the field for the post body, and that is gonna be a rich text field.
So right here will click that option and go ahead and provide a name right here.
I'll use body for this one.
Now, once we create that, we've finished off our content model.
We have modeled a blog posts with four pieces of data.
And as long as those four pieces of data are provided, we have enough to actually get something rendered to the screen.
From here, all we need to do is click save to, actually save this content model.
And once it saved, we can start to create blog posts based off of the model over here.
For this, we go over to the content tab and we're going to click.
Add blog posts.
That option is also available up above Whoops.
It's not available yet.
Not until we have our first post in place.
So let's get our first post in place right here.
Add blog posts and were brought to our blog posts editor page.
It has all of the fields we specified Title slug published date and Body And now we can create our very first post for the title.
I'll use a `Contentful` blog posts for the slug.
I'll just use something like `Contentful`.
I can pick whatever makes sense for me.
Then down below, I'll say This one was published today and we can set up our post body as well.
My post is here..now.
Currently, this post is not published, which means that even if we did have things wired up with our Gatsby site, this data would not be accessible to the outside world.
We can fix that by changing the status from draft to published by Clicking are Publish Button.
Now we have our first published post, and if we had back over to the content page, we can see it showing up right here.
From here, we can add a second post into the mix.
Then we'll figure out how to actually pull this data into our site right here.
Something like debugging `node.js`.
I'll have the slug be debug-Node for the published date.
I'll say this was published a couple of days ago and for the body.
I will say, Here's how you can debug your aps dot, dot,.and we'll go ahead and publish this one as well.
So now we have our very first content model blog posts, and we've created two instances of it a `Contentful` blog posts and debugging `node.js` from here.
What we want to do is figure out how we can access this data via our Gatsby.
`GraphQL` API, Once we have that in place, will be actually able to show this content on the site.
Getting that done requires us to set up a `gatsby-plugin-react-helmet` API page and will be searching for `Contentful` now, right here.
The first result.
That's the one we're looking for.
Gatsby source `Contentful` that's going to allow us to source are `GraphQL` content directly from the `Contentful` CMS.
Now, actually, setting this up is really easy down below.
All we need to do is provide our space i d, which is the I d for our project and our private access token.
And we'll look at where that lives in just a moment now.
Before we actually set this up, I did want to mention there are source plugins for other CMS is as well.
For example, if I search `Wordpress`, we confined one for that Gatsby source.
`Wordpress`.
And if I search for something else like Drew pull, there are plugins for that as well.
So when it comes to your Gatsby site, you consorcio, that content from a lot of different places you could even use multiple if that made sense for your particular situation.
In this case, though, we are going to set up that `Contentful` source plugin.
So let's head over to `Visiual Studio Code`.
Shut down things in the terminal and we're going to run `npm install` to get that installed.
That is Gatsby source `Contentful`.
And we're going to go ahead and install that, and we can go through the process of setting it up in the meantime, so to get this set up, what we need to do is head over to that gatsby-node file.
Excuse me? The `gatsby.config` file where we have our long list of plugins and we're gonna add a new one into the mix.
Now, we could put this wherever we'd like.
I'm just gonna toss it right up top as the first item in the plugins array right here.
This is something we'll be setting up options for.
So this one needs to be an object in there setting up the `resolve` property with the plugin name right here.
That's Gatsby source `Contentful`.
And I can see down below that it did indeed, installed correctly, which is a great first step.
Next up, we provide our options object and on the options object we have to specify.
Two things are space I d.
That's a string.
And we also need to specify our access token.
That is also a strength.
This is what's going to allow us to actually fetch that content.
Now, both of these, we confined over in the `Contentful` web app.
So let's head over there.
From here, we can go to settings and down to API keys.
Now you're spaces by default.
Have an example key pair set up for you.
So if we click on that, we can view all of those details down below.
Down here we have our space, i d, and we also have our content delivery API access token.
That is what we need.
So to set this up, we're gonna use environment variables to prevent this sensitive data from sneaking into our source code.
We already have an environment variable file for that, so we'll just make some more changes to the Dev E N V file.
Right here we have our one environment variable.
Let's add two more.
First up will be `Contentful` underscore space underscore i d.
Then after that, we'll have `Contentful` access token, and all we need to do is populate those two with the correct values.
I'll grab the space I d.
I'll bring that right here.
Then I'll grab that content delivery access token, and I'll bring that over to the E N V file as well.
Now, with this in place, we can access those two things in our CONFIG file, and then we'll be all done will have access to all of that `Contentful` data.
Let's go ahead and use those variables.
So over here for space i d.
That is process.e n v.Contentful Space I d and down below.
For access token, that is processed.e n v.Contentful access token and world done.
Everything is configured.
So with this what? Seven lines of configuration code were able to set up everything we need to source content from `Contentful`.
Now, what we're gonnado is start up our APP in development mode using `npm run develop`.
And once that's up and running, we're gonna head over to `GraphQL playground`  and take a look at the new queries we have access to because those queries are going to allow us to access the data we just created.
So right here, these sites starting up, I'm gonna head over to `GraphQL playground`  and give things a quick refresh over in the docs.
We should see those new queries showing up and right here we have six.
Now we have to for working with content types.
This is not going to allow us to fetch the content itself.
But it's a way to work with content types, not something we need.
And we also have a couple for working with our rich text `node` as their some specifics to that will talk about shortly.
For now, what I really want to focus on is `Contentful` blog posts and all `Contentful` blog posts.
We can use the  first one to fetch data about an individual post and we can use the 2nd 1 to fetch a list of all posts.
And that's exactly what we're gonna end up doing now.
If I crack that open, we can see a similar structure to what we had with our other queries.
We have edges.
We have `node` and `node` represents our post.
We have title slug published date and body.
So let's actually set up a query to fetch some post data.
I'm going to crack open a new tab over here will set up a brand new query, and this query is going to use all `Contentful` blog posts to fetch something about every single post we're working with.
Now we want to work with edges in there.
We have `node` and over going to do is grab the title for each and every post.
So if I take a quick moment to fire that off, what do I get? I get debugging.
No JS and I get a `Contentful` blog posts.
So there we go.
We've successfully sourced the content from the CMS right inside of our Gatsby `GraphQL` API.
Let's grab a couple of other fields real quick as well.
We're gonna grab the slug for each post and we're also going to grab the published date.
Now I'm intentionally not grabbing the body field because it's not as simple as just getting a body back, which is a bunch of `html`.
There's a little more to it.
And don't worry, we're going to address that in the next video.
For now, though, we can fire off our new query and we get new data.
I see the correct slug and the published date for both of my posts were also going to talk about how we consort our posts from most recently published two oldest, and we'll figure out how we can actually format this date to be a little more friendly when it comes to rendering it to the screen.
I'm excited to continue on with `Contentful`, but let's take a quick moment to recap what we did.
Essentially, we use `Contentful` as a Web app to manage our site content.
We have our content models and our individual content themselves.
We were then able to pull all of this into our Gatsby `GraphQL` API, using another one of Gatsby's source plugins.
In this case, it was Gatsby source `Contentful`.
Now that we have access to it via our API.
We could use those queries in our `React component`s to get that data rendered to the screen.
That's the topic of the next lesson.
So let's jump right in.
