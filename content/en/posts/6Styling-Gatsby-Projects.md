---
title: "6. Styling Gatsby Projects"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=3373"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## Transcription text

You now have a decent amount of content on your Gatsby sites spread across four pages.
The only problem is that all of this content is unstylish and looks pretty terrible.
In this lesson, you're going to start to learn how you can style your Gatsby sites using CSS along the way.
This video also covers the process of installing and setting up `gatsby-plugin-react-helmet` and `gatsby-plugin-react-helmet` syntax.
But let's get started with some basic styles.
Getting those applied to the site in a `Visiual Studio Code`.
The first thing we're gonna do is create a new place for our site styles.
Now I'm going to close all open editors.
There's no need to have all of these files open anymore and down below in the source directory.
This is where we're gonna add a new folder.
I'll call this something like styles.
Once again in the name is not important.
And in there I'm going to put a new file called `index.css`.
This will be the start of these styles for our site and to make it obvious whether or not these styles are being included, all we're going to do is use the universal selector to select every element on the page and we're going to change its color over to read.
Now, by default, we can see these styles are definitely not being applied.
Nothing over here is red, and this is correct by default.
Gatsby is not gonna load in any of your style sheets.
It's up to you to import them.
And in this case, we're gonna import our base style sheet from the layout component as the layout component is used on each and every page.
So we need to do is set up another import statement to get those styles included in the static site that Gatsby generates right here.
Importing that's gonna be.
to get out of the `components/styles/index.css`.
Now, with just that, one line added, we can save the component and we can see that the styles are definitely being applied as everything is red.
And there we go.
We now have a style sheet loaded in, and we could write every style for our entire Gatsby site right inside of here.
Now, that's not the approach we're going to take.
We're going to break things up a little bit, but this is a great starting point.
Before we go any further, what I want to do is enable a CSS pre processor here will be using cess, allowing us to take advantage of the S CSS syntax so we can use all of the great features, functions, `mixins` and other tools it provides.
Now to do that, we are going to use our very first.
You can find a list of all available plugins on it.
Here Gatsby site.
That's `gatsby.js.orgs`.
And here's the site I had pulled up earlier in the bootcamp.
Now, in this case, we're looking for the plugins page.
This allows us to search through all of the available plugins to find the one we're looking for.
Now.
This list includes both official plugins released and maintained by the Gatsby core team, and it also includes third party apis slug ins written and maintained by members in the community.
So right here, the one we're looking for happens to be an official plugin.
And if I search for CSS here it is `gatsby-plugin-saas`.
So currently I can use the import statement to import a CSS file.
But if I tried to import a saas file or an s CSS file, Gatsby wouldn't know what to do.
Once we have this plugin correctly installed and configured, it will all work as expected.
The right hand side.
We have the documentation for this particular plugin here.
We need to install a few things and add a little bit of configuration, and we're going to work through that process together.
So let's go ahead and set up support for this by moving into the terminal, shutting down the development server using clear to clear the output and finally using `npm install`.
So right here, that's `npm install`.
And the first thing we're going to install is the plugin that is `gatsby-plugin-sass` as seeing over here.
So all of these are the names of the `npm` modules.
And the other thing we need, which is mentioned in the docs for this plugin is `node-saas`.
So this module is responsible for actually converting the files down to regular CSS.
And this plugin just allows us to actually do that from a Gatsby site.
Now we can go ahead and run this installation command, installing both of those tools.
And once that's done, all we need to do is configure our Gatsby site to, actually use that plugin.
It's not enough to just install the plugin.
It actually needs to be configured.
Now, this is done via a file that currently does not exist in our project.
But we can go ahead and create it.
It needs to live in the root of our project, and it needs to be called `gatsby-config.js` Now there's a lot we can do in this file as well explore throughout the bootcamp.
One of the core things we can do in here is configure the plugins we want to use, and that's exactly what we're gonna end up doing.
This config file just needs to export an object, But it's important to note that this is a `node.js` file.
So we need to use `modle.exports` setting that equal to the thing we want to export in this case, an object.
Now on here.
One of the main properties we're gonna end up using in this config file is plugins.
plugins is an array, and here we can configure all of the plugins we want to use.
Now, in our case, we only have the one plugin.
So we're going to provide that as one of our items in the plugins array.
And all we need to do is list out the name of the plugin.
That is `gatsby-plugin-saas`.
We can save the file, and now we're actually ready to use s CSS or saas, in the project.
So down below in the terminal, make sure to stop your development server.
If it's running, mine's not.
And then we're going to start it up again.
`npm run develop`.
And once it's up, it's going to be using this plugin, which means we can now create and import s CSS or saas files.
So I'm going to do just that.
What I'm going to do is take `styles.css`, excuse me `index.css` in the styles folder, and I'm going to rename.
I'm going to call it `index.css`.
Then what I'm going to do is import that file instead of importing the file that no longer exists.
I just add the S save the layout component and now our site should be back to a nice working state.
Here, everything is still shown in red.
And if I go over to the style sheet, I could change that to blue, save the file and I can see that my change is indeed being applied.
With that plugin in place, we should also be able to use all of the great s CSS features.
So I'm going to create a variable up above using dollar sign followed by the variable name, and I'll store the green color inside of there, then down below instead of just providing the color all reference it via that variable, So dollar sign color.
Now, this would not work in regular CSS, but we're not working in regular CSS.
We are in an S CSS file and right here I can see that green is showing up.
So there we go with a little bit of configuration adding just a few lines of code to our new file were able to tell Gatsby that we want to use a `gatsby-plugin-react-helmet` e for our site.
Now let's go ahead and wrap up the video by grabbing a nice base set of styles will be using for the project.
You can grab these styles by heading over to the browser and going to the following URL.
That's links.
mead.io/gatsby-styles`.
Now, this is just going to redirect you over to a github.
Just and here we have a very long style sheet.
This is what we're going to copy over to our project as our starting point.
So right here, I'll click the raw button to pull up the raw file content.
I'm going to highlight everything using `command A` or `control A` depending on your OS.
Then I'll copy it to the clipboard and paste it over here in `index.css` removing the stuff we had before.
Now, with this in place, we should notice a pretty big change to how our website looks over here.
What I'm gonna do is pull up.
The site will notice it's no longer in green, which is good, and will also notice that it's definitely a little bit styled.
We have nicer font families and a little bit of spacing along with nicer font size is now.
Obviously, we're not done styling just yet, but using that base set of styles will be able to further customize these styles for art project.
So that's where we're going to stop for this video.
We now know how to add basic styles into our Gatsby project, and in the next lesson, we're going to take that to the next level by learning about CSS modules.
That is my favorite way to style `React component`s.
So let's go ahead and jump right into that.

## Info

{{< alert theme="danger" >}} 
本書き起こしはgithubレポジトリで管理しています。
**If you find a mistake, please let me know via Github issues.** 
[Issues on Github](https://github.com/newt0/gatsbybootcamp-transcription/issues)
{{< /alert >}}

{{< alert theme="info" >}}
Andreaw Mead's Udemy Courses are  {{< color "#FF0000" >}}90%OFF{{< /color >}} now!
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Freact-2nd-edition%2F" target="_blank" rel="nofollow">The Complete React Developer Course (w/ Hooks and Redux)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fgraphql-bootcamp%2F" target="_blank" rel="nofollow">The Modern GraphQL Bootcamp (with Node.js and Apollo)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fmodern-javascript%2F" target="_blank" rel="nofollow">The Modern JavaScript Bootcamp</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fthe-complete-nodejs-developer-course-2%2F" target="_blank" rel="nofollow">The Complete Node.js Developer Course (3rd Edition)</a>
{{< /alert >}}

