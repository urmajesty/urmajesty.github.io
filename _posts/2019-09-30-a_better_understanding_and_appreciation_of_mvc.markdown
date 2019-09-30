---
layout: post
title:      "A better understanding and appreciation of MVC"
date:       2019-09-30 04:42:25 +0000
permalink:  a_better_understanding_and_appreciation_of_mvc
---

As I started my 2nd project with is Sinatra, I was very unsure of myself at first, and in hindsight, it was probably because I didn’t fully understand what MVC was.  Actually, I knew what the action was, I just didn’t fully understand how it worked, and the details that make it so cool.   

I first started to study MVC in my coursework.  Normally if my understanding is not soldified, I just go to a different source to get information.  Well once video gave a restaurant analogy, where the Cehf is the controller, the waiter is the view, and the chefs’ tools are the model.  That was very confusing to me as couldn’t grasp the complete scope of the how and why.  I’m always seeking to understand, and I am very curious, so I wasn’t fully satisfied with that broad of an analogy, I needed to know why it worked.  So, I told another developer about the restaurant analogy, and they compared it to a train system.  Since I didn’t fully understand at that time either, that analogy went over my head also.   

 

Finally, I decided to do my own research.  So, I researched videos coupled with written explainations.  and this is what I found:  

The model is connected to the database, it interacts with the database and pulls info from the database, it hands it over to the controller.  The controller doesn’t talk to the database directly, only the model.  The controller tells the model what it needs, then the model gives the controller what it asked for.  The model never talks to the view directly.  The view only listens to the controller.  The controller tells the view what to do, the view listens and follows commands.  The controller is essentially the commander.  it is the most essential because it communicates with both the model and the view.   To think of it a different way, if I’m writing code related to the database section of the flow it’s probably going to be the model, writing code that processes to and from the database to the server it’s probably going to be the controller, and if I’m writing code that has to do with frontend that is going to be viewed in the client’s browser, it’s going to be the view.  

 

The MVC is actually very important, and is very widely used.  Since, I’ve learned more about it, I’ve gained a greater appreciation for it, because, just understanding its flow will make web design much easier.   
