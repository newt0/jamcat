---
title: "17. Rendering Contentful Posts"
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

<iframe width="560" height="315" src="https://www.youtube.com/embed/8t0vNu2fCCM?start=13109" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

now that you have content in your `Contentful` CMS, what we're gonna do is figure out how we can get it rendered in the browser.
We've already seen a sample `GraphQL` query that fetches are blog posts from `Contentful`.
And the goal in this video is to get our post list rendered using `Contentful` posts instead of using the posts we created with markdown files.
So to kick things off, what I want to do is talk about how we can customize the all `Contentful` blog posts queary.
We're gonna learn how we consort our posts in a particular order and how we can customize the response of things like published date, getting a date that's a little more user friendly, as opposed to the current time stamp we're seeing in the response.
Let's get started by figuring out how to sort our data.
And remember, `GraphQL` is self documenting.
So the docs contain everything we need in order to get this done down below.
We have all `Contentful` blog posts the query where using here we have our type details.
That's the response.
We're looking for the arguments allowing us to customize the response.
There are four we have skipping limit, which is useful for pagination.
We have filter, which is useful.
If you're trying to implement something like a search bar and you want to filter to a subset of your posts and we have sort sort allows us to sort our data in an order that makes sense now, right here.
When we use sort, we provide two pieces of information.
We provide the field we want to search by.
Excuse me, sort by, and we also provide the order either ascending or descending.
So right here for fields, we can see we have a bunch of different fields available.
Now, this allows us to sort by various fields that aren't applicable to.
So what we're working with right here we have a lot of different fields because off that special, rich text field we set up in our case, if we scroll up a little bit, the one we're looking for is just sorting by published date.
And that's exactly what we're gonnado.
So let's take this over to the query right here on the query.
We are going to set up our arguments.
I'm going to set up sort and remember we have to provide fields.
That's plural.
And the field we're working with here is going to be the following that is published date.
Then next up, we have to provide an order.
And in this case, we could sort in ascending with A S C or descending with D E S C.
And this is the order we're going to go with.
Will have the most recent posts first, and we'll have the oldest ones at the bottom.
So if I run this, we should see the order reversed as this was published on the eighth, and this was published on the 10th and right here.
That's exactly what happens.
So we have our newer content first, using this argument, one more thing we can do is customize the published date value.
So let's check this out.
If we head over to the docs once again, we're going to go all the way to the left, and we're going to go to the type details.
We have edges, we have Node.
And here is the `node` we're currently working with.
We have title slug and published date, and you'll notice that with published date we have a `()`s set right here.
If we click on that.
There are actually arguments we can provide for just this one field To customize it.
I could do something like from now to say this post was published three days ago or 10 seconds ago.
I could used format string in order to customize exactly how I wanted to format it.
Let's explore both will start with from now.
So right here set up some `()`s from no setting that too.
True, I run it and I can see a day ago and three days ago.
So maybe that's what we want.
In which case this would work really well if we wanted to customize it even further.
What we could do is use the following It is format stringfy.
Now this uses the formatting pattern made popular by the moment JS library.
So here's an example.
I will use the following pattern.
It is four EMS, followed by a Space Capital D lower case.
Oh, comma.
Then why four times that's month, day and year.
And if I run it we can get see, we get the following set up April 10th 2019 April 8th, 2019.
Now you can provide whatever you'd like in there to really customize it and make it your own.
If you want to find all of the patterns you can use, you can open up a new tab and go to moment.
JS.com /docs Once you're there on the right hand side, you want to go to display and down below.
You can see all of the different tokens you can use in your pattern.
So there are different ways to represent months the day of the month, the day of the week.
There's all sorts of great patterns here, allowing you to generate the specific output you want.
In our case, though, we're not going to go any further.
We're gonna leave it like this.
April 10th 2019 is exactly what I want to show on the screen.
So now that we have this query in place, we're going to take this over to our blog posts page, and we're going to render these posts instead of the markdown posts.
Now getting that done is actually going to be your challenge for the video, so let's dive right into that in `Visiual Studio Code`.
We're going to close all of the open files we have and we're gonna focus on just one inside of our pages directory.
We have blog.js now.
Currently, we have a query that fetches the markdown data and renders that down below.
We need to change both of these things to work with the `Contentful` data.
So up above, I'm going to paste in the challenge comments, and they're pretty straightforward.
The goal is to render the `Contentful` posts in our list.
So first up, you want to swap out the markdown query with the `Contentful` query, and if you want to customize it further, using other arguments or options, you're more than welcome to.
But in general, this query can be used inside of the component.
Next up, you have to update the component to render the new data.
So our data structure is a little bit different, even though we still have those same three things.
We still have the title, the date and the slug.
They're just in a different place on the response.
And for the moment, don't worry that your link is gonna link to a non existent page.
Will address that shortly.
Finally, test your work.
Pull up the blog posts page and make sure you see your two `Contentful` posts showing up as opposed to the two markdown posts.
All right, pause the video, Knock that out, test your work, and when you're done, come back and click Play how that go, Let's get started and the first thing we're going to do is swap out the queries.
Now we have the old query over here, so let's go ahead and get rid of that.
It's no longer `allMarkdownRemark`.
We're going to go ahead and work on the new one.
So that is all `Contentful` blog posts from there were still going to be setting up our arguments.
Now we could do all of that on one line, or we could break it out onto multiple.
If we wanted to do it on one line, it would look like this will set sort equal to an object on their fields, is equal to published date, and then we'll go ahead and set order equal to descending Perfect.
Next up, we have to go ahead and specify what exactly we want back on the response that is edges `node` and from there we need the title.
We also need the slug and finally we need are published date and we're going to format that exactly like we did over here using format stringfy.
So right here that would be format string, setting it equal to whatever format string we wanted to use.
And I'll use the same one from before the full month, followed by the day of the month, a comma, then the full year.
All right, now that we have this in place, we are done with step number one, and at this point are program would crash if we tried to run things.
That's because we're trying to access data down below.
That no longer exists.
Since we've changed the query up above in the browser, If I go over to the blog posts page, it is indeed failing as expected.
So now that we've seen things fail, let's actually get things working.
We can go ahead and move on to step number two, where we update the component to render the new data.
So right down here, let's knock that out.
Data.
allMarkdownRemark` that no longer exists.
It is all `Contentful` blog posts now.
We still have edges and we still want a map over that down below.
Here we have our list item, but we need to do is customize this, starting with the slug.
It is still edge Node, but there's no longer fields.
It's just edge `node` slug exactly like we're seeing up above edge `node` slug Down below.
We have the title as well.
That does not exist on `frontmatter`.
It's right on `node` and below that we have the old date `frontmatter` that no longer exists and it's called something different right here.
Edge.Node.published date.
Perfect.
Now, with this in place, we have the new query and we're rendering that brand new data.
And hopefully everything works as expected when we actually move on to step number three and test our work.
So I'll refresh the page over in the site.
And what do I get? I have my two blog posts a `Contentful` blog posts and debugging `node.js`.
Now I can see down below at the bottom left in the little grey bar that it is linking over to the correct pages.
But if I click those links, obviously we don't get the pages content since we haven't wired that part up.
But the blog posts itself is indeed working, and that is a great start with this in place, we're all done for the moment.
In the next video, we're going to go ahead and actually create those pages dynamically using the `Contentful` content.
I'm excited to get to that, so let's jump right in to the next one.
