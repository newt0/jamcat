---
title: "19. 404 Pages and React Helmet"
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

<iframe width="560" height="315" src="https://www.youtube.com/embed/8t0vNu2fCCM?start=15018" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

There are just two videos left in this one.
You're gonna learn how to set up a 404 page, and you're also going to learn how to customize the head of your document to set up things like a page title.
And then in the next lesson, the final one will take our Gatsby site and will deploy it live to the Web.
For now, though, let's get started setting up a 404 page, and this process could not be easier in `Visiual Studio Code`.
I'm going to close all open editors, and all we need to do is create a new page in the pages directory, and this file should be called 404.js.
In here we export a `React component`, and that is what renders when someone visits a page that's not found.
So let's actually get to this right here.
I'm going to start by importing `React`.
Since we'll be setting up a `React component` and down below, I'll create it, Const not found equals.
I'll use a new functional component returning some `JSX` and then down below.
We can export it so  `export default` not found now on the not found page.
I still want to render the layouts so people can use the navigation bar to go over to a page that does exist.
And I'm also going to link to a different page, like the home page in the not found text.
So right here I'll import link from Gatsby and then down below, I'll import the layout component that we created from that file that is.
`/components` /layout.
Now we can actually fill out the return value for our functional component, and we're going to start by rendering the layouts.
Let's set the layouts up and inside of there we will render a couple of custom things on the page as well.
I'll start with a header.
Something like Page Not Found should get the message across.
Then down below, I'll set up a paragraph, and in their all I'm going to do is use the  `Link` component, and I'm going to link them over to a page that I know does exist.
I'll say something like head home and this link will go to /and there we go.
That's all we need to do to get a 404 page set up with our Gatsby projects.
Let's actually test this out.
So down below, I need to start up my server.
`npm run develop`ed.
And once that's up and running, we're gonna visit a URL.
That does not exist.
So right over here, I'll go to my site.
/This is not Riel, and I misspelled it.
But who cares? That's the whole point.
Now, when we're running our development server, Gatsby first brings us to this page, which is designed to give us more information.
As we're creating our site, we can see pages that do exist.
We can see why we're seeing the 404 in the production version of the site, though this would never show up.
Now we can view our actual 404 page by clicking preview Custom 404 page.
And when I do that, we get what we designed.
So this is what a regular user would see once we actually get our site up and running in production, which once again is the topic of the next lesson.
So right here they can go to a page that does exist or they can just click that home link to get back to a working page.
So there we go.
The 404 is all set up now.
I want to focus on customizing the head of our document so we can set up things like page titles.
And to get that done will be using the very popular `React` library called Helmet.
If you're not familiar with it, it's pretty much the standard for working with the head of your document from `React`.
And there's a `gatsby-plugin-react-helmet` us.
Integrate that into our sights.
Let's head over to the plugins page on the Gatsby site and search for helmet right here.
`gatsby-plugin-react-helmet`.
That's the one we're gonna end up using.
Now there are actually two libraries will install will be installing this plugin, and we'll also be installing the `React` Helmet library, which is linked to right here.
We can crack that open in a new tab to check that out as well.
This is just a standalone `React component` that we could use outside of a Gatsby site.
It's a really great choice for managing the head of your document, and they have a ton of great examples down below as to how you can get all of this done now, when it comes to the plug and we're going to install this polls, all of that information in to the static pages for our site.
So it's definitely going to be an important piece to the puzzle.
Let's take a quick moment to install both of these.
Then we'll actually wire them up in our app, so down below will shut things down.
Ellie is clear to clear the terminal output `npm install`.
First up is Gatsby plugin `React` helmet at the latest version, 3.0 point 12 and next up is `React` helmet itself at 5.2 point zero.
Now we can go ahead and let these install and, well, they're installing.
We need to configure this `gatsby-plugin-react-helmet` now.
There's no need to provide any options for this one, so it's as simple as listing it out in our plugins array, and I'll add it right up top as the first plugin right here.
Gatsby slug in `React` helmet And there we go.
It is configured.
Now what Weakendo is import the `React` helmet component and actually use it to set up titles for our pages.
Now there are two ways we could do this.
We could manually set up this configuration in every single page component as well as our blog impl it.
Or we could create a component that handles the configuration for us.
Something simple that we can render on old pages, meaning that we only have to configure `React` helmet once.
And of course, that's the approach we're going to take.
So in the Components Directory, let's create a new file called head.js for the component that's going to manage the head off our document right here.
We're going to import, `React` from `React`, and we're also going to import something from `React`.
Helmet Right here it is a named export called helmet.
That is a `React component` from the library.
We just installed `React` helmet and we're done.
Now we can create our component and export it from the file.
So right here CONST.
Head equals a functional component where we're going to return some `JSX`, which will get to in just a second down below.
Let's export it  `export default` head.
Now, when it comes to what this component should render over going to do is render helmet itself.
We're not actually gonna add anything else into this component.
And when helmet gets rendered, it doesn't show anything onto the screen.
Instead, it just manages the head of the document.
So right here we can configure things like the title using the title prop.
This is a test, so let's leave our component file like this.
Don't worry.
We will grab a proper title from the site Meta data a little bit later.
For now, though, let's just get this title showing up to do this.
Once again, this component needs to be loaded in and used in every single one of our pages, including art page templates.
Let's get started with the most obvious one, the home page.
Then we'll move on to the other pages we have so right here we have to import head import head from.
`/components`, /head, and then we render it.
And we're just going to do that as the first thing in the layout.
And remember, it's not going to show anything there.
This is just going to allow us to manage the document head.
So right here I'll render our component we can then go ahead and save things and start up the development server once again.
So I'll use clear, followed by `npm`.
Run, develop.
And once it's up and running will visit the home page and hopefully we see our custom title showing up.
Over here, we have the home page.
I'll just give things a quick refresh.
Let's try one more time.
There we go.
The server is finally up, and in a second we should see our page.
We have the page and we have our title.
This is a test is showing up.
Now when it comes to customizing that five icon, all you need to do for that is swap out the file in the static directory down below five Icahn.Co.
So let's continue on with this particular example, and what I want to do is focus on actually pulling in useful information.
The first thing we're going to do is we're gonna pull in the site metedata title.
This is something we're going to show as part of the title for every single page.
It's not the only thing we're going to show, but it's part of what we're going to show so right here for a sight like Gatsby.
I can see that if I hover over this title for a second, it's gonna show me the full thing.
We start off with something specific to that page `gatsby-plugin-react-helmet` followed by a vertical line followed by the site name Gatsby.js.
That's similar to the approach we're going to take here.
So each page will have something specific to render up there.
But then we'll also have something generic like the site title to get that done.
Let's first pull in these site title.
So right here, we're going to use you `staticQuery`, import `useStaticQuery`.
And I'll import `GraphQL` from Gatsby, then down below.
We can actually grab that information.
So `const Data` equals we're going to call `useStaticQuery` using the `GraphQL` template tag with our string.
And right here we're going to perform one of the first queries we ever set up.
Query site site meta data in there grabbing the title.
So now the title is something we can actually use down below.
Let's go ahead and set that up.
So instead of the static title, we're going to set up a dynamic one.
We have that data at data.sight.site meta data.title we can get, save things.
And hopefully we now see that showing up on the home page right over here.
I have full stack bootcamp, So this is a great start.
The next thing we want to be able to do is pass in the part that specific to this page which is going to come from first to get that done, the actual component is going to get called with a single prop.
So whatever someone renders head, they can pass in the title they want to use for that page.
So here I'm using head on the home page so I could say something like home.
Now I can go ahead and actually access that prop in the component and use that when determining what the title should be.
So right over here, let's get that done.
We have our `props` passed in.
I'm just going to destructure that object to grab the title.
And now we can use that in helmet down below.
Right here.
We're going to change the title prop that we pass to helmet we're still going to include this information, but we're gonna put all of that in a template.
Stringfy so we'll start off by adding in the page title That's the title prop up above, then a space, the vertical bar and another space, followed by the site title right here once again data.sight.site meta data.title.
Now we're going to see both of those things on the home page.
So right over here, I have home followed by full stack bootcamp.
So now we have a little component, making it really easy to integrate this into all of our pages.
Instead of needing to write this code in every single page.
Let's go ahead and actually get that done for the four other pages we have in the pages directory.
And we're also going to do the same thing for the dynamic page template for blog posts.
So right here, what I'm going to do is copy the import statement to grab the head component and will continue on in the contact page, will paste that in, will set up the head component inside of layout, and right here over going to do is provide the title for this specific page which will just be contact Next up.
We have the blog posts page, so we want to import head down below.
We want to use it right here.
We have layouts.
I'll go ahead and set head up providing the title for this particular page which will just be blog posts perfect.
Next up, we have about where we do the exact same thing import and set it up head title about and we're done.
And finally, the new page we just created our 404 page.
We could also use the head component inside of here.
I'll import it and down below will go ahead and use it, setting up the title to something like 404 Perfect.
The only other page we need to worry about as mentioned is the template for our blog posts right here.
What we can actually do is use the blog posts title as the page title, so I'm gonna import head exactly like we did before and down below.
We're going to set it up.
So right here in layouts, we're going to set up head.
But instead of providing a static string which made sense for our other pages were going to provide a dynamic value the actual blog posts title, which is used just down below.
So that's `props`.data.Contentful blog posts.title, and we're done now.
We have this set up everywhere on our site and we contest things out.
So over here we go to the blog posts page.
We have blog on about.
We have about on contact, we have contact, and if I actually visit one of my posts, I can see that showing up in the title as well.
Now that we have this in place, we have a really nice site, and it's working really well locally.
The next and final thing I want to focus on is actually getting this up and running in production so anyone with an Internet connection can check out the site you've created.
That's exactly what we're gonna do next.
So let's jump right into that
