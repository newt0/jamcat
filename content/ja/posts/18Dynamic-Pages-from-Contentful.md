---
title: "18. Dynamic Pages from Contentful"
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

<a href="//af.moshimo.com/af/c/click?a_id=2155533&p_id=969&pc_id=1263&pl_id=13856&guid=ON" rel="nofollow" target="_blank"><img src="//image.moshimo.com/af-img/0304/000000013856.gif" width="100%" height="auto"></a><img src="//i.moshimo.com/af/i/impression?a_id=2155533&p_id=969&pc_id=1263&pl_id=13856" width="1" height="1">

<div style="position: relative; padding-bottom: 56.25%;">
  <iframe 
    style="position: absolute; top: 0; left: 0; width: 100%; height: 100%;"
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=13764"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

Now that your list of blog posts is populated from `Contentful`, we want to make sure we're generating pages for each of those posts.
Right now, if we click on them, we get nothing.
And that's a problem.
So in this video, we're going to accomplis`<h2>` things.
First, we need to dynamically create new pages for the `Contentful` posts and then to we need to make sure we're actually rendering the post content in the post page template.
So that template is gonna need to change a little bit.
The entire focus is gonna be on Gatsby Node, where we dynamically create our pages and the blog template where we render the content to the screen.
Let's get started with Gatsby `node` Now to set things up for markdown it required us to use to of the internal API on create `node` and create pages Now on create `node` was just used to generate slugs for our posts.
That's a field we set up in `Contentful`.
So we actually don't need this anymore.
We can remove it entirely down below.
The only one we're going to use is create pages.
We just need to adjust it instead of fetching the markdown slugs and using those to create pages.
We want to fetch our `Contentful` slugs and use them.
So let's get started right here.
We have `allMarkdownRemark`.
I'm going to remove all of that.
We still have our base query, though this time we'll use all `Contentful` blog posts like we've used before.
There are no arguments required as we just need a list of slugs.
There's no need to order it as that doesn't matter.
Right here, edges Node.
And the only thing we're going to grab is the slug as that's the only thing we need Now down below.
When we loop through the data, we can use the `Contentful` slug right here.
Response.data that still exists.
No longer do we have `allMarkdownRemark`.
We now have all `Contentful` blog posts.
We still have edges and we still want to reiterate over that using for each inside we have the create page call.
The component is still blog.
EMP lit.
The path is still /blog posts word slash the slug.
But remember, the slug no longer lives on fields.
It is just edge.Node.slug down below for `context`.
We have to make the same adjustment, removing fields and one of those extra dots.
And there we go.
That is it.
So when we're working with a CMS, there's a lot less for us to do behind the scenes to get things to work.
We removed a lot of code, and now we're actually gonna have pages for our `Contentful` posts.
Before we worry about restarting the server, let's head over to the blog posts template and pull in the new data.
So we still want to set up a query, though it's gonna look a little different than this one.
So I'm gonna comment out this one and will build up the new query from scratch down below.
We also have our blog posts int.
Everything in here is gonna be similar, though different enough where we're just going to start from scratch with this as well.
So now blog posts renders an empty page using the layouts component.
Let's make sure that we're at least seeing that page instead of the 404 page.
So in the terminal down below, I'm going to restart things since we have made changes to the gatsby-node file.
And once the server is up and running, if I refresh this URL I would expect to see something valid as a page should exist with this slug from `Contentful`.
Right here.
I give things a refresh, and this is a great first step.
We're no longer seeing that 404 page.
Now let's set up our query once again to fetch the `Contentful` data so we can actually render some stuff to the blog posts page.
Now it's gonna look similar to what we have up above, though obviously slightly different.
We'll start off the same exporting a new constant called query.
All of which is required in order for the Gatsby.
Parse er to, find your query and run it right here.
`GraphQL` Inside of templates strings.
We put our query.
This query is still going to get access to the slug variable, which we need We need to be able to target the individual post and slug is a string just like we had to find up above now inside of here.
Which particular query are we going to use over inside of `GraphQL playground` ? We had worked with all `Contentful` blog posts in the docs.
There is a way to get a single blog posts using `Contentful` blog posts.
So this will allow us to target a specific post.
And if we scroll down to the arguments, we can see there are quite a few different ways we could target a post.
I could target it by its title.
The slug the published date, the content and others in this case, we're gonna target it by its slug.
So we'll be using this slug argument and in there will use e que to find the slug using equality.
All right, let's set that up.
So over here, that's gonna be `Contentful` blonde post Setting up the argument.
We just talked about slug in their e que and the value would be whatever is stored on the slug variable.
So now we're targeting the correct post and we can fetch some data.
For the moment, we're just going to fetch the title and the published date.
Don't worry.
We are gonna render the body in this video, but it requires an extra step.
So let's get started with the simple stuff right here.
We'll have the title down below.
We'll have the published date which I'll also format using format stringfy and I'll provide the same format we had before.
I'll start off with the month than the day of the month and finally the year.
With this in place, we should have access to that data in our component down below.
Let's get these two pieces of information rendered.
We had the title in NH Wanna Header tag and we had the date inside of a paragraph.
So right here for us, that would be the following.
It's still `props`, doc Data exactly like what we had before.
This time, though, we have to go into `Contentful` blog posts and in there we have the title down below.
Let's do the same thing for the published date that's `props`.data.Contentful blog posts don published date.
And now if we save things, we should see these two pieces of data showing up over in the browser.
Right here.
I have the title and the correct published to date for this post.
And if I go back to the blog posts and select the other one, that data shows up as well, which is a great step in the right direction.
Now that we have this in place, we want to focus on getting the post content itself rendered.
And as I mentioned, it's not as simple as just grabbing a single field and then using that field like we did with the `html` field that we got with our markdown query from up above.
So let's explore this center.
Get started, will remove that redundant to query.
And what we're going to do is head over to `GraphQL playground`  real quick and take a look at another property we have access to.
So we're going to do is modify this old `Contentful` blog posts query we already have in place alongside of title slug and published date.
We're going to grab body now.
A body itself is not something we can directly grab.
There are fields inside of it we need to access.
And in this case, when we're working with a rich text field in `Contentful`, we want to grab json.
This returns a json String, which is a representation of the content in that rich text field.
So if we go ahead and set this up and run our query, it's gonna work, and we're going to see we get a lot more data in the response here for our first post.
We have body json and we can see the value is a complex structure.
We have all sorts of different fields and to raise and objects.
And somewhere inside of there we can see the data that we actually wrote out.
My post is here, and if we scroll down for the other post we can get, see that as well Now the reason they use this complex structure is to keep track of things like the paragraphs embedded assets like images, headers, Bold attacks, a Tallix and Mawr.
All of that is mapped out in this object.
Now the good news is that we don't need to manually parse this and figure out how to render things to the screen.
`Contentful` actually provides an `npm` library we can install, and it's going to take the json, and it's going to convert it into a set of `React component`s that we can render anywhere.
So it's not just specific to `JavaScript`.
The library is actually specific to `React`, which makes it really easy to work with.
So let's install this library and set it up.
It will be as simple as a function call right here.
We need to shut down the server, and I'll clear the output and we're going to install this library.
That's `npm` I.
It is at `Contentful` /rich text `React`.
Renderers.
So this is going to allow us to render rich text fields using `React`.
It provides a single function.
We're going to import it and call it, and that's going to allow us to get our rich text field showing on the screen.
Let's run the installation and, well, that's running up above.
We can focus on our import statement, so we're going to grab a single thing from that library.
It is a function, and it's called Document to `React` Components.
Now this is going to take in the json that we're grabbing from the API once we set that up over here and it's going to spit out `React component`s that we can render wherever we want.
Teoh.
Now we're gonna grab that from the library we just installed `Contentful` rich text `React` renderers.
Perfect.
Now that we have this in place, let's actually use it and it could not be easier to work with.
So first up, we do have to grab the data.
So that's body grabbing the json value and we use this down below.
Now what I'm gonna do is set up right after the paragraph, a set of `{}` so we can set up our function call.
We're gonna call document to `React` Components exactly like we imported up above.
And all we do is we pass in that document that json Data.
So for us, that is `props`.data.Contentful blog posts lips Got a little ahead of myself with the keys there and on here.
We want to access body and we want to access json.
With this line in place, we now should be able to see our post content on the screen.
Right here.
Let's restart the server with `npm`.
Run, develop.
We're going to check out that content.
Then we're gonna make more complex changes to the content in `Contentful` and check those out as well.
Right here.
Things are starting up, so I'll refresh my site.
And once we get the blog posts page, we can pick a post and we do see the content in a paragraph, which is awesome.
I have the content for the first post and for the 2nd 1 Now let's head over to `Contentful` and add some more complexity to those posts so we can see what we get down below in the body.
Let's add some more stuff below our text.
I'll add a header, a new section, and below that, I'll add some more text.
I love Gatsby with `Contentful`, and I'll go ahead and make Gatsby bold because I can.
And now we're actually going to add an image into the mix as well.
So right here we can Lincoln image using this plus button, we can link an asset.
Now.
We haven't added any images to `Contentful` Weaken.
Do that in two ways.
One.
We could go to the media tab and add them there, then link them.
Or we could just add it right here when we try to link it.
So there are no assets.
We haven't added any from the media tab, but we could just create one on the fly, so I'll click that button.
And here we just need to pick a title for this one.
I'll call this grass.
We have a description, and we have the actual file down below.
In this case for the file.
What I'm going to do is pick grass for my machine, which we downloaded earlier.
So I have that in my project that is Gatsby bootcamp Source.
Here we have posts.
Gatsby grass.PNG.
This is the one we had used in our markdown posts.
Now we're going to use it in our `Contentful` post.
So once we have things loaded in, we can publish this asset.
Once the asset is published, we can use the back button to pick it from the list.
And right here we can see it's already been put inside of our post.
It's all remove the extra little space down below, and now we have a little more complexity.
I have some text, a header and image and some more text down there.
Let's publish these changes and check things out over in the browser.
What I'm going to do is shut down the server and started up once again so it can fetch that new `Contentful` data.
And then we'll just rear ender.
Excuse me, refresh the post page to check things out.
So right over here, we want to go to the other post a `Contentful` blog posts.
I'll give things a refresh.
And what do we get? We get some of our new content.
I have a header which looks styled consistent with the rest of the site, and I have my other paragraph with the bold text down below.
The only thing I'm missing is my image.
By default, your images are not going to show up.
But the good news is that we can make a small change to how we're calling that document to `React`.
Components function to actually render those images right in line before we focus on changing the code.
Let's look at the new data for our complex post.
So right here I'm going to rerun the same query we had before where we grab that json and we can see that it's a lot longer than what we had in the past.
We have our initial paragraph with the text here.
Then down below.
We have our heading to with that text a new section and below that we have a very long and very complex object for the asset.
The image that we've embedded in that post.
If we scroll down, there's a lot of stuff we just don't care about and are not going to use, but we can scan for two things.
One is the title right here, Grass.
We're gonna use that as the all text for the image and then down below that we have the URL.
This is what we're gonna use to actually fetch and render that image.
Now, this object can be really overwhelming, as there's just a whole bunch of stuff we don't need to worry about, almost any of it.
All we're gonna do is drill into that object to grab those do values, and we're going to generate an image element like we would do in any other situation.
So let's leave the actual rendered post up in the background.
And over here, we're going to focus on drilling down to that data right here.
To do that, we have to set up an optional options object.
So a new constant options is gonna be an object.
And we pass that in as the second argument to that function the document to `React component`s function.
So I'm gonna pass that in now.
What we can do is customized how certain `node` types are rendered on here.
We start by setting up the render `node` property.
This allows us to override how specific nodes are rendered, and we saw various `node` types in that data.
For example, we saw things like paragraph and heading to We set that up as the property, saying That's the type we want to customize In our case, the type we want to customize has a-in it.
So I have to wrap that name inside of quotes that is embedded asset black and all we do is provide as the value a function to run were customizing how the `node` is rendered.
We get the `node` data passed in and we return some `JSX`.
In this case, all we're going to do is return an image.
Now we want to set up values for the altar text end for source.
So let's start to get that done right here.
I'm going to create standalone variables for both of those things, so it's a little easier to work with.
We'll have Ault.
Then I'll have ur l down below and both of these are going to get applied onto the image.
Ault will get its value from the altar variable.
Then when we set up the source for the image, the value will come from you, R l Now, in order to get the correct values we need to drill into the Node, which is that really big, complex object.
So let's check that out in `GraphQL playground` .
Over here, we have our complex object.
There's quite a bit to it.
We have the data we want, and then we have a bunch of other stuff we just don't care about.
Now, our `node` is this object right here.
It starts with the data property.
We have data.target.
Now, we also have assists, which we're going to collapse.
And when we collapse, that will see the two fields we're looking for.
So this object is the Node, which means we need `node` data, Target Fields, title E n us for the altar text, and then on fields.
We need file e N u S URL for the URL.
Now it's never fun to drill into a complex object like this, but that's just where our data lives, and it's gonna be necessary just a single time.
So let's get that done over here.
We'll start with the altar text.
That's Node.data.target From there it was fields.title and we're grabbing the title in the locale.
I hav e n us.
If you see a different locale over in `GraphQL playground` , you want to go ahead and use that and then down below, we're going to grab you are l This is gonna be `node` doc data.target.fields Here it was file followed by the locale E N us, followed by URL.
Now we should be able to see both of those things showing up in the image element, and the end result should be a rendered image in the browser.
And that is exactly what we're getting right here.
We have all of our post content showing up, including the image, and all of this is managed from `Contentful`.
So when we're working with `Contentful`, we can easily manage our content or someone else who owns the site can manage the content using this nice interface and behind the scenes, they don't need to worry about changing code or changing markdown files or changing anything else.
Now, once again, `Contentful` is not for everybody, and neither is markdown.
It's really up to you to pick what makes the most sense for you and run with that.
All right, that's it for this one.
Let's continue on into the boot.
Camp is almost done.
There are just a couple of things that I didn't get a chance to cover so far that I want to cover in the next lesson or two, so let's get started.

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

