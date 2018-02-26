---
layout: post
title:      "THUNK: Some Thoughts"
date:       2018-02-26 15:14:48 +0000
permalink:  thunk_some_thoughts
---

You've got Redux going in your app, but your needs are more than they were before, and what a simple JS object provides? Doesn't cut it. Enter middleware, a neologism that, I believe, combines the word 'middle' with the word 'beware', because: a) it goes in the middle of two things (i.e. a server call between client and server), and b) beware, you're about to mess something up. At least at first. Later, less so. 

Thunk, in short, returns a function along with an action creator when dispatching an action via Redux. To be sure, Thunk is not necessary in all instances (i.e. simple dispatch actions that require nothing more than a case to switched on), but in other instances it makes what would be an incredibly complicated problem fairly simple. By combining with the store's dispatch, the returned function can, through Thunk, make multiple dispatch calls, expanding on Redux for a much more versatile return than the plain, old JS that would otherwise be returned.

For example, in my portfolio app, I'll implement mulitple dispatches in one call, allowing me to both make a request to the server side, and through a separate call, erase the values entered into a form on the client side.  At the same time, it 'syncs' up actions that otherwise could cause problems.

That is: adding in Thunk essentially helps to synchronize the so-called "asynchronized actions." In the time between a server request (i.e. Fetch) and the response, the code following the Fetch call cannot properly execute because it will hinge on information not present on the client-side. The difference between milliseconds and half-seconds is plenty to make your app break. Enter the '.then' call, which will prevent the next action from occuring until it's ready. No doubt there are some alternatives to the '.then' call, for example, a function call for a set amount of time to pass before the next action could in some instances serve fine. I'll be sure to implement something like this in some instances, i.e. displaying a timely message for a set amount of time before having it automatically disappear. But when the the amount of time required is unclear, like with a fussy server that just won't respond in a set amount of time, synchronizing the code becomes a must. 
