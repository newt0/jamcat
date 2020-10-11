---
title: "7. Styling Gatsby with CSS Modules"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=4009"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

Welcome to Part 7 of `The Great Gatsby Bootcamp` in this one will continue to talk about styling our Gatsby sites, and the focus is gonna be on CSS modules.
CSS modules are supported by default in All Gatsby projects, and it seems to be the preferred way to style Gatsby sites as it's covered extensively in the official Gatsby documentation.
Now with CSS modules, we're not learning a whole new language.
It is just CSS with a slight tweak, making it really easy for us to create complex Web applications without complex styles.
So let's go ahead and get started with the basics.
Let's get started by closing all open editors, and we're going to focus on just one of our components.
For the moment, that's gonna be the header component.
We want to add some styles to this, making the header look a little bit nicer.
Now to add of those styles will be creating a new style sheet right here in the components directory.
I'm going to call this `header.css` and in here will put the styles specifically for the header.
So, as an example, let's say we want to style the links.
Here we are targeting all `<a>` elements, and then we'll just set their color equal to a nice gray right here.
The pound sign followed by the hex code.
I'll use the number 96 times for that gray color.
Now, if we save these style sheets, none of these tiles get applied, since this isn't being imported anywhere.
So let's fix that in the header component.
We're going to import that style sheet just like we did in the last video when we imported this style sheet into the layouts component.
So right here in port, I'm going to import the following file that is `.
header.css`.
Now, if I go ahead and save the component, we can see that all of the links in our header are styled, which is a great start.
One thing you'll notice, though, is that it's actually all of the links on the site right here.
The link to my Twitter profile that's styled in gray.
And if I go to the home page, other links like the `Contact Me` link are also showing up in gray.
So it's important to note that just because you're importing a style sheet in a particular component doesn't mean those styles are scoped to that component.
In this case, we are selecting all `<a>` elements on the page, not just those that exist inside of the header.
So this is an important thing to note now.
What's the solution if I want to just target the links in the header? Well, there are a lot of different things we could do.
A simple approach without CSS modules would be to target by `className` something like Link.
Then I can use that `className` wherever I want to apply those styles.
So inside of the header component, I could add `className` on to the link.
This is the `React` prop `className`, and I'll just set this equal to the class I picked Link and over here in the browser, we now have that gray home link.
Now this is a great start, but it's important to remember that those styles air still globally accessible.
So if other components in our large application also want to style their links and they use a generic `className` like `link`, we're going to run into a problem where we have styles for multiple files overriding each other, leaving us with a big mess Now.
The solution before CSS modules existed was to do something like using naming convention a naming convention that would allow us to create longer, more complex `className`s, though they were more likely to be unique.
So something like header link instead of just Link.
Then, if I wanted a links styled in the Footer, I could use something like Footer, Link and so on.
So we can't use those generic `className`s because there's a high chance of conflicting styles, and the solution is to have a whole bunch of complex `className`s.
That's not ideal either.
The solution we're gonna use to solve this problem is CSS Modules.
CSS modules make all of the class selectors in the module style sheet locally scoped, which means that we have to manually import them and use them, and we'll see what this means in reality.
In just a second.
For now, let's notice one thing we have are two files saved and that home link is gray.
All we're gonna do is enable this file to be a CSS module.
By changing its name, we're gonna change the file extension down below.
I'm going to rename it to `header.modules.css`.
Now, you could also use `header.module.css`.
If you did not want to use the CSS syntax, though in this case, I'll keep it in place.
Now, right away, our app crashes and that's expected.
We're trying to import a style sheet that no longer exists.
So let's adjust the name here `.module.css`.
Now, if I save both files, it's no longer crashing.
But you'll notice that our link is also no longer gray.
I have the `className` link right here, and I'm also targeting it over here in this file that's loading.
So what's going on, as mentioned earlier when we're working with CSS modules are class selectors.
They are no longer globally applied.
Instead, there locally scoped.
It's something we need to import as part of the import statement and then apply directly to that element.
So let's see what that looks like.
The first thing we need to do is change our import statement.
I'm going to comment out the old one and adding new one just down below here on importing the default export.
I can call it whatever I want.
I'm going to call my `headerStyles` and we're grabbing that from the same file.
`.header.module.css`.
So when we're working with a CSS module, we actually get a default export.
This is an object which contains properties for every class we've defined in the module.
In this case, we just have one link.
So what we have is an object with a single property link.
We can use that property to apply that style.
So no longer are we gonna have a static string for the `className`.
It's gonna be dynamic.
So `className` equals inside of `{}`.
The following `headerStyles` link where link is the name of the class chosen over here.
Now, if we go ahead and save the header component will see that once again our link is gray.
Everything is back to working as expected.
And the great thing about CSS modules is that we're being explicit.
I'm explicitly loading in a set of styles from a specific file and I'm applying them directly to the element.
So there's zero chance of some sort of global style coming in and messing things up from another component, and that's what we want.
We want our components to be self contained and easy to update and work with.
So now that we have this in place, let's take a look at what exactly is happening over in the `html` for the site.
I'm going to open up the chrome developer tools in the browser.
You can always go to the menu mawr tools, developer tools to find them.
And here I'm looking for the Elements panel, and they'll use this selector by clicking it and picking an element on the page.
I'm going to click that home link and it's pulled up down below.
Now here we can see.
We do have the class attributes and there is a single class inside of there, but it's not something we ever created.
It is header module, followed by Link, followed by a random series of characters.
This is the `className` generated by the CSS module that keeps our styles unique.
Even though we're using a generic `className` like `link`, we could target links and other components in our project by using the exact same selector without any chance of overriding the ones in the header.
So now that we've seen how CSS modules actually function, let's continue working with them to style the rest of the site to get started.
I actually want to add a CSS module for the layouts component.
So right here in the Components directory that's `layout.module.scss`, and we're going to crack open the layout component as well.
And I'll just stay organized up above with the header stuff, then the layouts stuff.
Let's get started adding a few stylist of the layouts, allowing us to center the content on the site.
So it's not all pushed up against the left hand side.
Let's start with a new selector selecting the container class, and right here we're gonna set up a few basic styles, starting with the margin.
I'm going to use zero and auto to center things left to right, and we're also going to set up a max with for the site.
I'll use something like 750 pixels and finally a little bit of patting on all four sides, so the content isn't pressed up right against the edge of the browser right here.
One R E M should get the job done.
Now we have to import this module in the layout component and actually use those styles right here.
Import layouts, styles from `.layouts.module.scss`.
And once we have that in place, we can apply that to our `<div>` right here.
So this one is gonna have a `className` equal to on the layouts styles object.
We have that container property.
Now, if I go ahead and save things, we can see all of our content has disappeared because it's now centered in the browser, which is obviously a nice step in the right direction.
Another thing we're going to do with the layout is set up a sticky footer.
So right now, the footer kind of gets pushed up the page, especially on shorter pages.
It would be nice if it was always at the bottom of the site to get that done.
The first thing we're gonna do is create another `<div>` inside of the layout component.
So right here, let's set up that new development and we're gonna put the header and the page content inside of there.
The footer is gonna be just outside of the `<div>` and this is a common `html` structure for a sticky footer.
Right here will end up applying a few styles to this `<div>`, let's get started over in the inside of the container we to add a few new styles in order to get everything working.
The first thing we're gonna do is set up `display` setting `display: flex:`.
We're going to enable `flexbox` here and the `flex-direction` for the container is gonna be vertical.
Since we want the content and the header above the footer not left and right.
So right here we're using column as opposed to the default value, which is Roe.
I don't want the footer on there, right, I want it on the bottom.
The last thing we're going to apply to the container is `min-height` setting that equal to `100vh`.
This is the viewport height.
So here I'm setting the container height to the screen height.
That's the minimum height.
So it could always get bigger on longer pages.
And that's what we want.
Onley.
Other thing we need to do is style that new `<div>` we created I'll set up a class content for this, with `flex-grow` set to one that's going to allow that container this container right here to grow as needed, leaving just enough space for the footer in place.
So the `layout-module-scss` all done.
We have our styles in place over here.
All we need to do is apply the `className` prop to that new `<div>` layouts styles.content.
I save the program and over in the browser we can get See, we have these sticky footer in place.
So on the contact about blog posts page, that footer stays where it's supposed to.
Now, if the site content was shorter, it wouldn't be at the bottom.
Still, you'd still have to scroll to see it, which is exactly what we want.
So now that we have the layouts styles in place, let's go ahead and head back over to the header as we are gonna add a few more styles here.
So inside of the header module, let's get to it First up, I'm gonna add another class of selector for header to and a little more space for the header right here.
Patting is gonna be one aria on the top zero on the left and the right and three r e m on the bottom.
So we're just trying to put a little space between the header content and the other stuff on the page.
Now, if we had over to the header component, we can apply that right here.
So `className` equals That's gonna be `headerStyles.header`.
Perfect.
Now over in the browser, those styles should have taken effect and they did.
Perfect.
Now let's continue on to the `<h1>` shell in on the header.
I actually want this to be a link to the home page as well.
So what I'm gonna do is set up the `<h1>` and put a link right inside.
This link is going to have the same text I had before.
So the text value will still be Andrew Mead and we're going to send them to the home page.
So this is like clicking a sites logo and going to the home page.
I want to be able to do that same thing here.
So if I'm on the contact page, I click the name and I go to the home page.
Now, clearly, we have to add some styles to that, and that's exactly what we're going to do.
So in the header module, we'll set up a new classes selector for the title.
And right here we're gonna do a couple of things first up, setting the color equal to black.
That is the hex code with six zeroes.
Then we're gonna set the font size equal to `3rem`, making it a little larger and finally setting `text-decoration` to `none`, removing the underlying effect we get with links by default.
Now let's apply this to that link.
So right here, `className` equals `headerStyles.title`.
I saved the program, and over in the browser we can see that this is still a clickable link, but it's now styled to look like regular text, and you could swap that out with a company logo or whatever you wanted to.
Next up, let's focus on styling the navigation list so we can get rid of those bullet points and put the items left to right as opposed firm.
The top to bottom approach, which we currently have in place to style that will be styling are a Nord and list right here in the header module, a new class selector `<nav>` list, and we're going to apply just three styles.
First up `display: flex;`.
This is going to stack those items left to right, which is what we want.
I'm also going to set up list style type, sending unequal to none That's going to remove the bullet points which we don't want.
And finally I'll set `margin: 20;` to clear the default margin values that are lists typically get over in the browser we can get.
See that none of our changes have taken effect.
I forgot to apply that in the component.
So right here, `className` is going to equal `headerStyles.navList`.
So here we have a camel cased version of what we typed out in the CSS.
And our styles are applied perfect.
The next thing we're gonnado is at a few more styles to the individual `<nav>` items.
We added just one as an example, but we're gonna add a few more right here.
I'm also going to change the selector.
I'll change it from link over to something like `<nav>` item.
Now the color is going to stay in place.
I'm also going to adjust the font size, setting it 2.9 r e m a little bit smaller than it currently is.
Also add a margin on the right so the items aren't jammed right up against each other.
1.3 R e m on the right and finally, text decoration setting that equal to none once again to remove that underline effect we were getting.
Now we can use this for all four links in the navigation.
So right here, I'll take that  first one and I'll swap it out from link over to nab item and down below.
I can just copy this `className` definition for the other ones.
Onedo and three.
And I can see I have a little auto formatting from my `Visiual Studio Code` editor.
Perfect.
Now let's save the program over in the browser.
What do we get? We have a nice styled header.
I have my links to My page is sitting below the header text, which is also clickable.
Now when we're using CSS modules, we can get still use pseudo classes or anything else we might want to use.
So let's say that on hover we want to adjust the color of the link item we can get.
Do that `<nav>` item, Then colon hover.
So when someone hovers over that with their mouse will just change the color to something a little darker right here.
Hex code is 66 times perfect.
Now we contest that out over in the browser.
I have my links showing up.
Ah, hover over them and I can see they're getting a little bit darker, which is exactly what we wanted.
One more thing we can do with the Link component is set up a `className` that should get applied when we're on that specific page.
So if I'm on the contact page, I could style this link differently, giving the user a visual cue as to where exactly? They are in the site down below.
Let's go ahead and get that done.
I'll set up something like `active-nav-item` for that and over.
Going to do is set the default color to something even darker.
This will be the number 36 times a nice dark gray.
Now let's actually apply that over in the header component.
Then we'll be all done for styling.
So over here we have `className` for all of the links.
If you want to set up a special `className` for when you're on that page, you use `activeClassName`.
So right here, I would be setting that too.
`HeaderStyles.active-nav-item` perfect.
So right here, just matching up with what I had to find over here.
Now let's take that definition and move it to the other ones we have just down below are other four links.
So add it to the blog.
I'll add it to the about link and to the contact link.
And once we have, all of those in place will be able to test our work right here.
I'm going to save the program right here.
I can see on the contact page and the contact link is darker than the others.
I go over to the about page that's dark blog posts home.
So now we have a nice navigation system, letting the user know exactly where they are on the site.
All right, that's where we're going to stop for this one.
Now that we have some styles in place, we're done with what I would consider part one of the bootcamp will recover the basics of creating a site with Gatsby in the next video, we're going to start talking about how we can get dynamic data into our site using Gatsby's `GraphQL` API.
So let's jump into that.

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

<a href="//af.moshimo.com/af/c/click?a_id=2233170&p_id=898&pc_id=1106&pl_id=11638&guid=ON" rel="nofollow" target="_blank"><img src="//image.moshimo.com/af-img/0262/000000011638.jpg" width="100%" height="auto" style="border:none;"></a><img src="//i.moshimo.com/af/i/impression?a_id=2233170&p_id=898&pc_id=1106&pl_id=11638" width="1" height="1" style="border:none;">

