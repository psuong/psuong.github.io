---
title: "Scaffolding in Development"
date: 2019-04-12
draft: false

summary: "Thoughts on development"
---

# Scaffolding in Development

So I preferably enjoy working with low level APIs instead of high level APIs. The main reason behind that is the amount 
of control I have as a developer, especially on creating the functionality I need. So if there is an alternative API 
which provides a lower level solution than a high level API which does exactly what I need…

I would still go for the lower level solution, even if I have to recreate the same functionality as the high level API.

Now truthfully, that sounds like I’m just redoing the same work for the same functionality I need. But let’s step back a 
little bit and think about some of the benefits of a lower level API.

## Scaffolding

A low level API which allows you to chain functions together to create the desired outcome you need provides a scaffold.

Scaffolds in construction are temporary structures to aid in the construction or repair of a building or structure. But 
as a bystander you can clearly see how construction workers are constructing the building and their methodology. Take a 
look at the image of a bamboo scaffold used in Hong Kong below, you can clearly see how workers are going about the billboard.

> Image credit goes to Wikipedia, with photo taken by Greg Hume
![hong-kong-bamboo-scaffold](https://upload.wikimedia.org/wikipedia/commons/thumb/4/42/CantileverScaffold.jpg/1280px-CantileverScaffold.jpg)

So relating back to development, scaffolds can not only give you the guidelines to create a high level API, but also the 
logical reasoning and the specific data you’ll need to solve the problem you have! An API/framework that provides this 
is invaluable to you as a developer!

## A Common Scenario throughout Development

Imagine as your developing a feature using some API. Now this API gives you an out of the box solution which works and 
solves the problem you’re trying to solve with a single function! Now that’s a whole lot of time saved and you can now 
move onto the next feature.

But... some time down the line you need to tweak a functionality within the API to allow you do to do something a bit more 
grand. You look through StackOverflow, a forum, or Github issues to get some kind of idea on how to tweak the API’s 
pipeline, but then you realize that currently there is no way to solve your particular solution and the developer(s) 
of said API wouldn’t support said feature until X months later.

It’s a terrible situation to be in and you’ll likely plan accordingly to compensate for the situation.

## Conclusion

Now if you’re an API designer, you should not only think about the high level functionalities your developers will likely 
use. You should still support low level operations such that developers can really extend your API and make something unique 
you’ve never even thought of supporting!

Visibility in the framework encourages that developers care about what they’re using!

Thus, a good API is one that can be used multiple times in various similar situations to solve problems many developers face.

<script src="https://utteranc.es/client.js"
        repo="psuong/psuong.github.io"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>