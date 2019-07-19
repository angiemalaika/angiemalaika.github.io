---
layout: post
title:      "SINATRA, CRUD, MVC "
date:       2019-07-19 02:21:39 +0000
permalink:  sinatra_crud_mvc
---

Sinatra is a Domain Specific Language implemented in Ruby that's used for writing web applications. Created by Blake Mizerany, Sinatra is Rack-based, which means it can fit into any Rack-based application stack, including Rails. It's used by companies such as Apple, BBC, GitHub, LinkedIn, and more.  

I am a student at flatiron school and this week, I learned about Sinatra. In Sinatra you dive deep with the major concepts of MVC, a system for building web applications that governs 90% of the worlds' apps. You are required to manually set up routes and connect them to other pieces of your application. Without this manual setup, your application does not automatically know how to communicate with your database or what HTML files to load in the browser. And even more importantly, without a manual setup, you lose connection to the major components of a web application, and in particular, all the moving pieces of MVC. 


**Routes**

***Example: ***

get '/medicines' do

    # some code to get the medicines and render the correct HTML file
		
end

***Refactored:***

get('/medicines') { some code }


The get method is called with an argument of '/medicines' and is invoked with a block. 

A** *route* **is a method paired with a URL -matching pattern and each route is associated with a block:

  get '/' do
      .. show something ..
  end

   post '/' do
       .. create something ..
   end

    put '/' do
        .. replace something ..
    end

     patch '/' do
          .. modify something ..
     end

     delete '/' do
          .. annihilate something ..
      end

     options '/' do
        .. appease something ..
     end

      link '/' do
        .. affiliate something ..
      end

      unlink '/' do
         .. separate something ..
      end


Things to remember about routes: 


1. Routes are matched in the order they are defined. The first route that matches he request is invoked.

2. Routes with trailing slashes are different from the ones without:

     #get '/foo' 
          #Does not match "GET /foo/
      #end

3. Route patterns may include named parameters, accessible via the params hash:

     get '/hello/:name' do

         matches "GET /hello/foo" and "GET /hello/bar"
          params['name'] is 'foo' or 'bar'
          "Hello #{params['name']}!"

         end

4. You can also access named parameters via block parameters:

       get '/hello/:name' do |n|
          matches "GET /hello/foo" and "GET /hello/bar"
             params['name'] is 'foo' or 'bar'
                   n stores params['name']
                    "Hello #{n}!"
                   end

5. Routes may also utilize query parameters:

        get '/posts' do
               **  # matches "GET /posts?title=foo&author=bar"**
             title = params['title']
             author = params['author']
             **# uses title and author variables; query is optional to the **/posts route
         end


**MVC**

The Model-View-Controller paradigm is a popular way of building frameworks for web applications - it provides a separation of concerns where groups of files have specific jobs and interact with each other in very defined ways. In a nutshell:

        **Models:** The 'logic' of a web application. This is where data is manipulated and/or saved.

       **Views:** The 'front-end', user-facing part of a web application - this is the only part of the app that the user interacts        with directly. Views generally consist of HTML, CSS, and Javascript.

        **Controllers:** The go-between for models and views. The controller relays data from the browser to the application,        and from the application to the browser.

        **Active Record and Sinatra **


        ***CRUDE and MVC process ***

        ***Create* **: Model.create


          #get 'models/new'  =>   new.erb   =>   post 'models'
   

           ***Read* **: Model.all/Model.find(id_number)

           #get '/models'  => index.erb

           get '/models/:id' => show.erb 


            ***Update*:** Model.update 

            get '/models/:id/edit'  => edit.erb  => patch '/models/:id' 


             ***Delete: ***Model.destroy 


              get '/models/:id  => show.erb  => post '/models/:id/delete'



I hope this gives you a guide to what to expect in your project. LATER! 

sources : [learn.co ](https://learn.co://)



