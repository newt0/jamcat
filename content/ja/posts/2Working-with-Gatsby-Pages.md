---
title: "2. Working with Gatsby Pages"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=890"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

Welcome to the second lesson for `The Great Gatsby Bootcamp`, where you're gonna learn how to work with Gatsby pages.
Now, in the last lesson, we saw that by default we had to this source pages directory and in there we had a single file for the single page on our site.
It was `index.js` which exported a component.
That component rendered a little bit of text.
And that's exactly what we were seeing when we visited our static site over in the browser `The Great Gatsby Bootcamp` showing up in both locations.
So when it comes to page creation, the source pages directory is where Gatsby looks when it's figuring out what static pages your site needs.
So all of the files we put inside of this directory are going to represent me pages for our site, such as a home page and about page a blog posts page and anything else you might need and that will all depend on the type of site your building to get started.
I'd actually like to empty this file completely and build the page up from scratch.
So right here it's going to start off the same one thing will do in all of our pages is `import react`.
That's necessary.
If we're gonna use `JSX` and `React` to something we can import as it's already installed as part of our Gatsby Project from here, what we're going to do is create our `React component` for this page as a standalone variable.
So, `const index page`, you could pick whatever name you like.
This is just the one I'm choosing, and what I'm gonna do is set this up as a function.
This function is our `React component`, and all we need to do from here is return some `JSX` containing what should get rendered When this component gets rendered right here, return in `()`s().
I'll set up a `<div>` and in there I'll add an `<h1>` header element with the text value of Hello.
After that, I'll add an `<h2>` and add a little bio about myself.
Something like `I'm Andrew, a full stack developer living in a beautiful Philadelphia`.
Perfect.
Now that I have this in place, I can go ahead and make sure that this component gets exported like we were doing before.
So  `export default` followed by the name index page.
Now there's no need to create the separate variable and then export it.
But this is definitely the approach I prefer.
I find it a lot easier to manage my code.
So with all of this in place, we now have a new version of the index page.
If I save the file, I can see that Gatsby compiled a new version of the site.
And right over here, we have everything showing up.
`Hello, I'm Andrew, a full stack developer living in beautiful Philadelphia`.
So this is all it takes to create a page.
We add a file to the source pages directory.
That file is a `JavaScript` file which exports a `React component`.
Now, if you're not familiar with the basics of `JavaScript` or `React`, those aren't topics I dive into in the bootcamp, though I do have courses for both of those.
I have the modern `JavaScript` bootcamp, which covers everything you would need to know about `JavaScript`.
And I have [The Complete React Developer Course](https://www.udemy.com/course/react-2nd-edition/)  which dives deep into `React` and that entire ecosystem, if you're interested in either of those, I'll include links on the screen and in the description down below.
So what exactly is happening when Gatsby generates our site? It starts by looking in that source pages folder to figure out exactly which static pages it should create.
In this case, it sees we only have a single file, which means our site is only gonna have a single page.
Now, the pages you create should indeed be `JavaScript` files, and those files should export `React component`s.
Gatsby will render that `React component` to figure out what should get showing on the page.
That's exactly why we're seeing are two bits of text when we visit the root of our site at `localhost: 8000`.
Now, the name of the files in the source pages directory is also important.
In this case, we've called our file `index.js` This is similar to how `index.html` would be the default page for a website.
When you're working with Gatsby `index.js` in the source pages folder that is your home page.
So in this case, that's exactly why that content is appearing now to create a new page, all we need to do is add a new file to the pages directory and that's exactly what we're going to do right now.
In total, we're gonna add three new pages in this lesson.
Let's go ahead and get started by adding a blog posts page to the site.
So this is going to be a page where we will eventually show a list of all of the blog posts we've written To do that, we create a new file in the pages directory.
I'm going to call this blog posts.js And like we did with the `index.js` file, we have to export a `React component` which contains the content we want to render.
So let's get that done.
To start, I'm gonna import `React`.
Remember, we need `React` in order to use `JSX`.
And from there we're gonna set up our functional component.
I'll call this one something appropriate for the blog posts page like blog posts page.
I'll set this up as a function and I am going to return in the `JSX`, which contains the stuff I want to render in this case.
I'll also use a Route `<div>` and I'll set up a title and some text.
So the header for this page is going to be something like blog or my then down below.
We're going to set up a paragraph element and right here I'll just say something like Posts will show up here later on.
And that's true.
A bit later, in this bootcamp will actually get a dynamic list of posts showing up below the title.
Now the last thing we need to do is export the component.
It's an important step.
Otherwise, Gatsby cannot get access to dysfunction to actually render the page right here.
That would be blog posts page exactly as defined up above.
Now we can go ahead and save the file.
And over in the browser we have access to eight brand new page.
This page lives at localhost on Port `8000/blog`, where this part of the URL after the `/` is the name of the page file.
So in this case, I called it blog posts were here.
That's why we have access to `/blog`.
And when we visit that page, what do we get? We get our component content.
I have my header blog and I have my paragraph text just below creating new pages with Gatsby could not be easier.
All you have to do is at new a `JavaScript` files to that pages directory.
Now this bootcamp is not just you watching what I'm doing.
I've also included challenges which require you to use what you've learned to continue to build on the site so down below.
Let's talk about what I'd like you to do.
Then I'll give you some time to go off and do it before we work through these solution together.
So the big picture goal is to create an about page and a contact page so you'll be adding two new pages to our site by the end will have four in total Step one.
Create that about page.
You can include a page title and a bio.
Use an `<h1>` for the page title and a paragraph or two for the bio.
Then you're going to create the contact page for that one.
Include a page title and your contact details as well.
Now, when it comes to the file names, which end up being the Earl's, you can just use about and contact.
Finally, test your work.
Once you have that code in place, actually visit those girls in the browser and make sure you see your pages showing up.
So take some time to knock this out, test your work, pause the video When you're done, come back and click Play How that go.
Let's get to it.
Step one.
I'm going to create a new file in the pages directory for the About page.
Now I'm going to go with about as the URL.
Though maybe you wanted to do something like about me or even just me.
In this case, `about.js`.
I'll start by importing `React` from `React` and then we'll set up our components.
So a new constant about page or something similar, we'll set up the function itself and will return the necessary `JSX` like I had with my other pages.
I'll have a root `<div>` with all of the content right inside.
I'll have an `<h1>` that says about me.
Then down below, I can add a paragraph to the page as well, and I'll say something like I currently teach full time on you, Timmy perfect.
So once we have this in place, all we need to do is export that component  `export default` about page and we are halfway done.
Now that we have the about page created, let's go ahead and move on to step two and create that contact page.
So once again, we need to create a new file in the source pages directory.
I'm gonna call this contact so that would be `contact.js`.
And then here we move through that same process importing `React` so we can use our `JSX`, setting up a constant for that component contact page and then is setting up the component itself and returning the `JSX` that should get rendered on the page.
Now for the `<h1>`, I'll use the text value of contact.
What's not contact page? Then down below, I'll set up a paragraph analogue.
Just say the best way to reach me is via my Twitter, which is `@Andrew_J_Mead`.
Perfect.
Actually, I'll say via that on Twitter.
Excellent.
So now that we have this in place once again, just need to export the Component Export Default Contact page and we are done, we have are two new pages which just equals a new `Javascript` file that exports a component now Let's go ahead and older move.
Those challenge comments will make sure everything is saved and we'll move on to the final step, which was to test our work.
So first up, I'll swap out forward, `/blogposts` or `/about`.
I visit that and I see my about page, which is awesome.
From there.
I'll visit my contact page right here.
That shows up with the contact details I specified.
So at this point, we now know how to create pages with Gatsby.
The next thing we want to do is figure out how we can link between those pages.
It's already getting a little old manually typing URLs in the browser bar.
So let's jump right into the next video and learn how we can properly link between our pages when using Gatsby.

<a href="//af.moshimo.com/af/c/click?a_id=2180365&p_id=2520&pc_id=5570&pl_id=32577&guid=ON" rel="nofollow" target="_blank"><img src="//image.moshimo.com/af-img/1916/000000032577.png" width="100%" height="auto" style="border:none;"></a><img src="//i.moshimo.com/af/i/impression?a_id=2180365&p_id=2520&pc_id=5570&pl_id=32577" width="1" height="1" style="border:none;">


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

<a href="//af.moshimo.com/af/c/click?a_id=2233170&p_id=898&pc_id=1106&pl_id=11638&guid=ON" rel="nofollow" target="_blank"><img src="//image.moshimo.com/af-img/0262/000000011638.jpg" width="100%" height="auto" style="border:none;"></a><img src="//i.moshimo.com/af/i/impression?a_id=2233170&p_id=898&pc_id=1106&pl_id=11638" width="1" height="1" style="border:none;">

