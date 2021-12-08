# sleep

Sleep is the single most important activity we perform in life. <br />
A keystone activity 


# Why?

# What?

# Who? 

# When?




# How?




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




```sh
mix phx.new app --no-mailer --no-dashboard
```

This creates a new Phoenix Web App named **`app`**
without the mailer (email) or live dashboard
but with a database and `LiveView` support.


To start your Phoenix server:

* Install dependencies with `mix deps.get`
* Create and migrate your database with `mix ecto.setup`
* Start Phoenix endpoint with `mix phx.server`




<sup>1</sup> 
Other approaches to web app development 
might get you different results ... 
https://twitter.com/iamdevloper/status/787969734918668289