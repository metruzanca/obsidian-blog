---
title: Implement type-safe modals in React
slug: react-modals
date: 2023-05-16T15:36:24.856
description: Guide on using React features to build modals with great typescrpt support
tags: ['react', 'software patterns', 'programming']
draft: true
---

## [DRAFT]

After having done this a few times, I've decided to make an article.

This guide makes no assumptions of your chosen state management system and uses native react in its implementation. (contexts, useState, portals?)

The goal is to implement a Modal component that can be opened from any other part of the app but maintains type information so that the opener can pass data to the modal.

As a bonus, I will be giving some recommendations on how to guarentee your modal meets ARIA standards for usability.

