---
title: "10. Sourcing Content from the File System"
description: "The Great Gatsby Bootcamp"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=6692"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

A couple of videos ago, we went over to the browser and went to The Gatsby home page to.
Look at the following visualization here.
We talked about how we were going to use the `GraphQL` API that Gatsby provides a source our data from external data sources now.
So far, we have done that with site meta data.
We were able to pull in some basic information getting that rendered in our `React component`s.
But it's not exactly a great place for more complex data.
For example, the blog posts were trying to create for our site storing that inside of that little site.
`metedata` object just is not realistic.
Instead, we're going to start to focus on creating a blog posts word by markdown blog posts.
So inside of `Visiual Studio Code`, we'll be adding markdown files for each of the blog posts we want to create.
Those will then be listed over on the blog posts page of our site and will also have Gatsby dynamically generate brand New pages based off of a page template for each and every blog posts.
So that's the end goal.
Let's get started by writing a couple of posts in `Visiual Studio Code`.
What we're gonna do is put our blog posts in the `src` directory.
For the moment, we can collapse the other directories inside of there, and we can also close all of our open editors.
We're going to create a brand new folder in the `src` folder and I'm going to call this posts.
You could call it something else like blog posts.
The exact name could be whatever you want in here, we're gonna add a couple of posts.
I'll have one called `gatsby.md` and real quick.
I'll create another one.
Let's call it `react.md`.
So for The Gatsby post, we're just gonna add a little bit of sample text.
I'm not actually going to write out an entire post.
Let's get started by adding, What's number.
One as the `frontmatter` for our markdown posts?
So we start with `___`.
We end with `___` and right in between, we can add key value pairs for whatever makes sense for us now.
4 posts.
You might want to include the post `title`.
Maybe the date, the post was published, a list of tags the author, whatever sort of data you want to add on to the actual post content.
So right here, let's keep it simple.
I'm going to set up a `title` for this post, so that is `title` call and space.
Inside of quotes.
I'll call this `The Great Gatsby Bootcamp` and then down below.
I also set up a `date` right here, `2019 4/4`.
Then we can just put a little bit of content on the screen.
So right here, I just launched a new bootcamp.
Then I'll set up a second header using to hash signs, followed by a space for a new section.
I'll call that topics covered, then down below.
I'll just list those out.
So I have Gatsby as the first one.
I'll go ahead and put `GraphQL` in there and last up is `React`.
So there we go.
We have some `frontmatter`, and we also have our blog posts content itself with a couple of things for markdown that should end up becoming different in terms of how it looks on the screen.
I would expect this to be a small paragraph and this to be a large header.
Now let's go ahead and do the same thing for the `React` post.
So right here we want to set up that `frontmatter`, the `title` for this one can be something simple, like `React`, and I'll set the date to an earlier date.
So right here I'll use `2019 the fourth month` but the `second day`, so two days ago, then allowed the content below.
In this post, you'll learn `React`.
Perfect.
So what do we have? We have a blog two posts, The Gatsby Post and The `React` Post.
What we need to do is figure out how to get this inside of Gatsby, because once it's in there, we need to transform it from markdown to `html`.
And we need to get that rendered to the screen.
Step one, though, is to tell Gatsby that we're now sourcing content from an external source.
It's coming.
Not from `sitemetedata`.
Not from a CMS, not from third party API.
It is coming from the `filesystem`.
Everything we need is right here in the Posts folder.
There's a plugin that's gonna let us get that done.
Let's head over to the browser and go back to the Gatsby site.
If we scroll up a little bit.
We're gonna head over to the plugins page, and we're gonna use the search bar to just search for source right here.
We're going to see all of the from an external source.
For example, Big commerce, a post Greste database Custom API, Instagram, Google Photos, video trail.
Oh, and more.
Now, in this case, we're not trying to source from any of those are content lives on the `filesystem`.
So we're trying to source it from the `filesystem` right here.
`source-filesystem` is going to bring up the `gatsby-plugin-react-helmet` going to allow us to pull those markdown files into Gatsby.
Then a little bit later will use another plugin to convert them for markdown to `html`.
We can actually render to the screen.
Let's get started, though, by adding this plugin into our Gatsby project and getting it configured.
So over here we're going to shut down our current development server.
I'll use clear to clear the terminal output, and we're going to install that new plug it.
So `npm install`.
That is `gatsby-source-filesystem` at the latest version 2.0.28.
I'm going to run the command.
It is going to set that up, and all we need to do is enable it by adding it to our `plugins` `array` over in the `gatsby.config` file.
Now, we've only worked with plugin before, and it didn't require any customization.
I simply listed out its name as a `String`, and that was enough to get the job done.
With the `filesystem` source plugin, there are a few options we have to provide, so the set up looks a little bit different.
Let's add a second item onto the `plugins` `array`, and this second item is not gonna be a `String`, it's actually gonna be an `object`.
Now, when we set up a plugin as an `object`, we still have to provide the plugins `name` and we do that via the `resolve` property.
So right here as the value for `resolve`, we type in the plugin's `name` that is `gatsby-source-filesystem`.
And there we go.
This is identical to what we have above.
The only advantage is that now we can expand on that `object`, adding what the `filesystem` plugin needs, which is an `options` `object` on `options`.
We have to provide two things.
Both our `Strings`.
First up is a `name` we can pick `src` for this.
And the second is the `path` to the directory on the `filesystem` that we're trying to source our content from.
So right here, that's `path`.
And we're gonna use a `template string` to get the job done.
To start off, let's enter plate a value that is `__dirname`.
If you're not familiar, this comes from `node.js`and remember, this is a `node.js` file.
That's why we're using `module.exports` instead of the export syntax and after `dirname`.
All we have to provide is `/src/`.
So, with just this little bit of set up, we're now telling Gatsby to source content from the `filesystem`.
This includes everything in the `src` directory which would also include our markdown posts.
Now that we have this in place, let's start up that development server once again.
So down below, `npm run develop` and what we're gonna do is head over to `GraphQL playground` and I want to take a look at exactly what's been added with the addition of this plugin because there are two new queries we now have access to.
So over in the browser we'll go back over to the playground and give things a quick refresh.
If we head over to the docs, we're going to see we have two new queries that did not exist before.
We have a file for fetching an individual file, and we have all file for fetching multiple files.
Let's go ahead and use `allFile` to explore some of the files in our project.Right here, under type details, We can see we have `edges`.
That's what we want.
`edges` makes it possible to perform pagination.
And in there we have access to `node`.
Node represents an individual file.
And here we have a bunch of information about the file that were currently requesting we could request it's `size`, the `extension`, the `absolutePath` when it was created, the `dir`, the `name`, all sorts of interesting things show up inside of here.
Now, remember, this did not exist before because we were not sourcing content from the `filesystem`.
now that we are, we can actually use that right here in `GraphQL playground`.
And that's exactly what we're gonna do.
So I'm going to remove our current query by removing everything from inside of it, and we're going to use `allFile` and from there as mentioned, we're going to grab `edges`.
And for each `edge`, we have the `node` and in the `node`, we have access to whatever we want about that file.
Let's go ahead and grab the `name` this files name were also going to grab the `extension`.
And finally, I'll choose to grab the directory as well using `dir`.
Now, if I go ahead and run this, we're going to see a list of every single file in our source directory with these three pieces of information.
So here I have about with the JS extension that's sitting in the pages folder, that's correct.
Below that, I have `blog`, `contact`.
I have our `index page`, the `header component`, the `footer`.
I have our CSS files in there as well.
And if I scroll to the bottom, I can see that amongst those other files.
I have my Gatsby markdown post right here and down below.
I have my `React` markdown post.
So now we are correctly sourcing content from the `filesystem`.
From here, The question is, how do we specifically target these markdown files? And how do we take their contents and convert them into something that's useful for us inside of `React components`? So this is just step one of about three steps to getting the markdown blog posts and running.
In the next video, you're gonna learn how to transform the's markdown files into `html` you can actually use and render.
I'm excited to get to that, so let's jump right into the next one.

<a href="//af.moshimo.com/af/c/click?a_id=2155533&p_id=969&pc_id=1263&pl_id=13856&guid=ON" rel="nofollow"><img src="//image.moshimo.com/af-img/0304/000000013856.gif" width="728" height="90" style="border:none;"></a><img src="//i.moshimo.com/af/i/impression?a_id=2155533&p_id=969&pc_id=1263&pl_id=13856" width="1" height="1" style="border:none;">
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

