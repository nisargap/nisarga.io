---
title: "Why Hugo Is My Blog Engine of Choice"
date: 2017-09-24T15:49:29-04:00
subtitle: ""
categories: ["general", "technology"]
---

I had been thinking about starting a development blog for a very long time and was looking for a solid blog engine or static website generator to make the process of creating my blog and getting content out there as quickly as possible a bit more streamlined. In the past I had used [GatsbyJS](https://github.com/gatsbyjs/gatsby) which had suited my needs but this time around I felt like I needed something that was different. Gatsby is definitely a great blog engine but getting the compatibility right with various plugins because of the fact that it was React took some time to get used to.

## Enter Hugo
I have been working with Go for several months now and was impressed by the language's reliability and ease of use in server-side situations. At my startup the main language of choice for server-side development is Go. So I thought to myself perhaps there is a popular blog engine that is created with Go - this is what led me to Hugo.

## Why Hugo?
There are definitely many options for blog engines. One of the most popular ones that is supported by [GitHub](https://github.com) is [Jekyll](https://jekyllrb.com/), Jekyll is certainly a great option and it is easily extensible in the sense that plugins and themes can be made easily. Jekyll is certainly extremely popular as well with over 31,000 stars on their [GitHub source repository](https://github.com/jekyll/jekyll) vs. Hugo's 19,000+.

The primary reason I chose Hugo over Jekyll is that Hugo was a lot faster in generating and serving up content for testing. Jekyll is built primarily with Ruby which is an interpreted language, Hugo on the other hand is compiled Go code. Due to the nature of Hugo being written in Go, it is also available on multiple platforms whereas Jekyll is only available on those platforms that support Ruby.

## How easy is it to get set up with Hugo?
On macOS, getting Hugo installed was as simple as doing `brew install hugo`. You can learn more about [Getting Started with Hugo](https://gohugo.io/getting-started/quick-start/) on their official website.

## Can you install and create themes?
It is very easy to install themes to Hugo, most themes which you can find [here](https://themes.gohugo.io/) are simply installed by git cloning their repo into the `themes` directory. It is also not difficult to modify these themes or create your own, you can find all of that information on the official website as well as theme specific repos as well.

## Startup? Need a static website?
If you're a startup and need a static website, Hugo might be your answer. It is very easy to get things up and working with your website with Hugo.
