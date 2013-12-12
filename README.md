Fulcrum Webhook Sample - Rails 4
================================

A Rails 4 application to serve as Webhook endpoint for use in Fulcrum. It simply
receives the event requests and stick them into the database.

This can be used as a foundation for other application.

Get it Running
--------------

### Production

Deploy to Heroku using the following steps:

#### Create

- Clone this repo
- `cd fulcrum-webhook-sample-rails4`
- [Install the Heroku Toolbelt](https://toolbelt.heroku.com/)
- `heroku login`
- `heroku create`
- `ruby -e "require 'securerandom'; puts SecureRandom.hex(128);"`
  - Use this string in the next command.
- `heroku config:set SECRET_TOKEN=<string from previous command output>`

#### Deploy

- `git push heroku master`
- `heroku run rake db:migrate`
- `heroku domains`
  - Remember this URL for later.

For more help check out [how to get started with Rails
4](https://devcenter.heroku.com/articles/getting-started-with-rails4) on
Heroku.

#### Use

Go into Fulcrum and add your Heroku application's URL as a webhook.

#### See it in Action

This assumes everything is hooked up properly between Fulcrum and this app.

##### From the Site

- Create a form in Fulcrum.
- Visit the heroku app in a browser.
- You should see the form create event request in the list of requests.

##### From the Console

- Create a form in Fulcrum.
- heroku run rails console
- `WebhookEventRequest.last` should show you the form create event request
  received.

### Development

#### Install

```
bundle install
bundle exec rake db:create
bundle exec rake db:schema:load
```

#### Run

```
bundle exec foreman start
```

#### Use

In your local Fulcrum server, create a webhook with `localhost:3000` as the
URL.

#### See it in Action

This assumes everything is hooked up properly between Fulcrum and this app.

#### From the Site

- Create a form in Fulcrum.
- Visit app (`localhost:3000`) in a browser.
- You should see the form create event request in the list of requests.

##### From the Console

- Create a form in Fulcrum.
- `bundle exec rails console`
- `WebhookEventRequest.last` should show you the form create event request
  received.

