---
title: "5. Creating Gatsby Page Layouts"
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

<div style="position: relative; padding-bottom: 56.25%;">
  <iframe 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=2894"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

In this lesson, you'll be taking your pages to the next level by creating a single page layout component.
So you can think of this video as a continuation of the last one.
In the last video, we set up our header and footer, and in order to render them on every page, we had to import them on every page and then manually set them up in the correct position four times.
Now that was four times for four pages.
As our pages grow and are layouts shifts, that's going to require us to make even more changes to every single page component.
What we're going to do here is set up a universal layouts component that we can easily use to create a new page with just a couple of lines of code.
So let's see what that's gonna look like and how it's going to help us to start.
Let's create a new component in the Components directory, and this is something we're going to call `layouts.js`, and eventually this will be the only component that our pages need to import in order to get up and running.
Now we're going to focus on `layouts.js` and `index.js`.
If we can get the layout to work here, it'll be really easy to add it to the other three pages.
So to start, let's create the basic structure of the layout component right here.
We're going to start by importing `React` from `React`.
Then we'll set up the layout constant right here.
It's a functional component where we return some `JSX` and I'll start off with a single root.
`<div>`.
Now down below will go ahead and export this component.
So that's going to be  `export default` layout and we're done.
Well, we're done for now.
Let's actually try to use this over in `index.js` and see what happens.
So here's the big picture goal.
I want to be able to remove all of the components that are used on every page and just use that single layouts component instead.
So that's the only one I'm gonna end up importing.
How important layouts from.
`/components/layout` and then we're gonna use it down below.
Now here's what that's gonna look like.
I'm going to recreate the return statement and I'll remove the duplicate one in just a second right here were actually going to start by rendering layouts and the stuff we want to put on the page.
The stuff unique to the page, Because right inside.
So for us, what's unique While it's not the `<div>` or the header or the footer, it's just this stuff right inside.
So I'm going to copy those three elements.
I'm going to paste them into layouts, and this is the end goal of what we want now.
Currently, if I remove that duplicate return, this is not going to work as expected.
I'm going to save `index.js`.
I'm going to navigate over to the home page and what do we have? We have a blank screen.
That's because we're passing stuff to the layouts component this stuff right here.
But it's not actually rendering it.
So what is it rendering? It's just rendering an empty `<div>` well, in `React`, we get access to the content inside of a component via the Children prop, and that's exactly what we're gonna use to get all that other stuff rendered.
So right here inside of `layouts.js` we get our `props` and we're going to use one right here.
We are going to render `props.children`, and I'm just putting that inside of `{}` to reference that `JavaScript` variable.
Now what is `props.children`? Well, it's the `JSX` passed in.
So it is `JSX` for these three elements.
Now all I'm gonna do is save `layouts.js` over here.
What do we see? We see that on the home page.
We now have our home page content, which is a good start.
From here.
We can customize the layout component to add stuff that's going to be shared on all pages like that header and footer.
So I'll import the header from right here.
That is `.
header` and I'll do the same thing for the footer.
And then finally, we're going to use both of those now the header is going to go just before the individual page content, so I'll put that right here, and the footer is going to go just after that content exactly like we had before.
The nice thing, though, is that if I want to adjust the layout further, I no longer need to go into the individual page components Instead, I just adjust the layout component, which now maintains the page layout.
And here we go.
Our `index.js` file is much simpler.
It's concerned with a lot less.
And over here we have the exact same stuff rendered to the screen that we had before.
I have my header with my `<nav>` links and down below.
I still have my footer as well.
So using the layout component is just going to make our lives a whole lot easier.
Now, let's go ahead and integrate that into the other three pages for the site.
Over in `Visiual Studio Code`, we can start with the blog posts page.
So right here we no longer need to import.
Those two things were just going to import layout.
And I'll copy that line to the clipboard for now, then down below, we have to use it.
So right here we need to restructure what we have.
We render the layouts and inside of there, what do we put? We put what we have right here.
So I'm gonna move that just inside and I'll delete the older I had before and there we go.
The blog posts pages now also powered by that layout, having the header and footer set up behind the scenes.
Now let's quickly do the same thing for the other two pages.
So right here, pasting in the layouts import, then setting that up down below and moving the unique content for the page.
So this stuff right here just inside and deleting the oldestructure we had perfect last up is the contact page.
So once again, using the layouts and putting the unique content just inside.
Excellent.
So in the last two videos, we had to do a little bit of restructuring going into each and every component file, which can be a little bit of a pain at first.
But now it's done.
All of our pages are powered by the layouts, and no longer are we gonna have to move into individual pages and adjust the same thing in every page.
If you find yourself doing that, it's probably something that needs to be broken out into a standalone component instead.
So over here, let's just go to the about page and the contact page to make sure everything is working.
And there we go.
We have a basic static site created and powered by Gatsby now were not done, not by a long shot.
There's a lot more to cover, and what I want to focus on in the next few lessons is styling your Gatsby sites.
So let's go ahead and dive right into that, starting with the next lesson.

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

