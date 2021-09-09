# README

This Ruby on Rails application allows you to interact easily with mpp heroku postgres db.

After cloning locally, steps:

1. Open `config/database.yml` file and fill in host, port, username and password with the creds given by heroku (go to heroku app then in add-ons, go to "Heroku Postgres", then go to Settings tag)

2. Setup app:

> bundle install

This assumes you have ruby version 2.6.3. If you don't have this ruby version, use [rvm](https://rvm.io) to change your ruby version, or simply change the ruby version in `Gemfile` file

3. We don't need to setup databases for this Application since we connect to an already live database. This will open a console that connects directly to heroku postgres:

> rails console

Now you can access data quickly. A few ideas:

Last cross selling :
> CrossSelling.last
This will start a select limit 1 query and you can view directly the structure of CrossSelling table.

Get Number of access logs more than a month old
> AccessLog.where('timestamp < ?', 1.month.ago).count

Delete old access logs 
> AccessLog.where('timestamp < ?', Date.today.at_beginning_of_month).delete_all 

Get similar items for product "8674323"
> SimilarItem.where(dsm_code_ref: "8674323")