---
layout: post
title: How To Create A Basic Web Component In Google Canary
date:   2014-02-07
categories: posts
---

##Introduction

Before getting started, make sure to read through [this article](/posts/2014/02/06/how-to-inspect-shadow-dom-in-google-canary-to-style-a-video-player.html) that talks about some of the default settings you'll need in Google Canary.

##Basics

A web-component consists of 3 parts:

1. Templates (```<template>```)
2. Shadow DOM
3. Mutation Observers, Object.observe()

Google Canary also gives you three different ways to create a web-component:

1. Declarative
2. Imperative
3. Extending

We'll go into each one in further depth but in general, every web-component has a DOM structure that is a ```<template>``` element wrapped by an ```<element>``` element.

```
<element>
	<template>
	</template>
</element
```

##Declarative Pattern##

In the declarative pattern, you create a .html file that contains the ```<element>``` and ```<template>``` as well as any ```<style>``` attributes and other DOM elements. You will reference this new DOM element by the value you assign to the name attribute in the ```<element>``` tag.

```
<element name="my-new-element">
	<template>
		<style>
			div { color: blue; }
		</style>
		
	</template>
</element>
```