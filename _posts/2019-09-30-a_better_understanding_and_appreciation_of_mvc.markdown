---
layout: post
title:      "A better understanding and appreciation of MVC"
date:       2019-09-30 00:42:26 -0400
permalink:  a_better_understanding_and_appreciation_of_mvc
---

As I started my 2nd project with is Sinatra, I was very unsure of myself at first, and in hindsight, it was probably because I didn’t fully understand what MVC was.  Actually, I knew what the action was, I just didn’t fully understand how it worked, and the details that make it so cool.   

I first started to study MVC in my coursework.  Normally if my understanding is not soldified, I just go to a different source to get information.  Well once video gave a restaurant analogy, where the Cehf is the controller, the waiter is the view, and the chefs’ tools are the model.  That was very confusing to me as couldn’t grasp the complete scope of the how and why.  I’m always seeking to understand, and I am very curious, so I wasn’t fully satisfied with that broad of an analogy, I needed to know why it worked.  So, I told another developer about the restaurant analogy, and they compared it to a train system.  Since I didn’t fully understand at that time either, that analogy went over my head also.   

 

Finally, I decided to do my own research.  So, I researched videos coupled with written explainations.  and this is what I found:  

The model is connected to the database, it interacts with the database and pulls info from the database, it hands it over to the controller.  The controller doesn’t talk to the database directly, only the model.  The controller tells the model what it needs, then the model gives the controller what it asked for.  The model never talks to the view directly.  The view only listens to the controller.  The controller tells the view what to do, the view listens and follows commands.  The controller is essentially the commander.  it is the most essential because it communicates with both the model and the view.   To think of it a different way, if I’m writing code related to the database section of the flow it’s probably going to be the model, writing code that processes to and from the database to the server it’s probably going to be the controller, and if I’m writing code that has to do with frontend that is going to be viewed in the client’s browser, it’s going to be the view.  

To sum put it in technical terms:  The Sinatra controller’s  job is to handle all the incoming requests, responses, and routing.

In the application_controller.rb file, I created a class for the application that inherits from Sinatra::Base. Sinatra::Base gives the app a Rack-compatible interface that can be used via Sinatra’s framework.
To get the controller set up for the file structure. I added code that tells Sinatra where to find the folder (Sinatra looks for it in the root by default).  After the code, I wrote routes.

Routes are what connect requests from a browser to the specific method in your app (in the Controller) that can handle dealing with the request and sending a response. For example, on the simple side, a route might just show, or render, a basic HTML view. In my project  route might receive data submitted via a form, say a course title and its subject, process that data, and then show the completed post–a new course, which is just another HTML view.

Some basic GET request could look like this:
The get '/' do and get '/edit' do lines correspond to the URLs in the browser. So, if the domain is teachent.com, get '/' do refers to that root domain. get '/edit' do would refer to teachent.com/edit.
The erb :index and erb :about lines tell the controller which view file, in this case an embedded ruby file, in the views folder to get and show. So we would need to have a index.erb and an about.erb in a views folder for this to work.
The view file is represented by a symbol of the same name in the route. Sinatra assumes that the view templates are all directly under the /views folder.

Dynamic routes can handle a HTTP request based on attributes in the URL. These attributes are represented by represented by symbols coded directly in the route and their values are easily accessible through the automatically generated params hash, so they can be used to look up or process data.
For example let’s say that in our course site at teachent.com you want to be able to get individual courses via their id in the URL (e.g. teachent.com/courses/:id . Obviously, we wouldn’t want to write out a route for every single course and its id. A symbol is used instead: get '/courses/:id' do, where the :id could be any number. The value of :id is then accessible through params[:id].  This could be used to grab the proper course:  The params hash was used to look up a course from the database. That course was then assigned to an instance variable. Instance variables in Sinatra are used to pass data to our views.

Whenever you create an instance variable with in a controller route, that variable is available within the corresponding view file. Note that the instance variables will not be available within other routes in the controller; only the view specified within a single route.
This assumes you also have a course model with in your app/models folder, that could look something like this:
The user has attributes like a course and subject, so once the user object has been assigned to @user in the controller route, we can weave all those attributes right into our ERB template:
We can even iterate through data in views. For example, let’s say we want to show all the courses in the course index page. First, we might assign all the courses into an instance variable in the teachent/index route:
Then, iterate over the courses in the teachent/index.erb template.  That also linked to the course page using the course id, which will be processed by the get '/teachent/:id' route. 
Note that these instance variables do not need to be objects from models; they can be any variable that you want to assign and use in the view.


 Receiving user-input data from forms is the key to building web apps.  Next I needed to correctly hook up forms to the controllers. So in order to do this I need to create a basic form and route that will render it.
Setting up the route is as easy as connecting the URL for a new course post to the proper view, which is going to contain our form. In this case, let’s say we want the url to be teachent/new:
The <form class="" action="/teachents" method="post"> line is very important for setting up the route. The action attribute tells the controller what part of the code (that is, which route) should handle the form. Think of it like an address. The method attribute is simply how it’s going to get there, in this case via POST.
The other important part is the name attribute on each input tag, as this is what sets up our params hash. I’ve put name="course", & name="subject", It will produce a hash.  When the form is submitted, this data is now available in a params hash!   So I set up the post route and use params to make a new course...  but I ran into a problem because once the form has been submitted, the user is going to be shown a blank page.  That's why post is important.  POST just sends the information, it doesn’t display it afterwards. After the course data has been processed and completed, it makes sense to show the finished course to the user. Sinatra has a  redirect method that will take the user to another page, in this case the course show page. Add it to the route to get this.
The redirect "/users/#{@user.id}" is going to send it to our user show route, get '/users/:id', so the user can be proud of their new creation.



The MVC is actually very important, and is very widely used.  Since, I’ve learned more about it, I’ve gained a greater appreciation for it, because, just understanding its flow will make web design much easier.   
