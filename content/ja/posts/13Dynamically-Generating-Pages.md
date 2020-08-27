---
title: "13. Dynamically Generating Pages"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=9314"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

It's time to continue on with our three goals.
We already have our page slugs.
Goal number two is to generate a new template for the blog posts page, and we're going to do that by creating a new directory in the source folder called Templates.
Now the reason I'm creating a new folder is that I want to differentiate the `React component` were about to create from the standard components in the Components Directory or the specialized components in the Pages folder.
Here we're working with page templates and those are going to work slightly differently, so we'll create this new folder in there.
We'll put a new file.
I'll call this `blog.js`, and in here, all we need to do is create and export a `React component`, the template for ourblog posts pages.
So right here, let's start with the very basics.
I'm just going to `import 'React' from 'react'`.
Then down below, I'll set up the blog posts int, which is just a function, and I'll have it return some static text.
Now I'm actually gonna put that taxed inside of a layout, so let's import layouts real quick as well.
Importing layouts from.
to get out of the templates.
Directory, `/components` /layouts.
Now we can use it and actually render some content to the screen.
So right here, layouts in there.
This is the blog posts template.
Now you'll notice that we're not rendering anything specific about the post like the title, The date or the actual body will work on that in just a little bit.
For now, we just want to get the basic template file in place down below.
Export default blog, and we're done.
So we have the template in place for each and everyblog posts page.
That is goal number two.
The third goal is to generate a new page for each post, and that's going to require us to use another API from inside of the Gatsby `node.config` file.
We can check this out over in the API docs.
So right over here, what I'm going to do is scroll to the top of the `node` API.
page back to that table of contents, and the one we're looking for is actually the very first one as of now, `createPages`.
`createPages` gives us everything we need to dynamically generate new pages for the site.
Now down below, we can see exactly how this works.
Don't worry.
We're gonna work through all of this together and will actually be using a slightly newer syntax to make life easier.
What I really want to focus on are just these two lines right here.
We export a create pages function, and Gatsby gets access to that function and runs it a single time.
And we destructure that first argument to get access to `GraphQL` query and actions `GraphQL` is going to allow us to fetch some data.
In our case, we want to fetch those markdown nodes which contains the data we need and on actions.
We get access to an action for creating a new page.
So let's go ahead and actually set this up.
Then we'll work through the rest of the function, getting everything in place.
So right over here, inside of the Gatsby, no, to file module.exports.That's going to be `createPages` with a capital `P`.
And this is just a regular old function.
Now I am going to destructure that first argument like we saw them do in those API docs.
The first thing we have access to is a `GraphQL` function.
It's actually a little different than what we've been importing from Gatsby in the past, and the second thing we get access to are a bunch of action functions.
In this case, just one right here.
We're going to grab that it is called `createPage` and we're going to call it for every new blog posts page we're trying to create right here.
I'm just destructuring that from actions which is itself an object so down below, we can now take advantage of this API.
To dynamically create the pages.
And we need to do three things one get path to template to get markdown data.
And then finally, three render excuse me, not render create new pages.
So these are the three things we need to be able to do, and the first one is super easy.
We just want to get the path to that new template we've created.
That's `blog.js`.
I'm going to store this in the following variable.
I'll call it something like blog posts Plett, and this is going to be a path an absolute path to that file on your machine starting way back from the root of the hard drive.
And to do that will use `path.resolve` that will `resolve` a partial path which will provide as a string right here.
Now, for us, this needs to be the path from our current location in the `Gatsby Bootcamp` folder to the destination, which is `blog.js`.
So that's `.
source/templates/blog.js`.
The `resolve` function itself is gonna add everything up front to create an absolute path from the root of the hard drive.
Now, the next thing we need to do is actually fetch the markdown data.
We need access to all of those slugs so we can dynamically create these new pages.
Now, we already know how to query those.
We've done just that in `GraphQL playground` , and we're going to use a similar query inside of the `node` file.
Now, we don't need to grab anything except for the slug.
So the operation will be performing is gonna look a little bit like this.
The end result is that we get a bunch of edges with the slug defined for each.
That's all we need.
Now let's head over to the file and talk about `GraphQL`.
This is not the same as the `GraphQL`.
We've been importing from the Gatsby module in files like our header component.
This is actually a function itself that we pass a string `GraphQL` query too bright here.
That's going to be a `GraphQL` we're gonna pass to at a template string.
And in here we just type out the query We want to perform exactly like we have over in `GraphQL playground` .
So it's a query that is `allMarkdownRemark` from their `edges` from their `node` from their fields and finally slug.
So this is what we need to provide in order for everything to get fetched correctly.
Now you'll notice that we're not doing anything with the return value.
This function actually returns a promise.
So we have a couple of different options.
I can add a, then call down below to get access to the value that eventually comes back.
Or I can use `async await`, which is what I'm going to docs.
Oh, right here.
We're gonna mark this function as　`async`.
Then I'll set up a new constant response, and I'll be awaiting the `promise` from this function.
Now, unfortunately, I can't dive deep into a sink a weight in this particular video, as I want to stay focused on `GraphQL`.
If you're not familiar with the syntax, though, it is nothing more than a way to make a `promise` API.
look a little more on a synchronous, sir.
Right here.
We have some very synchronous looking code down below.
We can now do something with the response.
Now, what exactly are we going to do? Well, we want iterating over all of those posts, and we want to run that create page function for each of them.
So right here we have our response.
We have data.
We have `allMarkdownRemark` and on their we have `edges`.
Now we're going to use the for each `array` method to run a function.
This function right here for each of those.
Now, if we have an array of edges, I could call the individual element something like an edge.
And now, inside of here, the goal is to call, `createPages`.
So I'm going to call `createPages`, and I'm going to provide to it an object and on here.
We have to provide three things.
First up is the component were trying to render.
Now the component is not an actual `React component`.
It is just the path to the component.
And we already have that up above.
I have the blog posts template string, which I'll use down below.
The next thing we have to add on here is `path`.
So we're creating a new page.
But where exactly should someone be able to access the page we're creating.
For example, `/test` would be `localhost:8000/test`.
In our case, though, it's gonna be dynamic based off of these slug that each post has.
So I'm going to use a template string.
That's `/blog/${theSlug}`.
So right here inside of the template string will interpret the following value.
That's `node`.
Excuse me `edge.node`.
Then we're going to grab fields and we're going to grab the only field we have slug.
So now when I visit forward slash blog posts word slash some slug I'll see that blog posts page rendered down below.
Just one last thing that is ``context``.
``context`` is an object and this contains stuff we can pass down to that template.
Now, In our case, the only thing we really need is the slug.
If that template has the `slug`, it can fetch the rest of the data for the post like the `title`, the `date` and the body content.
So right here, we're going to pass the `slug` through which you could consider kind of like an `id` , as it is unique for each and every post.
And right here we'll just use the following that is `edge.node.fields.slug` once again.
So this is going to run twice, creating two new pages.
The first is forward slash blog posts word slash `React`, and the second is forward slash blog posts word slash Gatsby.
Both are going to be rendered using the template we've defined.
And both will have access to a little extra data which they can later use to pull everything they need about that blog posts.
Now that we have this in place, we're all done.
I know that this in depth configuration can be a little dry.
But if you are interested in using Gatsby being comfortable with `createPages` and with on create `node` is essential for doing what we've just done here.
This exact same stuff is just as essential.
If you're pulling your data from a CMS like we'll see a bit later.
For now, though, let's test things out down below.
I'll shut down the server.
I'll start it up once again, and we're actually going to try to visit one of those two pages.
Let's start with `/blog/react` over in the browser.
I'll head back over to the Gatsby site here.
We're on the blog posts page now.
We don't have links to our post pages yet, so we'll have to manually visit them.
I'll go to forward to `/react` first.
If I visit that, what? Oh, I see.
I see this is the blog template, which is awesome.
If I go to `/gatsby`, what do I get? I also get that blog template.
And if I go over to something else like `/node`, what dough I get right here.
I get a 404 page.
So there is no Node blog posts.
But if I were to create it, this particular page would exist and we would actually be able to view the So let's go back to one of the posts pages that did exist.
And there we go.
We now have a way to dynamically generate pages.
Now we're not done yet.
There's still two very important things we want to do on this page.
We actually want to render the post content and on the blog posts, what I want to do is linked to the individualblog posts pages.
Now that second task is something you already know how to do it.
So that's gonna be your challenge for the video than in the next one will focus on pulling in the individual data to the template component.
So for the blog posts page, what you want to do is actually create clickable links for each and every post that heads over to the correct URL.
So let's talk about what I'd like you to do.
We don't need any of these files any longer, including our little goals list.
As we've completed all three of those, the only file you're gonna need is the blog posts page and just up above, I'll paste into the challenge comments.
So the goal is to link to the blog posts in the list that were rendering down below.
Now, right here to get that done first, you're going to need to fetch the slug for each post by modifying our query down below.
Then you need to use that slug to generate a link.
Make sure to use the `Link` component provided by Gatsby.
And you want that to go to the correct location, So `/blog/slug`.
Finally test your work.
Actually, pull up the page in the browser, click those links and make sure it brings you over to the correct blog posts page.
All right.
Take some time to knock out those three steps.
Test your work.
When you're done, come back and click Play how that go.
Let's get to it.
And the first thing I'm gonna do is grab the  `Link` component from Gatsby as I know.
I'm going to need it a bit later.
Down below.
We want to make sure we fetch the slug for every single post.
Now we have that query right here inside of `node` along side of `frontmatter`.
We want to grab fields and in there we want to make sure to grab the slug so we can actually use it when creating our links destination.
Now, down here when it comes to modifying the structure, I didn't give you any specific rules for how to create the link or what to put inside of it.
So for now, anything works.
What I'm going to do is set up the opening tag for Link right here, and I'll put the closing tag below the paragraph, making both of those clickable.
Perfect.
Now all we need to do after in denting things is to set up the to property.
And this needs to be dynamic.
There is no one static destination.
It is based off of the static text, forward slash blog posts word slash and the dynamic text stored in that slug field.
And for us right here, that would be the following `edge.node.fields.slug`.
So there we go.
We have our Lincoln place, and hopefully it's working as expected.
Before we actually test this out, I'm going to remove the challenge comments up above, save the component file, and now we'll make sure our link is working Over here.
I have the blog posts page and I am seeing links for both posts.
If I click the `React` one.
I'm brought over to the `React` page.
If I go back to the blog posts page and click `The Great Gatsby Bootcamp`, I'm brought over to forward slash blog posts /Gatsby, which is awesome.
So at this point, when it comes to the markdown blog, there is only one thing we need to do.
We need to figure out how to actually use the slug in this template to fetch the data, the title, the date and the post body.
Because all of that needs to get rendered to the screen.
That's what we're going to do in the next video, So let's jump right into that.

## お知らせ

{{< alert theme="danger" >}} 
本書き起こしはgithubレポジトリで管理しています。
**ミスを発見したら、Github issuesでお伝え頂ければ幸いです。** 
[Issues on Github](https://github.com/newt0/gatsbybootcamp-transcription/issues)
{{< /alert >}}

{{< alert theme="info" >}}
Andreaw Mead氏のUdemy Coursesが {{< color "#FF0000" >}}現在90%OFF{{< /color >}} です!
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Freact-2nd-edition%2F" target="_blank" rel="nofollow">The Complete React Developer Course (w/ Hooks and Redux)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fgraphql-bootcamp%2F" target="_blank" rel="nofollow">The Modern GraphQL Bootcamp (with Node.js and Apollo)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fmodern-javascript%2F" target="_blank" rel="nofollow">The Modern JavaScript Bootcamp</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fthe-complete-nodejs-developer-course-2%2F" target="_blank" rel="nofollow">The Complete Node.js Developer Course (3rd Edition)</a>
{{< /alert >}}

