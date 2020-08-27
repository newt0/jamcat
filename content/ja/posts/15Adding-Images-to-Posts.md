---
title: "15. Adding Images to Posts"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=11008"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

Now that we have post content rendered on our site, What I want to focus on in this video are two final things.
Before we move on to sourcing our content from the `Contentful` CMS, we're gonna focus on adding support for images in our posts, and we're gonna add a few final styles to make the post and the post list look a little nicer than they currently do.
But to get started, what I want to do is figure out how we can add images into our posts, and this is really going to require us to just install and configure three new.
Now, before we get to any of that, we need an image to actually put in one of our posts.
You're more than welcome to use any image you already have.
If you want to use the image I'm going to use, you can head over to links.mead.io board slash grass pick.
When you visit that Earl, it will redirect you over to this picture of some grass and we're going to save this image to the project.
So all right, click save image as on the desktop.
I have my Gatsby bootcamp folder.
And there we have the source posts directory.
And for the moment, I'm just gonna put this file right alongside of my two markdown files.
So let's save that file.
In its place, I can close that tab and over in `Visiual Studio Code`, we can make sure it's actually showing up inside of posts.
We have grass.PNG and right here we have our image.
Now we want to render that image in one of our posts, and I'm gonna put it in The Gatsby bootcamp post.
I'll put it right here just below that paragraph text and just above the topics covered list.
Now, to add a image to markdown, we used the following syntax.
It's an exclamation mark, followed by a pair of brackets, followed by a pair of `()`s in de `()`s.
We put the path to the image.
In this case, we're gonna have a relative path from this file to the image they're in the same directory, so that would be `grass.PNG`.
Then we can set up our all taxed for when we're unable to load the image, or for when someone's using an accessibility device like a screen reader.
We can just use grass for that.
So with this in place, we now have the finished markdown post.
And before we actually install and configure those three plugins I talked about, let's just see what we get in the browser right here.
We get our Ault text.
So by default, Gatsby doesn't know where you're trying to fetch the image from.
What we need to do is install and configure those three plugins to set up support for this sort of syntax right inside of our blog posts.
So to get started in the terminal down below, what I'm gonna do is shut down the Devitt server.
Use clear to clear the terminal output, and we're going to run `npm install`.
Now the first plugin we're going to install is `gatsby-plugin-react-helmet`.
Rehr E provides all sorts of tools for working with and processing images, and it's a dependency of the other plugins were going to use.
So this needs to get installed at the latest version, 2.0 point 32.
Next up, that is Gatsby-remark,-images.
And this is what's going to allow us to use images inside of our markdown posts when they're processed with remark right here.
The version for this one at 3.0 point 10 and the final one we're going to install is Gatsby Remark Relative images.
This is going to allow us to source images relative to the markdown bile.
So in this case, Stott /grass.PNG is going to correctly render the image right here and the version for this one at 0.2 point two.
Now we can go ahead and install all three of those and, well, that's running in the background.
We can head over to our `gatsby.config` file as we're going to need to make some pretty big changes to the plugins array.
Now, the first plugin we're going to set up is the sharp plug it, And that's going to go right here before we transform our markdown files.
So right here That would be the following Gatsby plugin sharp now.
No options are required for this, which is why I'm providing it as a string as opposed to an object up above.
Now, the other to plugins we installed are both remark specific.
We installed Gatsby Remark images and Gatsby remark.
Relative images.
Both of those actually get configured in the options object for this plugin.
That means we need to remove it from just being a string and switch it over to being an object and `resolve` `resolve`s that same plugin value.
So at this point, what have we done? We haven't added any new functionality, but now we do have a structure where we can set up options, since it's an object and not just a string.
And that's exactly what we're going to do.
So right here we're setting up an options object and on this options object were setting up a plugins array.
So these are plugins specific to the remark transformer, and this is all outlined in the docs for those specific plugins.
So if you're wondering how I knew the documentation can guide you in terms of how to configure things now, right here, what we need to do is set up both of those plugins like we would do with our main plugins array.
So the  first one is just gonna be a string as no options are required, that is, Gatsby remark, relative images and the 2nd 1 that's gonna be an object, as there are some options we want to provide.
So right here `resolve`.
This is Gatsby remark images, and we're going to provide an options object just down below.
Now there are only two options I want to provide, and the first is Max with.
So let's say I have an image that's 1920 by 10 80 a standard h D size.
The problem is that ah, you CSS and my blog posts, making sure that the blog never gets past 750 pixels wide so that images unnecessarily large for the `context` in which it's going to be used.
We can have our Gatsby site automatically resize it, using Sharp and our other plugins by setting Max with equal to a value.
In this case, I'll use 7 50 next up, I'm going to customize link images to original.
This is another option we have available, and I'm going to turn this off.
Otherwise, when you click an image in the post, it brings you over to the actual location of that image, and that's not really behavior.
I ever enjoy when I'm reading a blog posts.
Oh, I don't want it for mine and then we are done.
So we've configured our Gatsby site to use Sharp.
And then when we transform our markdown files, we have a couple of other plugins that makes sure the images get rendered correctly.
Now all we need to do is start up our server once again with `npm run develop` that's going to start up the debit server.
It's going to get the image, and it's going to make sure it actually gets included in the static site right here.
Let's just refresh things over in the browser and what do we get down below? We get `The Great Gatsby Bootcamp`.
We have our date, and then we have the post content.
The paragraph up above are nice grass image and topics covered down below.
So now when we have those plugins in place, we can add images to any of our posts by simply specifying them like we did here.
Now, one thing you can additionally do is organize your posts directory further.
Let's say that grass is specifically for The Gatsby Post.
It could get a little confusing.
If I have dozens of images inside of here, one thing I could do is create a folder for each post.
Something like Gatsby for The Gatsby Post.
Then I could move the markdown file and the image right inside of there.
I could even take this further, creating an images directory inside of there if I wanted to.
But in this case, now it's a little more organized.
I can, see the assets for The Gatsby post right there and for the `React` post down below.
So what, this in place? Our site should be working.
Once again, we have the exact same URL structure and functionality.
All we've done is we've organized that posts directory just a little bit more.
Now let's wrap this video up by adding a few styles into the mix.
One thing I want to do for the Post page is add more space between the bottom of the post and the footer down below as the footer kind of looks like it could just be some content for the Post.
So to do this, we're gonna work with CSS modules.
I'm going to start by closing down all open editors and we want to focus on the components directory.
We have our footer component.
There is no CSS module for that.
So I'll create it.
A new file in the components directory.
Footer, doc, module.s CSS.
And from there, all we're going to do is set up a single class selector for Footer and I'm going to set margin top equal to three r e m, which is the same spacing I use on the bottom of the header.
Now we can import this and apply it to the footer element right here.
So import footer styles from.
footer.module.s CSS.
Then we just set up our `className` down below like we did when we originally learned about CSS modules.
That is footer styles.butter and we're done.
If we say things, we should see a little more space between the bottom of the post and the footer.
That looks a lot nicer Now.
Another major problem is on the blog posts page itself.
We want to make sure that this content is clickable, but now it looks terrible and we still have the numbers.
We want to clean this up and we're going to do that by adding a few more styles into the mix.
Now this content comes from the pages directory.
In there, we have blog.js So all closed the components folder and the two files we were just working with We're gonna open up blog JS, and we're going to create styles specifically for it.
Right here.
I'll create a new file blog.module.s CSS, and now we can actually set up some styles for it.
We're going to style the entire list itself.
End the individual list items, but start by styling.
The list itself will set up a class selector for something like posts, then will set up a few styles.
I'll start with list style type setting that equal to none.
We don't actually want to show those numbers next to each post, and I'm also going to set margin equal to zero to remove the default margin that those lists usually have.
Let's start there in the blood component we have to import those styles.
So I'll import blog posts styles from.board slash blog.module.s CSS.
And once the import statement is in place down below will use it now.
I designed that for our ordered A list right here.
So `className` setting that equal to hear it is blog posts styles.posts.
Now, with this in place, we should be headed in the right direction over here.
At least we no longer have the numbers and everything is nice and aligned.
Now what? We want to target the individual items.
When it comes to the Dom structure, it's pretty complex.
Well, it's not pretty complex, but it could be.
We have the list item.
We have our link which just gets converted to an `<a>` element.
And in there we have hte two and P.
Now, in the end of the day, I actually want to apply styles to all four of these things.
And there are two approaches to that.
I could set up four new class selectors over here, and I can load for in and set up four instances of `className` or I could just use one.
So let's explore how we might get that done right here.
That is.post and this is going to apply some general styles and all we're going to do here is put some spacing between our posts above and below them.
So margin one R e m on the top and the bottom and then zero on the left and the right.
Now this particular class is going to get set up on the list item.
This represents the individual post.
So right here, `className` setting that equal to that's gonna be blog posts tiles.post.
Now what we're gonna do is just use some basic principles from CSS and S CSS to style the rest by element name.
This is perfectly valid, and it's a common approach.
So right here I could say something like, Let's target our `<a>` elements inside of posts and apply some styles to those Maybe, for example, I want to set the background equal to a off white.
I'll use the hex code f four F four F four for that, and I don't want that purple and blue link text, so I'll set the color equal to black, which is the hex code, the number 06 times.
So if we just set that up, we should see those styles actually applied.
And over here they are, so we don't have to just use class selectors in our modules.
Sometimes we want to set up one and just style some stuff inside of it, making our lives a lot easier.
This is also just fine.
Now what? We're gonna add a few more styles inside of here.
I'll set display equal to blog so we can control the spacing.
I'm also going to set patting equal to one r e m to put some space between the text and the edge of this off white box.
And from there I'm going to set text decoration for the link equal to none.
I don't wanna have that underlined link, and over here we can see we're now headed in a nice direction.
Now, when we're working with CSS modules and using this approach were not limited in any way, I could still set up something like this.
I could target `<a>` elements using the hover pseudo class.
So when you're hovering over the link, we could make the background a little darker.
Here, I'll set the background equal to that would be a hex code of e four e four e four, which is just a slightly darker grey.
This is going to apply exactly like we would expect as we hover over.
We see it now.
From here we can continue styling the other elements inside of the post like the `<h2>` and our paragraph.
So let's add those into the mix as well.
Nothing to stop us from just targeting them by elements.
Right here.
I'm going to set up margin bottom for the `<h2>`.
Removing that and then I'm going to set up some styles for that paragraph as well, and then will be done right here.
Just three styles.
First up is the color.
I'm gonna use the hex code with the number 76 times, which is a slightly dark gray, Not too dark, not too light.
Then we're going to set the font size equal 2.8 R e m.
A little smaller than it currently is.
Currently it's sitting at one Arianna.
Then we're going to set the font style equal to a Talic just to differentiate it from the other content in that box.
And there we go.
We set up a single class selector in our CSS module and we targeted the elements inside using element selectors.
Now, if we check things out over here.
What do we get? We have our styled blog posts.
I can still access those posts by clicking on them.
I convey you the post content and everything is looking pretty good.
So now we have a complete site with a markdown blog posts powered by Gatsby.
We could take this and we could continue on with it, really? Making it our own for either ourselves or for a company where working with now, this is just the start, being able to create a markdown blog posts awesome.
And it works really well for a lot of folks who prefer that.
But with Gatsby, we can also source our content from a CMS.
And that is exactly what we're going to cover next.
I'm excited to get to that.
So let's jump into the next lessons.

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

