---
title: "4. Creating Shared Page Components"
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

<a href="//af.moshimo.com/af/c/click?a_id=2155533&p_id=969&pc_id=1263&pl_id=13856&guid=ON" rel="nofollow" target="_blank"><img src="//image.moshimo.com/af-img/0304/000000013856.gif" width="100%" height="auto"></a><img src="//i.moshimo.com/af/i/impression?a_id=2155533&p_id=969&pc_id=1263&pl_id=13856" width="1" height="1">

<div style="position: relative; padding-bottom: 56.25%;">
  <iframe 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=2158"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>


You're Gatsby site currently has four pages, and the content for those four pages is completely unique.
There is no shared content.
We type out everything.
The page should render in the component for that page.
Now, this works really well for unique content.
But think about things that are shared across multiple pages in your sight, like a header or a footer.
This is not something we want to have to type out for each and every page.
We're gonna have duplicate code all over the place.
Instead, we want to create a separate `React component` that all of these pages can use and render.
And that's exactly what we're gonna do it in this video.
Together, we're going to create a footer that will show up at the bottom of every page on our site.
Then, as your challenge for the video, you'll create a header for these site pages with a shared navigation.
So it's really easy to access all of the content on the site.
So let's get started together with the footer to get started, we need to create a new file for a new `React component`, The footer.
Then, once we have that component in place.
All of these pages can import it and use it where they like at the bottom of the page that will give us a shared footer.
Now, this new component file should not go in the source pages directory.
Since we're not trying to create a new page, we're just trying to create a component that can be rendered on every page.
So to do that, we have to start by creating the components directory and from there we're gonna go ahead and create `footer.js`.
This will be the footer component.
Now the Components directory has no special meaning.
The files inside of here aren't going to do anything unless they're imported and used somewhere else.
And that's exactly what we want now to stay organized.
I'll put the footer all the way over here on the right.
Let's go ahead and create the component.
I'll start by importing, `React` from `React`.
And once we have that in place, we can create a new constant called footer.
And that's where I'm going to store my functional component and I'll set up the content I'm going to render.
In this case, it will be the footer element as the root element.
And right inside of there, all I'm going to do is add a paragraph and I'll put in a little text like `created by Andrew Mead`.
You can use your name there, then up the copyright information.
So Copyright 2019 now on a Mac to generate that symbol, that is Option `G`.
I'm not sure what it is on other operating systems.
You could always type out the full word copyright.
The last thing to do is to export the component from this file otherwise will never be able to access it.
So export as the default export footer.
And there we go.
Everything in this pile is done.
We can now import and render this component on the various pages for our site.
Let's start with the one page we already have up.
That's the contact page right here.
I have the contact page component to start.
I'm going to go ahead and import the footer, so I'm importing the default export, calling it footer, and I'm grabbing that from a file relative to this one.
So I'm going to start off with dot,.to get out of the pages directory, where the current file lives.
Then it's `/components`.
Since I'm looking for a file in there and it's called Footer leaving off the JS file extension.
Now that we have the footer component imported, it can actually be used on the page.
And in this case it's going to make sense to put the footer at the bottom where it belongs.
So right here just before that closing `</div>`.
I'm gonna render the footer component now if I save things, What do I see in the background? I can see that my contact page does have the footer, which is a great start using `React component`s, were able to compose our pages, and nothing we're doing here is Gatsby specific.
Here we're just using the fundamentals of `React`, so I'll do the same thing for the about page importing the footer from We're going out of the pages directory into components and there we have Footer and I'll copy this line to the clipboard so I can use it for my other files right here.
Before that closing, `<div>` will render the footer component and then let's check out the about page so I head over to `/about` and right here I can see the footer is showing up, which is great.
Now let's take this over to the other two pages, `blog.index`.
So for blog posts paste, that import statement in then just below where we have that closing `</div>`, that will be footer to render it.
And finally, for the home page.
So right here importing the footer component and rendering at near the bottom of the page content.
Perfect.
The last thing to do is to check those two pages the blog posts page and the home page.
I'll go to `/blog`.
The footer shows up, I'll go to just the root and here the photo also appears.
Now we have a single place to manage the footer content.
And if we wanted to update something like the year, I would simply type it in, save the file.
And now that change is gonna be reflected on every single page for the site, which is exactly what we want.
All right, I'm going to change that back over to 2019 and now it's time for you to do something similar, but for the page header.
So let's talk about what you're gonna do for this challenge.
The big picture goal is to create a shared page header.
So step one set up a header component.
That component should render a site title.
So a title for the entire site and it should include links to all four pages.
So this header component is going to contain our main navigation.
Now, don't worry about creating the perfect `semantic `html`` structure.
You can just get all of this content show into the screen.
And as we work through the challenge solution, I'll go ahead and set up the `semantic `html`` markup down below.
Next up, make sure the component new create gets rendered at the top of every single page for the site, all four of them Then test your work.
You should be able to see your navigation bar, and you should be able to click between all of the links to navigate to the four pages on your site.
So take some time to knock this out, test your work when you're done, come back and click play how that go.
Let's get to it by first creating the new component.
So this is gonna be a new component in that components directory called something like Header.
So that's `header.js` And in here, we're going to import `React` since we're gonna end up using some `JSX` to render the header component.
And I'm also going to import that named export link from Gatsby.
As I do want to set up the navigation links as well down below, we can actually create the footer Constant and set up our function for the functional component.
Now, I mentioned that your job was to just get the content rendered to the screen and not to worry too much about the correct semantics for this sort of thing.
In this case, though, we will work through that together.
So I'm going to start with the `<header>` element.
From there.
I'll set up an `<h1>` with the text of `Andrew Meat`, which I'll use as the title for this site.
You could have used any text you wanted to.
Then we'll focus on the navigation menu.
So for this we want to start with the `<nav>` element.
Then we're going to create an unordinary list(`<ul></ul>`), and in there we'll have a list item for each and every link.
So this is the basic structure we're gonna use.
And the first list item will contain our first link, in which case I'll just link to the home page.
So right here a new instance of the `Link` component.
The text is home.
And where are we going to? We're going to `/` down below.
I can set up another list item with a second link for this one.
I'll go to the blog posts page, though the order of the links was not important as long as all four are showing up, Then from there it's about followed by contact.
So I'll knock out about first that is going to go to `/about` and finally setting up the list item for our last link, this link going over to the contact page.
So to `/contact`.
So this is the basic structure for our header component.
The end result is our site title and four links showing up to the screen.
Now I actually called this footer.
That is a mistake.
I should have called that header just down below.
Let's go ahead and export our new component.
So  `export default` header and all we need to do from here is import this file and render it somewhere on the site.
And in this case, I want to do that for all four pages.
So that is step number two.
I'll start with the contact page.
So right here.
Actually, I'm going to start with the page showing up, which is the home page.
So right here in `index.js`, I'll start by importing the header from that's `.
components/header`.
And I'm going to copy this line to the clipboard so I can use it in my other page components just down below.
As the first thing I render, I'm going to render the header component.
And if I say if the file, I should see that showing up and it is here I have home blog about and contact.
And if I click one of those links like the blog think it brings me over to the blog posts page, which is awesome.
Now the blog posts itself doesn't have a `<nav>` menu, so let's fix that here.
I'll paste in my import statement.
I'll set up the header component and I'll do the exact same thing for my other two pages as well.
First up is about rendering the header and last up is the contact page perfect.
Now, once we have this in place will have that shared navigation.
And the final thing we need to do after saving the contact file is to test our work.
So right here among the blog posts page, I'll go to home than blog about then contact.
And we can see that on each and every page we have our header showing up, up top and down below we have our Futter.
So when we're working with Gatsby, we can compose our site of various components exactly like we're able to when we're using `React` in any other `context`.
The only important thing to remember is that if we're creating a `React component` that's not meant to be an entirely new page that should not go in the source pages directory.
In this case, we're putting it in the source components directory.
But this directory could be called anything you'd like.
Its name is not important.
All right, That's where we're going to stop for this one.
I'll see you in the next lesson.

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

