---
layout: post
title: How To Inspect Shadow Dom In Google Canary To Style A Video Player
date:   2014-02-06
categories: posts
---

<a href="https://news.ycombinator.com/submit" class="hn-button" data-title="How To Inspect Shadow Dom In Google Canary To Style A Video Player" data-count="horizontal">Vote on Hacker News</a>

<style>
.video-demo ^ div {
	background: beige;
	margin: 0;
}
.video-demo ^ div div {
	padding: 0;
}
.video-demo ^ div div div {
	background: navy;
	border-radius: 0;
	padding: 0;
}
.video-demo ^ input[type="range"] {
	background: antiquewhite;
}
</style>

So, you have to use Google Canary in order to see what's happening here. [Are you?](https://www.google.com/intl/en/chrome/browser/canary.html)

Make sure you're setup to view this tutorial by typing about:flags into the Google Canary URL bar and then enable two currently disabled flags: 

1. Enable Experimental JavaScript Mac, Windows, Linux, Chrome OS, Android Enable web pages to use experimental JavaScript features. #enable-javascript-harmony.
2. Enable experimental Web Platform features. Mac, Windows, Linux, Chrome OS, Android
Enable experimental Web Platform features that are in development. #enable-experimental-web-platform-features

Once you've done so, restart your browser and come back to this page.

Let's talk about the ```<video>``` tag as a common example where the shadow DOM is not currently visible to web inspection:

```
<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  Your browser does not support the video tag.
</video>
```

But if you've ever used the video player, you know that the browser is rendering a lot more DOM elements than what appears in the code above. In Google Canary, navigate to TOOLS and then on the GEAR box to open a menu that'll let you select Show Shadow DOM:

![Show Shadow DOM](/images/2014-02-06-web-components-example/01.png)

<video controls="controls" 
       class="video-stream" 
       x-webkit-airplay="allow" 
       src=""></video>


 If you inspect the video player above, you'll should now see something like the following image:

 ![Inspecting Shadow DOM](/images/2014-02-06-web-components-example/02.png)

Let your CSS inspiration do the rest!

<video controls="controls" 
       class="video-stream video-demo" 
       x-webkit-airplay="allow" 
       src=""></video>

In Google Canary, the above video player looks like this:

![Google Canary Video Player](/images/2014-02-06-web-components-example/03.png)

Here are the styles:

```
<style>
/* background of the entire video */
.video-demo ^ div {
	background: beige;
	margin: 0;
}
/* background of the control bar */
.video-demo ^ div div {
	padding: 0;
}
/* background of the controls */
.video-demo ^ div div div {
	background: navy;
	border-radius: 0;
	padding: 0;
}
/* the range input, for example */
.video-demo ^ input[type="range"] {
	background: antiquewhite;
}
</style>
```

To enter a Shadow Dom, you must specify the CSS selector of the element which is the root of the shadow dom followed by either a cat ^^ or a hat ^. The cat ^^ allows you to select any element within the shadow dom, regardles its inheritance. For example .video-demo ^^ div would select all internal divs including divs within other nested shadow doms. The hat ^ will enter the shadow dom once. For example, .video-demo ^ div selects the first child div node upon entering the .video-demo shadow dom.

Once you figure out where the dom elements are located, the styling is in your control.
