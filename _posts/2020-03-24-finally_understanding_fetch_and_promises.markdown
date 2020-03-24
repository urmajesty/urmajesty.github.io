---
layout: post
title:      "Finally understanding Fetch and Promises*"
date:       2020-03-24 02:35:01 -0400
permalink:  finally_understanding_fetch_and_promises
---


####  *...using analogies and not so technical verbiage

Fetch and Promises had my mind boggled for a bit before I did my research.  So, I'm writing this blog post for those who may have a different learning style and is having trouble grasping the concepts.  

First, to understand fetch I had to know a little about AJAX (Asynchronous JavaScript) .  The short version is, that sometimes we want to do operations, and the functions that perform those operations don’t always run in order and/or sometimes they take a while to load.  That being said, you may have a function that takes a while to load, and the other functions can’t proceed until the one before it is done.  

**AJAX Analogy Alert!** It’s kinda like the functions have to wait in a long line, at the grocery store, where every other function before it has at least 30 coupons to use.

![](https://i.imgur.com/02a6qXs.gif)

Or, like the functions are in line to get off at an highway exit, and the function police are doing traffic stops and thoroughly searching every vehicle one at a time before the next can pass.

![](https://i.imgur.com/twBss8d.gif)

In a totally different real-life scenario,  if you have 2 functions,  and part of the operation is in the 1st function and the other part to complete the operation is in the 2nd,  the 2nd function could run before the 1st.  If that happens, the 1st would come back as undefined, and the entire operation would fail.   When it pertains to code for a website, that could mean users look at a blank screen, for the full time it takes the operation to be processed and the content to be rendered to the browser.

That’s where Promises come to the rescue.   Promises are a style of code the AJAX technique.  Promises, promise that an operation will be completed and holds the promise of a resulting value for that operation.  

**Promise Analogy Alert!**  It’s like 2 friends, Promise and Operation, are in a grocery store checkout.  When it’s time to pay, Operation realizes he forgot his wallet.  So, his friend Promise agrees with the cashier, to let Operation leave with the groceries (render to the browser)  if the Promise stays there and promises the operation will return later with the payment (the data), thereby allowing Operation, to proceed to work as planned.  

![](https://i.imgur.com/9lgfchS.gif)

Once you understand Promises, understanding fetch is easy.

Fetch is essentially a function that takes URL of your target website as it’s parameter(argument), and returns a Promise of the website’s data.  Then, (.then) if it’s successful, the response(“data”) becomes a function that returns the response (the promises of data) in JSON format.

```
fetch('http://interestingwebsite.com')
  .then((response) => {
    return response.json();
  })
```

You will have to create a 2nd .then with a function passes the JSON Promise as a parameter so that you may get your actual parsed response body (JSON objects).

```
 .then((data) => {
    console.log(data);
  });
```

TADA!!!

![](https://i.imgur.com/wGisQ0G.gif)


I hope this helps. 

