---
title: "1. Creating a Gatsby Site"
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

<iframe width="560" height="315" src="https://www.youtube.com/embed/8t0vNu2fCCM?start=38" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
## Transcription script

Welcome to the very first lesson for `The Great Gatsby Bootcamp`, where we're going to start using Gatsby in this video in particular, we're gonna focus on three things.
One, we're gonna learn a little bit more about Gatsby to we're going to install The Gatsby command line interface.
And three, we're gonna use that command line interface to create and run.
Our very First Gatsby project by the end will have our first Gatsby site up and running.
And that's what we're gonna build off of and customize throughout the rest of the bootcamp.
Let's get started with Gatsby by pulling up its website.
We confined that over at `Gatsby.js.orgs` and I want to spend it just a couple of minutes here, exploring the tool in a little more detail.
As mentioned in the welcome video, Gatsby is a static site generator based on `React`.
`GraphQL` and `node.js` Now Gatsby can do so much more than you contest likely do with a static site generator, and you actually won't see that term anywhere on The Gatsby home page.
So instead, let's think of Gatsby as a `React` framework for building complex websites and Web applications.
So with Gatsby, you're not just limited to static sites.
You can also build complex Web apps with data storage, authentication and more.
So if I'm trying to build a personal website to make myself look good to potential employers, I could use Gatsby to get that done.
If I want to start a freelance Web development business building websites for restaurants, I could use Gatsby for that, too.
And if I wanted to launch the next startup and I needed to create my Web app, I could use Gatsby to build that Web app out.
Now Gatsby has gotten so popular because it's really fast and super easy to work with.
Gatsby has so many core features baked right in, so you can get started with a new project in a matter of minutes without needing to install or customize any build tools.
Gatsby comes with everything you need to get started right away, and the good news is that you can further customize your Gatsby projects, using one of the many plugins that it supports.
These plugins allow you to add all sorts of new features to your site, both big and small.
And don't worry, we'll be diving deep into plugins and how to use them a little later in the bootcamp.
Now let's say I'm creating a personal website using Gatsby.
I wanna have a small portfolio of my projects, and I also want to maintain a and making myself look good to potential employers.
Now, for me, I want to write those posts in markdown.
I like having my content directly inside of the project itself.
So what I want to do is write markdown posts.
Then I want Gatsby to convert those over to individual `html` pages for my site.
In that case, there is a `gatsby-plugin-react-helmet` us.
Get that done.
So all we need to do is write the markdown posts in new markdown files, and Gatsby handles the heavy lifting of converting those over to `html` pages, using a unified template so everything looks consistent in your sight.
Now let's go back to that other example of someone who's starting a freelance business targeting restaurants.
In that case, the restaurant owners want to customize things.
They want a blogger taken, talk about new specials, and they also want to be able to update their menu on the fly whenever it's convenient for them now.
In that case, markdown is eight terrible choice.
The restaurant owner is likely not technical and does not want to manage content in markdown.
They would have to learn about markdown and code and get in all sorts of things.
It's never going to happen.
That's why content management systems like `Wordpress` got so popular it allowed website owners to easily manage the content displayed on the site without needing to write code.
The good thing about Gatsby is that it conduce to that same thing.
There are and even `Wordpress` so you can have a website powered by Gatsby but still allow the website owner to manage that content, using a nice, simple admin interface where they're just filling out forms, fields and clicking, Save and the new content magically appears.
I remember when I was running my freelance Web development business from about 2000 and 11 to about 2000 and 15 and everyone you talked to wanted a `Wordpress` site.
They didn't want a `Wordpress` site because they cared about using `PHP` or my `SQL`.
They wanted a `Wordpress` site because they knew with a `Wordpress` site, they could customize the content on their own.
Now everyone can have what they want.
Developers can write their sites in a modern stack, using `node.js`,`GraphQL` and `React`, and the website owners can still manage their content using whatever CMS they're most comfortable with, including `Wordpress` in this bootcamp will end up covering both of those approaches.
So we're going to start off creating a simple Gatsby site and getting comfortable with the basics.
Then we'll convert that over to a blog posts word by markdown files and from there will convert it over to a blog posts word by a content management system and in this case, will be using the `Contentful` CMS to get that done.
Now let's actually get started with Gatsby.
The only thing you need installed on your machine to use Gatsby is `node.js`.
If you don't have `node` installed, you can grab it over at `node.js`.org's and you don't need a specific version.
Just grab something modern.
Let's say ver.8 or greater.
In this case, we have ver.10 and ver.11.
Both of those would be perfectly fine.
And if you have something slightly different on your machine.
That's gonna work fine as well.
Now, to actually use Gatsby, we have to install its command line interface that's going to be used to generate new Gatsby projects.
And it's available as an `npm` module.
So what I'm gonna do is crack open my terminal, and from here we're going to run a single `npm` command.
That's `npm install` followed by the G flag(`-G`) to install the module globally.
And the module name is `gatsby-cli` at the latest version to appoint 4.17.
Now, if we go ahead and run this command, it's gonna work through the installation process.
And once this is done over, going to do is generate a New Gatsby project and open it up in `Visiual Studio Code` or whatever text editor you want to use.
So right here The installation did complete successfully and to generate a new project.
First, we want to figure out where to store the project.
Now, if you have a folder on your machine where you like to store your programming projects, go ahead and switch to that directory for this bootcamp.
I'm just going to put the new project right on my desktop, so I'll use `cd desktop` to switch over to the desktop.
And from here we're going to use The Gatsby New Command.
Now the new command is going to accept a couple of arguments.
First up is the project name.
Now this project name is the name of the folder that's going to get created.
So in this case, I'll call it something like Gatsby-bootcamp.
And the other argument we provide is the URL to the starter we want to use Now.
Gatsby has a few built in starters officially released by The Gatsby team, and there are hundreds of other ones created by third parties developers allowing you to build all sorts of interesting sights and applications.
The goal in this bootcamp is to explore the fundamental Gatsby features, and if you know those, you'll be able to work with and customize any of those other starters out there.
So for us, it's gonna be the following URL `https;//github.com/Gatsby.js/gatsby-starter-hello-world`.
So take a quick moment to run that command, and it's going to do two important things.
One, It's going to create that new project folder and pull all of these starter code in to what it's doing right now is installing all of the modules necessary for your project to actually run.
Once this command is done, we can crack open the new directory in `Visiual Studio Code` and get started building out our site.
Actually, before it's even done, we can get that process started.
So over in `Visiual Studio Code`, I'm gonna open up that new directory now for me.
I put it on my desktop and I called it Gatsby bootcamp.
So I'll crack that open and right here, you'll notice we do have a set of files and folders showing up, and we will explore all of these in detail.
For now, all I want to do is run a single command from the terminal, allowing us to start our site up now in the background.
I can see that the command has finished and were actually done with the terminal.
We're not going to use this for anything else in the bootcamp.
All of the other terminal commands.
I'll be running.
I'm going to run from the integrated terminal that `Visiual Studio Code` comes with.
You can always go up to terminal New terminal, defying the keyboard shortcut to open up the terminal in VSC.
It's definitely a keyboard shortcut I recommend.
Now right here.
We're going to run one of the few scripts that Gatsby provides.
If we open up Packaged doc, json Weaken, see under the scripts Property we have six.
The one that we're going to start with is the develop script, which allows us to start up the development server that we can use to run our app locally and build the project out.
This comes with all sorts of great features, like Live, reload, so your changes are reflected in real time.
Now there are a few other commands as well.
We'll be exploring later in the bootcamp.
But for now, let's start with that develop script.
So from the terminal right here in the Gatsby bootcamp project that is `npm run develop`.
When we do that, it's going to try to start up our Gatsby project.
The default port for that is 8000 and once this command is done, we should be able to crack open `localhost: 8000` and visit our site here.
It's saying that things have compiled successfully, so let's crack this side open in a new browser tab.
localhost on port 8000.
I visit that in What do I get? I get a small `html` page printing hello World to the screen.
So there we go.
If you're seeing this, that means you have successfully created and ran your very First Gatsby project.
Now, for the moment, it doesn't do anything too interesting.
So let's go ahead and wrap up by actually customizing what we're seeing on the page.
To get that done, we need to focus on the source directory.
Now we have a lot of other folders and files in the project will focus on those later in the bootcamp.
For now, the focus is on to the source directory, and if we open that up, we can see there is a single directory inside of there called pages.
The Pages directory is a very important folder in Your Gatsby project, and it's actually the topic of the next lesson.
So for the moment, we're not going to dive too much into the details of what it is or how everything's working.
If we go inside of that folder, though, we can see we have a single file `index.js`.
This contains the `React component` that's rendering the home page right here.
If I open it up, we can see it's about as simple as it gets online.
One we import `React` on line three.
We export a functional component where we set up a `<div>` with the text of Hello World.
So this is the content or seeing in the browser.
If I go ahead and remove that text content, I can replace it with something like the name of the bootcamp, `The Great Gatsby Bootcamp`.
I can save the file, and in real time we can see the changes reflected over here, thanks to the development server were running in the background.
All right, that's where we're going to stop for this one.
In this first lesson, you got Gatsby installed and you also created and started up your very First Gatsby site.
In the next lesson, if the focus is gonna be on Gatsby, pages will talk about customizing pages and creating new ones, and the focus will be on that page is directory and the files inside.
I'm really excited to get to that and learn more about why all of this is even working, so let's jump right in to the next lesson.

{{< alert theme="info" >}}
Andreaw Mead's Udemy Courses are {{< color "#FF0000" >}}90%OFF{{< /color >}} now!
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Freact-2nd-edition%2F" target="_blank" rel="nofollow">The Complete React Developer Course (w/ Hooks and Redux)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fgraphql-bootcamp%2F" target="_blank" rel="nofollow">The Modern GraphQL Bootcamp (with Node.js and Apollo)</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fmodern-javascript%2F" target="_blank" rel="nofollow">The Modern JavaScript Bootcamp</a>
- <a href="https://px.a8.net/svt/ejp?a8mat=3BK8OP+16V93U+3L4M+BW8O2&a8ejpredirect=https%3A%2F%2Fwww.udemy.com%2Fcourse%2Fthe-complete-nodejs-developer-course-2%2F" target="_blank" rel="nofollow">The Complete Node.js Developer Course (3rd Edition)</a>
{{< /alert >}}