---
title: "9. GraphQL Playground"
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
    src="https://www.youtube.com/embed/8t0vNu2fCCM?start=6432"
    frameborder="0"
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen
  >
  </iframe>
</div>

## 本文

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

