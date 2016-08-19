# Ruby on Rails Tutorial: sample application

This is the sample application for [*Ruby on Rails Tutorial: Learn Rails by Example*](http://railstutorial.org/) by [Michael Hartl](http://michaelhartl.com/).

This sample has been modified to run on Cloud Foundry. The `cf-autoconfig` gem was added to enable auto-configuration of database connections as described in the [Cloud Foundry documentation](http://docs.cloudfoundry.com/docs/using/services/ruby-service-bindings.html). The `mysql2` and `activerecord-mysql2-adapter` gems were also added to support connection to MySQL database. 

## Running the application on Cloud Foundry

After installing in the 'cf' [command-line interface for Cloud Foundry](http://docs.cloudfoundry.org/devguide/installcf/),
targeting a Cloud Foundry instance, and logging in, the application can be pushed using these commands:

Choose a MySQL service from the list and create a service instance named `rails-db` using a MySQL service and plan: 

~~~
$ cf create-service p-mysql 100mb-dev rails-db
Creating service rails-db
OK
~~~

Now push the application: 

~~~
$ cf push 
Using manifest file manifest.yml

Updating app rails-sample
OK

Creating route rails-sample-desiccative-acetylizer.cfapps.io...
OK

Binding rails-sample-desiccative-acetylizer.cfapps.io to rails-sample...
OK

Uploading rails-sample...
Uploading app files from: rails_sample_app
Uploading 41.1M, 6349 files
OK
Binding service rails-db to app rails-sample
OK

Starting app rails-sample
OK
...

0 of 1 instances running, 1 starting
0 of 1 instances running, 1 starting
0 of 1 instances running, 1 starting
1 of 1 instances running

App started

Showing health and status for app rails-sample
OK

requested state: started
instances: 1/1
usage: 256M x 1 instances
urls: rails-sample-desiccative-acetylizer.cfapps.io

     state     since                    cpu    memory          disk
#0   running   2014-05-29 03:34:22 PM   0.0%   50.3M of 256M   80.2M of 1G
~~~

The application will be pushed using settings in the provided `manifest.yml` file. 
