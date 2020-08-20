---
title: "9. GraphQL Playground"
description: "The Great Gatsby Bootcamp"
shorttitle: ""
publishDate: "2020-08-20"
ENTRYTYPE: "Gatsby Bootcamp"
series:
- The Great Gatsby Bootcamp
tags: 
- Transcription
- Tutorial
- Youtube
category: 
- Gatsby.js
image: 
pinned : true
draft: false
hideToc: false
enableToc: true
enableTocContent: false
copyright: "All rights reserved"
---

Welcome back in this video as promised.
I just want to take a couple of minutes to explore how you can set up an alternative to `GraphQL` This is the default IDE for working with your `GraphQL` API in Gatsby.
But Gatsby also comes with support for another IDE.
No one has `GraphQL` playground.
It's a lot newer and comes with a much nicer feature set, including some what I would consider essential features.
Now to swap out `GraphQL` for `GraphQL playground` , all we really need to do is set an `environment variable` on our machines.
And we're going to do this in a cross-os compatible way.
So right here we can close all open editors.
We don't even need the source directory for this video.
And we're going to focus on `pacakge.json`.
Now, this could be as easy as setting up the `environment variable` right here in the script.
The problem with that is, it's not cross-os compatible, so instead will create an `environment variable` in a separate file, which will load in a very common approach.
So right here a new file in the root of the project called `.env.development` in here, we're going to define our key equals value pairs for the `environment variable`s.
Now, in our case, we just need one.
The name is `Gatsby_GraphQL_IDE` and the value we want is playground.
That's going to enable `GraphQL` playground support giving us that new tool in the browser.
So now that we have this in place, the only thing we need to do is actually load this file in when we're using the development server.
And to do that will use the very popular `env-cmd-npm` package down below in the terminal.
I'm gonna use `control`, see to shut down of the development server.
Then we'll use `npm install` with the Save Dev flag.
Since this is a dependency we only need in development and from here, we're going to go ahead and set up the following `env-cmd`.
So let's go ahead and install this, and once it's installed, we're actually going to work it in to our `package.json` script.
So inside of `package.json` What are we going to do? We're going to change the development script right here.
It's gonna use e n v c m d to load that `environment variable` file in.
Then it'll run Gatsby, develop right here.
We're gonna modify this script that's going to be `env-cmd` the new tool we just installed.
And from there over going to do is provide the name of the file we've created `.env.development` and we're done.
Now it's going to load those `environment variable`s in then run the Gatsby server.
So let's save `package.json` in the terminal down below.
We're going to start it up like we've done before.
`npm run develop` And once it's up and running over going to do is refresh the `GraphQL` page over here and we should see something quite different.
I'll go ahead and give it a refresh, and we can see it's loading an entirely new interface.
Here we have `GraphQL` playground.
Now it comes with the same set of features.
I type my query over here.
I can run it and see their response, but it's a lot easier to work with.
We could manage tabs so we can have multiple queries at the same time.
We also have a nicer set of docs that, in my opinion, is much easier to work with.
So here we have site.
Then we can see all the arguments and our fields below `sitemetedata.title` and `.author` so we can see everything in one shot making it a lot easier to construct the queries we want to perform.
So that's it for this video.
I just wanted to show you how you could set up support for this new tool going forward.
I'll see you in the next one.
