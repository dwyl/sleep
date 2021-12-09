# sleep

Sleep is the single most important activity we perform in life. <br />
A keystone activity 


# Why?

# What?

# Who? 

# When?




# How?

Firstly, you can try the App via Heroku:
https://sleepdev.herokuapp.com

Try: 
+ **Log _in_**
+ **Start** a sleep timer
+ **Stop** the timer
+ **Log _out_**.
+ **Log _back in_**
+ ***Confirm*** your "sleep" session was recorded.


# _Tutorial_


## Implementation Note

We built this MVP App using using 
[**`Elixir`**](https://github.com/dwyl/learn-elixir) 
and 
[**`Phoenix`**](https://github.com/dwyl/learn-phoenix-framework) 
because it's one of the simplest ways 
to build web applications
from first principals.
Our objective is to get to a _useable_ app
as **_fast_ as possible** 
so we can start inputting/saving data.
You will see below, 
that we can get up-and-running
with a **basic interface**,
**saving data** to the database,
**authentication**
and ***deployment***
in **_less_ than 20 minutes**.<sup>1</sup>
Anyone who knows basic programming 
(e.g. `Python`, `JavaScript`, etc.)
should be able to follow along.


## Create New Phoenix App

```sh
mix phx.new app --no-mailer --no-dashboard
```

This creates a new Phoenix Web App named **`app`**
without the mailer (email) or live dashboard
but with a database and `LiveView` support.


When you see the prompt asking you 
to fetch and install the dependencies:

```
Fetch and install dependencies? [Yn]
```

Type `y` followed by the `Enter` key:

You should then see:

```
* running mix deps.get
* running mix deps.compile
```

To start the Phoenix server:

* Install dependencies with `mix deps.get`
* Create and migrate your database with `mix ecto.setup`
* Start Phoenix endpoint with `mix phx.server`

You should see the following output in your terminal:

```
[info] Running AppWeb.Endpoint with cowboy 2.9.0 at 127.0.0.1:4000 (http)
[debug] Downloading esbuild from https://registry.npmjs.org/esbuild-darwin-64/-/esbuild-darwin-64-0.13.5.tgz
[info] Access AppWeb.Endpoint at http://localhost:4000
[watch] build finished, watching for changes...
```

When you open http://localhost:4000 in your web browser,
you should see see something similar to the following:

![phoenix-framerwork-welcome-page](https://user-images.githubusercontent.com/194400/145309471-306fdd5e-324f-4c4a-bd9f-6fddbec7f512.png)





<sup>1</sup> 
Other approaches to web app development 
might get you different results ... 
https://twitter.com/iamdevloper/status/787969734918668289