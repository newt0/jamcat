---
title: "3. Linking Between Pages with Gatsby"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=1620"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## Transcription text

Now that you have a few pages in place, let's go ahead and link between those pages.
Now, the most obvious way to get this done would be to use the `<a>` element provided by `html` itself and that would indeed work.
So let's start with the home page.
I'm going to navigate over to `index.js` the home page component and in the browser I'll navigate over to `localhost: 8000`.
All we're gonna do is include some text down below, like `Need a developer`.
Then I'll have contact me, which will be a link over to the contact page.
So what am I going to do? Well, over here, I'll add some stuff just below our `<h2>`.
It will be a paragraph tag, something like `Need a developer?`.
Then after that, it will be the link.
So here I'm using the `<a>` element.
The link text will be something like Contact me and I'll set up the `href` attributes to specify the destination that would be ``/contact`` to navigate over to that page.
Now, this is indeed gonna work.
I save the file, I see my new text and my link on the home page and I'm going to click `Contact me`.
It brings me over to the page, as expected now this does indeed work, but you'll notice that we went through a full page refresh.
The entire page went away.
It went to a white screen.
Then the contact page was loaded in.
Let's see that one more time.
So we click the link.
We see that flash of content and the new content appears.
That's because we're using the standard `<a>` element.
This is indeed going to work as a tool to link between your pages.
But Gatsby actually has a different way.
You can link between your pages, which comes with a lot of optimization, allowing the content to be swapped out instantaneously.
So let's see that in action.
And the first thing we need to do is import something new up above.
Right here, for this import statement will be grabbing a named export, so inside of `{}` that is capital "L" link and will be grabbing it from the Gatsby `npm` module.
Now remember, Gatsby is an `npm` module that's already installed with our project over in `package.json`.
It's listed out as one of our three dependencies.
So we're good to go.
No need to install anything new.
And what we're getting access to is `Link`.
`Link` is a `React component`.
When we use `Link` to link between the pages of our Gatsby site, there's a whole bunch of optimization that happens behind the scenes.
For example, Gatsby is going to pre load the page content you might be heading to.
So if you do click that link, it loads instantly, and you no longer get that flash of content between pages so down below will leave our old example in place and will add the new one just below it.
Need a developer.
Then we'll set up our new link using the  `Link` component.
So right here, I'm going to set that up.
Now, here we have a separate opening and closing tag, and right in between, we put the text for the link so once again, contact me.
Perfect.
The only other thing we need to do is specify a prop to the  `Link` component.
The  `Link` component needs the to prop two is the path we're trying to head to.
In this case, it is `/contact` exactly like we had up above.
So this is the correct way to link between pages in your Gatsby site.
If you're still linking to an external site like your github profile or Twitter, the `<a>` element is perfectly fine.
Let's go ahead and see this in action.
I'm going to save `index.js`.
Over in the browser will navigate to the home page, and right here we see two links.
The old one we had before and our new link down below.
Now let's pay careful attention to the content.
As we click the new link, I click it, and what do I see? I can see the new content instantly.
No longer do we have the flash of content we got when we clicked that old link.
So it's a much nicer user experience.
Once again, when using `Link` Gatsby performs all sorts of optimization is behind the scenes to make sure the new content can be showing in what looks like riel time.
Well, let's go ahead and remove that first, a solution which wasn't working so well.
And with that in place, we are done with new content down below a quick challenge for you to knock out.
The goal is to add a couple of new links to the site on the contact page.
I'd like you to take that Twitter handle and convert it into a link to the Twitter profile.
So it should actually take users away from your site over to `Twitter.com`.
Now, if you don't have a profile, you want a link, then, you can just linked to any external website like `google.com` or something similar for step two on the about page, I want you to link over to the contact page if someone wants to reach out based off of your bio, so make sure to include the correct link there.
Finally test your work.
Actually, pull up the site, click both of those links and make sure they work as expected for this link.
The link internally between two of your pages.
You should see the content instantly without that flash.
All right, knock it out.
When you're done, come back and click play.
All right, let's get to it on the contact page.
I'm gonna link over to the Twitter profile.
So right here.
I do want that handle in the future, so I'll cut it out, copying it to the clipboard.
Then I'm going to set up the a `<a>` element, and since we're working with an external link, we don't need to use the `Link` component.
Now the text is going to be exactly the same as what we had before.
Just the handle itself and the URL will be specified via the `href` attributes.
That will be `https://twitter.com/` the handle, which once again I have as part of the clipboard perfect with the Lincoln Place.
We can always is set up to the `target` attributes, setting that `=_blank`.
And that's going to open the link in a new browser tab so users aren't completely redirected away from our site.
Let's go ahead and test that out over inside of the browser.
I should have that new link showing up.
I click it.
It opens up a new tab, and it pulls up my Twitter profile.
Now I can go ahead and close that, and I'm still on the contact page.
The next link you needed to create was onto the about page on the about page.
I wanted you to link over to the contact page.
In this case, we want to use the  `Link` component as we're linking internally.
Some going to import the named export link from the Gatsby module, then down below.
We're actually going to use it.
No, I didn't tell you where to put it.
So anywhere is fine.
I'll just add it down below my other paragraph right here.
I'll add a new paragraph.
I'll put the link right inside.
The link text can be something like, Want to work with me? Reach out and then all I need to do is set up the to prop for the `Link` component right here.
That will be a string `/contact` and we're done.
Now let's head over to the about page and make sure this actually works, if it does, will be all done our challenge.
So I'm going to remove those challenge comments.
I'm going to save every single file in the browser.
Let's go to `/about` here.
We have our new link, which is a good start.
I click it.
It brings me over to the contact page without that full page refresh, which is excellent.
And now that we know how the link between the pages on our Gatsby site let's go ahead and move on into the next video, where you're gonna figure out how to create shared components.
So imagine we want to take links to the next level, setting up something like a navigation bar that shows up exactly the same for every single page.
That is the topic of the next lesson, so let's jump right into that.

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

