---
layout: post
title: "Installing Ruby on Mac OS X"
date:   2013-08-24
categories: it ruby
---
By default Ruby is installed on a Mac OS X but its interpreter version is 1.8.x. This version is a bit old and if you want to develop with the last version of Rails (v4) you have to upgrade to a newer version.

Here are steps I followed to set up my development environment. The original post can be found [here](http://createdbypete.com/articles/ruby-on-rails-development-with-mac-os-x-mountain-lion/).

### Homebrew Installation
Homebrew is a command line package manager for Mac OS X. We are going install it first because we will use it to set up our ruby environment.

{% highlight ruby %}
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"

# Add Homebrews binary path to the front of the $PATH
echo "export PATH=/usr/local/bin:$PATH" >> ~/.bash_profile
source ~/.bash_profile
{% endhighlight %}

After that run the following command to be sure that all is ok:
{% highlight bash %}
brew doctor
{% endhighlight %}

### Ruby installation
Now we have the package manager installed we are going to install rbenv and ruby-build. Rbenv allow you to install multiple ruby versions on you machine and choose the one you want to use per project.

{% highlight bash %}
brew install rbenv ruby-build
echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
source ~/.bash_profile
{% endhighlight %}

Now rbenv is installed let's install the latest ruby version:
{% highlight bash %}
rbenv install --list 	#list all ruby version available.
rbenv install 2.0.0-p0  #install the specified version
rbenv rehash 			#has to be always ran after each installation/upgrade
rbenv global 2.0.0-p0   #we set this version the one used globally
{% endhighlight %}

### Rails installation
{% highlight bash %}
ruby --version 			#to be sure to use the correct ruby version
gem install rails
rails new myproject
cd myproject
rbenv local 2.0.0-p0  	#to set the ruby version used in this project
{% endhighlight %}

### Resources
- [Original post](http://createdbypete.com/articles/ruby-on-rails-development-with-mac-os-x-mountain-lion/)
- [Hombrew website](http://brew.sh/)
- [rbenv github repository](https://github.com/sstephenson/rbenv)
