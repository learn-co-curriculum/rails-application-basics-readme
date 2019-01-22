# Rails Application Basics

## Objectives

1. Install the Rails gem
2. Generate a new application with `rails new`
3. Properly name a newly generated Rails application by using and naming both the app constant and directory
4. List the information that goes into the folders and files within a Rails file skeleton
5. Start a local server using the Rails CLI
6. Load the local site from port 3000 in a browser
7. Start a Rails console with the Rails CLI

# Ruby on Rails Introduction

Welcome to the world of Ruby on Rails development! With over a decade of open
source contributions, Rails has evolved into one of the most powerful web
application frameworks available. Before we can start building applications, it
is important to first understand what the Ruby on Rails framework is... and what
it's not.

## Why Use a Framework?

If you wanted to put surround sound in your house, would you go and spend years
researching how to best fabricate speakers, learn how to transfer sound through
wires, weld your own sound board, and create from scratch every other component
that would be required to have a surround sound system in your home? Most likely
not. Instead it would be much smarter and more efficient to purchase a surround
sound system from an organization that already put in all of the research and
development work to create a professional system.

In the same way, when it comes to building a web application it would
technically be possible to build out all of the functionalities yourself, but
it's typically a better idea to leverage a system that has already spent over a
decade developing the tools necessary for getting applications built.

## What is Ruby on Rails?

- **A web framework** - A web framework provides developers the tools they need
  in order to build applications. While every application is unique there are
  certain components that can be found in almost every application, such as:
  routing, asset management, database connections, and the list goes on. A good
  web framework gives developers these baseline tools so that they don't have to
  create the base application functionality for each new project.
- **A Ruby Gem** - At its core, Ruby on Rails is simply a set of Ruby code
  libraries, and since the entire codebase is open source you have the ability to
  review the framework to better understand how it works.
- **A MVC framework** - MVC stands for Model-View-Controller, this essentially
  means that Rails takes advantage of the popular application architecture that
  helps developers naturally separate concerns and organize their applications
  properly. This setup encourages a specific set of conventions, such as placing
  the logic for the application in the model files, managing the code flow in the
  controllers, and displaying content to the user in the views.

_On a side, but very important, note: don't worry if some or all of what we just
reviewed seems foreign. We'll be covering everything in detail in future
lessons, so don't worry if it all feels a little overwhelming._

## What Ruby on Rails is not

- **A programming language** - This is one of the most common misconceptions.
  Ruby on Rails is not a programming language; instead, it is a set of code
  libraries built in Ruby.
- **A slow framework** - Due to the fact that Rails is one of the most
  straightforward frameworks to learn, it can lead to a number of poor coding
  practices from beginners. However, if built properly, Rails projects can be as
  fast as any other framework. Furthermore, Rails's service-based architecture
  makes it a perfect candidate for microservice applications, which can be some of
  the fastest and best performing applications on the web.

# Creating Your First Rails Project

_Before you continue, this assumes that you have Ruby, RubyGems, and Bundler installed on your system._

## Installing the Rails Gem for Local Users

If you are using the IDE you should not do this step. You already have rails
installed. Just skip down to generating a new rails application!

As mentioned above, Rails is simply a Ruby Gem. To install it on your system,
run the following command in the terminal of your computer:

```bash
gem install rails
```

Depending on your system configuration, you may need to prepend the command with `sudo` to install the gem as the root user. Once the gem is installed you can create Rails applications!

## Generating a New Rails Application

Our application is going to be called BlogFlash. To create the application, run the following command:

```bash
rails new blog-flash
```

There are a number of common naming conventions for Rails app names. Typically
you will want to use all lower case letters, separated by '-', as shown in our
`blog-flash` naming structure. In the same way that there are rules for naming
methods, variables, classes, etc. in Ruby, there are naming rules for
application names. Since the application name is used as the app constant and
throughout the application, the best approach is to keep your naming simple and
to follow a standard naming practice.

## Rails File Structure Overview

Since you will be working with this file structure on a daily basis, it is very
important to understand and become familiar with the file system. Below is a
breakdown for each directory:

- **app** – contains the models, views, and controllers, along with the the rest
  of the core functionality of the application. This is the one directory where
  you can make a change and not have to restart the Rails server. The majority of
  your time will be spent working in this directory. In addition to the full MVC
  structure, this directory also contains non Ruby files, such as: css files,
  javascripts, images, fonts, etc.

- **bin** – some built-in Rails tasks that you most likely will never have to
  work with.

- **config** – the config directory manages a number of settings that control
  the default behavior, including: the environment settings, a set of modules that
  are initialized when the application starts, the ability to set language values,
  the application settings, the database settings, the application routes, and
  lastly the secret key base.

- **db** – within the db directory you will find the database schema file that
  lists the database tables, their columns, and each column’s associated data
  type. The db directory also contains the seeds.rb file, which lets you create
  some data that can be utilized in the application. This is a great way to
  quickly integrate data in the application without having to manually add records
  through a web form element. The schema file can be found at `db/schema.rb`.

- **lib** – while many developers could build full applications without ever
  entering the lib directory, you will discover that it can be incredibly helpful.
  The lib/tasks directory is where custom rake tasks are created. You have already
  used a built-in rake task when you ran the database creation and migration
  tasks; however, creating custom rake tasks can be very helpful and sometimes
  necessary. For example, a custom rake task that runs in the background, making
  calls to an external API and syncing the returned data into the application’s
  database.

- **log** – within the log directory you will discover the application logs.
  This can be helpful for debugging purposes, but for a production application
  it's often better to use an outside service since they can offer more advanced
  services like querying and alerts.

- **public** – this directory contains some of the custom error pages, such as
  404 errors, along with the robots.txt file which will let developers control how
  search engines index the application on the web.

- **test** – by default Rails will install the test suite in this directory.
  This is where all of your specs, factories, test helpers, and test configuration
  files can be found. _Side note: We always use RSpec, which means this directory
  will actually be called `spec`._

- **tmp** – this is where the temporary items are stored and is rarely accessed
  by developers.

- **vendor** – this directory has been utilized for varying purposes in the
  past. In Rails 4+, its main purpose is for integrating Client-side MVC
  frameworks, such as AngularJS.

- **Gemfile** – the Gemfile contains all of the gems that are included in the
  application; this is where you will place outside libraries that are utilized in
  the application. After any change to the Gemfile, you will need to run `bundle`.
  This will call in all of the code dependencies in the application. The Gem
  process can seem like a mystery to new developers, but it is important to
  realize that the Gems that are brought into an application are simply Ruby files
  that help extend the functionality of the app.

- **Gemfile.lock** – this file should not be edited. It displays all of the
  dependencies that each of the Gems contain along with their associated versions.
  Messing around with the lock file can lead to application bugs due to missing or
  altered Gem dependencies.

- **README.rdoc** – the readme file is an important place to document the
  details of the application. If the application is an open-source project, this
  is where you can place instructions to other developers, such as how to get the
  app up and running locally.

## Creating the database

Before we can startup the rails server, first you can create the database by
running:

```bash
rake db:create
```

## Starting Up the Rails Server

To startup the Rails server, make sure that you are in the root of the
application in the terminal and run:

```bash
rails s
```

This will startup the rails server and you will see output such as the following:

```bash
=> Booting WEBrick
=> Rails 4.2.3 application starting in development on http://localhost:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
[2015-11-14 22:16:54] INFO  WEBrick 1.3.1
[2015-11-14 22:16:54] INFO  ruby 2.1.2 (2014-05-08) [x86_64-darwin13.0]
[2015-11-14 22:16:54] INFO  WEBrick::HTTPServer#start: pid=3080 port=3000
```

Now that the server is running properly, you can verify that it's working
properly in the browser by navigating to `http://localhost:3000/`.

Here you will see the 'Yay! You're on Rails!' page that ships with Rails. It
shows that we're ready to start building the application!

In order to **shutdown** your server, you will need to hit the button
combination `CTRL+C`.

## Using the Rails Console

The Rails console is an important tool in the arsenal of any Rails developer. It
gives you a direct connection to your application's ecosystem and lets you
perform tasks such as:

- Running database queries
- Running application code
- Performing full CRUD tasks with the database
- Allowing you to switch between making permanent database changes and running in
  a sandbox mode to test scripts out

To start up the Rails console, run the following command in the terminal:

```bash
rails c
```

This will open up a new Rails console session. We don't have any database tables
or records yet, so we can't perform queries. (Don't worry, we'll get to that
soon enough!). However, we can test it out to make sure that we can access
methods from within the application.

Rails ships with a great set of view helpers. One particularly awesome one is
the `pluralize` method that takes in a word and returns the plural equivalent.
Let's test that out in the console to make sure it's working. Run the following
command in the Rails console:

```bash
helper.pluralize(5, 'laptop')
```

This should return `"5 laptops"`. If you switch the 5 to a 1, it will return `"1 laptop"`. Pretty cool, right? This means that the Rails console is working. To
close the session, run the command `control + d` and it will return you to the
regular terminal session.

Why are we using the `rails console` instead of just starting an IRB session?
That's a great question. Try running the same `pluralize` method in an IRB
session and you'll see the following error: `` NameError: undefined local variable or method `helper` for main:Object ``. The reason for the error is that
there is a very significant difference between the Rails console and IRB. Even
though they both run Ruby code, the Rails console loads the full Rails
environment, which provides access to Rails's specific methods (along with the
full application database). Don't worry if the idea of using the console is
still fuzzy –– we'll be using it constantly in future lessons, and it will soon
become second nature.

<p class='util--hide'>View <a href='https://learn.co/lessons/rails-application-basics-readme'>Rails Application Basics</a> on Learn.co and start learning to code for free.</p>
