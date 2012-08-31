---
comments: false
date: 2011-01-11 14:58:47
layout: post
slug: rails-new-app-workflow
title: Rails new app workflow
wordpress_id: 517
categories:
- Ruby on Rails
tags:
- rails
---

These are the steps I take when creating a new Rails app, documented here for when I forget.

 

#### Create app

 

rails new <app_name>

 

cd <app_name>

 

#### git

 

git init

 

git add .

 

git commit –m 'Initial commit'

 

**Remember**: Rails generates a .gitignore file for us.

 

#### rvm and gemsets

 

rvm gemset create <app_name>

 

echo 'rvm use 1.9.2@<app_name>' >> .rvmrc

 

echo '.rvmrc' >> .gitignore

 

Creates a .rvmrc file in current directory that way when you cd into this directory rvm automatically switches to the correct version of ruby and the gemset we just created. 

 

Change in and out of the directory to get rvm to kick in:

 

cd ..

 

cd <app_name>

 

#### Gemfile

 

Edit ./Gemfile and add the following lines.

 

gem 'haml'

 

group :test do

 

gem 'rspec'

 

gem 'rspec-rails'

 

end

 

Then install and run bundler:

 

gem install bundler

 

bundle install

 

#### rspec

 

Generate the rspec files:

 

rails g rspec:install
