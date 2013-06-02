# animal_center

For the National Day of Civic Hacking 2013

## What is it?

It's an open source webapp to help the [Iowa City Animal Center](http://www.icanimalcenter.org/) increase their adoption rate.  (Cats in particular don't get adopted as often as dogs, for example.)

It will be a simple app that allows images of animals up for adoption to be easy to caption, kind of like on [the Cheezburger sites](http://icanhas.cheezburger.com/lolcats).  The idea is that people can make funny captions for adoptable cats and dogs, share them on Twitter/Facebook, and hopefully get a lot more people considering adopting these animals.

[Visit the app!](http://animal-center.herokuapp.com/)

From a technical standpoint, it's a [Ruby](http://ruby-lang.org/)/[Rails](http://rubyonrails.org/) app using [Bootstrap](http://twitter.github.io/bootstrap/) and some JavaScript, among other technologies.  It's hosted on [Heroku](http://heroku.com/) because they're great at making web apps easy to deploy.  They were also kind enough to donate money for hosting (in addition to their free level of hosting), and other sponsorship of the [National Day of Civic Hacking in Iowa City](http://www.meetup.com/Iowa-Open-Source-Hardware-meetup/events/120069522/).

## Getting Started

We're happy to hear you'd like to help out!  There are [issues organized by milestone](https://github.com/OpenHackIC/animal_center/issues/milestones) and labelled with difficulty (most are "easy") and technologies you need to know (such as "html", "js", or "ruby").

A quick crash course for designers and web developers unfamiliar with Rails:

* Templates are stored in `app/views` and are essentially HTML, plus some ERB tags (`<% code %>`, `<%= value %>`).
* Assets, such as images, CSS, and JavaScript are stored in `app/assets`.  This allows something called the _asset pipeline_ to compile from LESS to CSS, and from CoffeeScript to JavaScript.

### Development Environment

This is an app that can run on Heroku, so if you already have Git, Ruby, and PostgreSQL on Linux or OSX, you're probably in fine shape.

If you want to use a reproducible, Heroku-like development environment, you can use Vagrant to get set up.  It will set up a virtual machine that is known to work with this application.  (Run into problems?  Vagrant makes it easy to destroy and recreate your development environment, if necessary.)

* Install [Git](http://git-scm.com/) or a [GitHub client](https://github.com/)
* Clone this repository
* Install [VirtualBox](https://www.virtualbox.org/)
* Install the newest version of [Vagrant](http://www.vagrantup.com/)

The following commands may each take a little while to complete.

Within your clone:

    vagrant up
    vagrant ssh

Now you are SSHed into your guest Vagrant virtual machine.  Now you can run these commands:

    cd /vagrant
    bundle
    # Unfortunately, the Vagrant box doesn't come with a PosgreSQL user by default.
    sudo su postgres -c 'createuser --createdb --no-superuser --no-createrole vagrant'
    bundle exec rake db:create
    bundle exec rake db:schema:load

Not using Vagrant?  The steps above are stil basically what you need to do, but without the Vagrant specific parts:

    bundle
    # configure config/database.yml by hand
    bundle exec rake db:create
    bundle exec rake db:schema:load

Now you can run the app:

    bundle exec rails server

And open it in your browser:  http://localhost:3000/

You can now make changes to the code to your heart's content.  **Happy hacking!**

## Contributing

Ruby code should generally follow the [community Ruby Style guide](https://github.com/bbatsov/ruby-style-guide).  If you're writing tests, `rspec` is recommended.

JavaScript or CoffeeScript, your pick.

[Git Flow](https://github.com/nvie/gitflow) is recommended, but not required.  The development branch is `master` and the release branch is `stable`.

### Patches/Pull Requests

* Fork the project.
* Make your feature addition or bug fix.  Please follow the style recommendations (see above).
* Add specs for your changes, if you are able. This is important so we don't break it in a future version unintentionally.
* Commit.
* Open a pull request. Bonus points for topic branches (see `git flow`).

Thanks for your contributions!

## License

GPLv2. See LICENSE for a copy.
