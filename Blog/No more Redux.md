---
title: No more Redux
slug: no-more-redux
date: 2023-05-03T10:20:42.502
description: Redux is a great library, but most applications don't need it. 
tags: []
draft: true
---

> Gippity drafted intro

>[!info]- Prooompt
>The title is going to be "No more Redux" and is going to be basically talking about why most apps don't need redux and my advice for approaching building apps without it.
> 1. The topic of the blog post: Building react apps without redux.
> 2. The purpose or goal of the blog post: to show that you can build apps without redux and they end up making the apps a lot leaner and easier to work in.
> 3. The target audience for the blog post: React developers who are most likely tired of redux's boilerplate
> 4. Any specific points or ideas to include in the introduction: Redux was a great tool but we've got hooks and context now

Not sure if relevant for an introduction but I want to mention how putting all our data into one single store is no longer as common of a pattern as it used to be. Later on I also want to mention how we shouldn't use redux as a cache. Often I notice people storing req responses in redux, when the browsers nowadays have great caching and we can use modern strategies like "stale while revalidate" (SWR). (either thru swr package or react query)

If you're a React developer, you've likely encountered Redux at some point in your career. Redux was once hailed as the go-to state management tool for React applications. However, with the advent of newer React features like hooks and context, Redux is no longer as essential as it once was. In fact, many apps can be built without it altogether.

In this blog post, we'll explore the idea of building React apps without Redux. We'll discuss why Redux's boilerplate can be tiring for developers, and how not relying on Redux can make your apps leaner and easier to work with. We'll also touch on how the pattern of putting all of our data into one single store is no longer as common as it used to be.

Moreover, we'll address the idea of not using Redux as a cache. Although it may seem tempting to store request responses in Redux, modern strategies like "stale while revalidate" (SWR) offer better solutions. We'll introduce some popular packages that implement these strategies, such as SWR and React Query.

If you're ready to explore the world of building React apps without Redux, read on!

