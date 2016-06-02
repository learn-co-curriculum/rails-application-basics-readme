# Rails Application Basics

## Objectives

1. Install the Rails gem
2. Generate a new application with `rails new`
3. Properly name a newly generated Rails application by using and naming both the app constant and directory
4. List the information that goes into the folders and files within a Rails file skeleton
5. Start a local server using the Rails cli
6. Load the local site from port 3000 in a browser
7. Start a Rails console with the Rails cli

[View this lesson on Learn.co](https://learn.co/lessons/rails-application-basics-readme)


# Ruby on Rails Introduction

Welcome to the world of Ruby on Rails development! With over a decade of open source contributions, Rails has evolved into one of the most powerful web application frameworks available. Before we can start building applications it is important to first understand what the Ruby on Rails framework is.. and what it's not.


## Why Use a Framework?

If you wanted to put surround sound in your house, would you go and spend years researching how to best fabricate speakers, learn how to transfer sound through wires, weld your own sound board, and create from scratch every other component that would be required to have a surround sound system in your home? Most likely not. Instead it would be much smarter and more efficient to purchase a surround sound system from an organization that already put in all of the research and development work to create a professional system.

In the same way, when it comes to building a web application it would technically be possible to build out all of the functionalities yourself, but it's typically a better idea to leverage a system that has already spent over a decade developing the tools necessary for getting applications built.


## What is Ruby on Rails?

* **A web framework** - A web framework provides developers the tools they need in order to build applications. While every application is unique there are certain components that can be found in almost every application, such as: routing, asset management, database connections, and the list goes on. A good web framework gives developers these baseline tools so that they don't have to create the base application functionality for each new project.
* **A Ruby Gem** - At its core, Ruby on Rails is simply a set of Ruby code libraries, and since the entire codebase is open source you have the ability to review the framework to better understand how it works.
* **A MVC framework** - MVC stands for Model-View-Controller, this essentially means that Rails takes advantage of the popular application architecture that helps developers naturally separate concerns and organize their applications properly. This setup encourages a specific set of conventions, such as placing the logic for the application in the model files, the code flow in the controllers, and the views to simply display content to the user.

*On a side, but very important, note: don't worry if some or all of what we just reviewed seems foreign. We'll be covering everything in detail in future lessons, so don't worry if it all feels a little overwhelming*

## What Ruby on Rails is not
* **A programming language** - This is one of the most common misconceptions. Ruby on Rails is not a programming language; instead it is a set of code libraries built in Ruby.
* **A slow framework** - Due to the fact that Rails is one of the most straightforward frameworks to learn, it can lead to a number of poor coding practices from beginners. However if built properly, Rails projects can be as fast as any other framework. Furthermore, with Rails service based architecture it makes it a perfect candidate for microservice applications, which can be some of the fastest and best performing applications on the web.


# Creating Your First Rails Project

*Before you continue, this assumes that you have Ruby, RubyGems, and Bundler installed on your system*

## Installing the Rails Gem

As mentioned above, Rails is simply a Ruby Gem, to install it on your system, run the following command in the terminal of your computer:

```gem install rails```

Depending on your system configuration you may need to prepend the command with ```sudo``` to install the gem as the root user. Once the gem is installed you can create Rails applications!

## Generating a New Rails Application

Our application is going to be called BlogFlash. To create the application, run the following command:

```rails new blog-flash```

There are a number of common naming conventions for Rails app names. Typically you will want to use all lower case letters, separated by '-', as shown in our ```blog-flash``` naming structure. In the same way that there are rules for naming methods, variables, classes, etc. in Ruby, there are naming rules for application names. Since the application name is used as the app constant and throughout the application, the best approach is to keep your naming simple and to follow a standard naming practice.

## Rails File Structure Overview

Since you will be working with this file structure on a daily basis, it is very important to understand and become familiar with the file system. Below is a breakdown for each directory:

* **app** – contains the models, views, and controllers, along with the the rest of the core functionality of the application. This is the one directory where you can make a change and not have to restart the Rails server. The majority of your time will be spent working in this directory. In addition to the full MVC structure, this directory also contains non Ruby files, such as: css files, javascripts, images, fonts, etc.

* **bin** – some built-in Rails tasks that you most likely will never have to work with.

* **config** – the config directory manages a number of settings that control the default behavior, including: the environment settings, a set of modules that are initialized when the application starts, the ability to set language values, the application settings, the database settings, the application routes, and lastly the secret key base.

* **db** – within the db directory you will find the database schema file that lists the database table, their columns and the column’s associated data types. The db directory also contains the seeds.rb file, which lets you create some data that can be utilized in the application. This is a great way to quickly integrate data in the application without having to manually add records through a web form element. The schema file can be found at `db/schema.rb`

* **lib** – while many developers could build full applications without ever entering the lib directory, you will discover that it can be incredibly helpful. The lib/tasks directory is where custom rake tasks are created. You have already used a built-in rake task when you ran the database creation and migration tasks; however, creating custom rake tasks can be very helpful and sometimes necessary. An example of a rake task I have created recently was a rake task that I had the server run in the background that called an outside API and synced the API data into the application’s database.

* **log** – within the log directory you will discover the application logs. This can be helpful for debugging purposes, but for a production application I will typically use an outside service since they can offer more advanced services such as querying and alerts.

* **public** – this directory contains some of the custom error pages, such as 404 errors, along with the robots.txt file which will let developers control how search engines index the application on the web.

* **test** – by default Rails will install the test suite in this directory. This is where all of your specs, factories, test helpers, and test configuration files can be found. *Side note: We always use RSpec, which means this directory will actually be called `spec`.*

* **tmp** – this is where the temporary items are stored and is rarely accessed by developers.

* **vendor** – this directory has been utilized for varying purposes in the past, in Rails 4+ its main purpose is for integrating client side MVC frameworks, such as AngularJS.

* **Gemfile** – the Gemfile contains all of the gems that are included in the application; this is where you will place outside libraries that are utilized in the application. After any change to the Gemfile you will need to run: bundle. This will call in all of the code dependencies into the application. The Gem process can seem like a mystery to new developers, but it is important to realize that the Gems that are brought into an application are simply Ruby files that help extend the functionality of the app.

* **Gemfile.lock** – this file should not be edited; it displays all of the dependencies that each of the Gems contain along with their associated versions. There have been times where I discovered application bugs due to varying Gem’s dependencies.

* **README.rdoc** – the readme file is an important place to document the details of the application. If the application is an open-source project, this is where you can place instructions to other developers, such as how to get the app up and running locally.

## Creating the database

Before we can startup the rails server, first you can create the database by running:

```rake db:create```

## Starting Up the Rails Server

To startup the Rails server, make sure that you are in the root of the application in the terminal and run:

```rails s```

This will startup the rails server and you will see output such as the following:

```
=> Booting WEBrick
=> Rails 4.2.3 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
[2015-11-14 22:16:54] INFO  WEBrick 1.3.1
[2015-11-14 22:16:54] INFO  ruby 2.1.2 (2014-05-08) [x86_64-darwin13.0]
[2015-11-14 22:16:54] INFO  WEBrick::HTTPServer#start: pid=3080 port=3000
```

Now that the server is running properly, you can go and verify that it's working properly in the browser by going to: ```http://localhost:3000/```

Here you will see the 'Welcome aboard' page that ships with Rails and it shows that we're ready to start building the application!

## Using the Rails Console

The Rails console is an important tool in the arsenal for any Rails developer, it gives you a direct connection to your application's ecosystem and lets you perform tasks such as:

* Run database queries
* Run application code
* Perform full CRUD tasks with the database
* Allows you to switch between making permanent database changes and running in a sandbox mode to test scripts out.

To startup the rails console, run the following command in the terminal:

```rails c```

This will open up a new Rails console session. We don't have any database tables or records yet, so we can't perform queries (but don't worry, we'll get to that soon enough!), but we can test it out to make sure that we can access methods from within the application.

Rails ships with a great set of view helpers, one of my favorites is the ```pluralize``` method that takes in a word and returns the plural value. So we can test that out in the console to make sure it's working. Run the following command in the Rails console:

```helper.pluralize(5, 'laptop')```

This should return "5 laptops", if you switch the 5 to 1, it will return "1 laptop", pretty cool, right? This means that the Rails console is working, to close the session run the command ```control + d``` and it will return you to the regular terminal session.

Why are we using the `rails console` instead of just starting an `irb` session? That's a great question, try running the same `pluralize` method in an `irb` session and you'll see the following error `NameError: undefined local variable or method `helper` for main:Object`. The reason for the error is because there is a very significant difference between the `rails console` and `irb`, even though they both run Ruby code, `rails console` loads the full Rails environment, which gives you access to Rails' specific methods (along with the full application database). Don't worry if the console is still fuzzy, we'll be using it constantly in future lessons and it will soon become second nature to use.

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/rails-application-basics-readme' title='Rails Application Basics'>Rails Application Basics</a> on Learn.co and start learning to code for free.</p>
