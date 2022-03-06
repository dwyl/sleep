# _Tutorial_

This tutorial takes you through _building_ a sleep tracking App from scratch
so that you can understand how it works.
If you get stuck, _please_
[**ask questions**!](https://github.com/dwyl/sleep/issues)


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
in **_less_ than 20 minutes**. <!-- <sup>1</sup> -->
Anyone who knows basic programming 
(e.g. `Python`, `JavaScript`, etc.)
should be able to follow along.


<!--
<sup>1</sup> 
Other approaches to web app development 
might get you different results ... 
https://twitter.com/iamdevloper/status/787969734918668289
-->

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


<!-- uncomment when ready for review
[![HitCount](http://hits.dwyl.com/dwyl/sleep_tutorial.svg?style=flat-square)](http://hits.dwyl.com/dwyl/sleep)
-->

So far so good. 


#### Quick Note on App Naming Conventions

You will often see Phoenix apps with the name of the app in the project files
e.g: in the **`Chat`** example 
[github.com/dwyl/phoenix-chat-example](https://github.com/dwyl/phoenix-chat-example)

[lib/chat/repo.ex#L1](https://github.com/dwyl/phoenix-chat-example/blob/main/lib/chat/repo.ex#L1)

```elixir
defmodule Chat.Repo do
  use Ecto.Repo,
    otp_app: :chat,
    adapter: Ecto.Adapters.Postgres
end
```

[lib/chat_web/router.ex#L1](https://github.com/dwyl/phoenix-chat-example/blob/main/lib/chat_web/router.ex#L1)
```elixir
defmodule ChatWeb.Router do
  use ChatWeb, :router

... etc.
```

Having `Chat` or `ChatWeb` namespace can be useful 
if you're working on multiple Phoenix apps simultaneously 
and need to context switch. 
That's why we use the `Auth` namespace 
in our Authentication App:
[github.com/dwyl/auth](https://github.com/dwyl/auth)

e.g:
[lib/auth_web/controllers/auth_controller.ex#L1](https://github.com/dwyl/auth/blob/main/lib/auth_web/controllers/auth_controller.ex#L1)

```elixir
defmodule AuthWeb.AuthController do
...
```

The reasons why _this_ app is namespaced **`App`** are: <br />
**a)** It's less to type and still provides clarity/context.<br />
**b)** <br />
**c)** If we _succeed_ in building a sleep-tracking app, 
we will re-use some of the code in our "main" App. 
[github.com/dwyl/app](https://github.com/dwyl/app)
This means it's easy to 
"lift and shift" the code & tests
without needing to waste time with "find & replace".
<br />

If you prefer to namespace your app differently, go for it!s

## Show Me the Code! 👩‍💻

Open the project in your editor/IDE of choice.

### Create `/live` Directory

Since we are using Phoenix LiveView for this App,
we need to create a new `live` directory 
with the following path:
`lib/app_web/live`

### Create `app_live.ex` File

Inside that newly created `/live` directory,
create a new file called 
`app_live.ex` 
with the path:
`lib/app_web/live/app_live.ex`

```elixir
defmodule App.AppLive do
  use AppWeb, :live_view

  def mount(_params, _session, socket) do
    {:ok, socket}
  end

  def render(assigns) do
    AppWeb.AppView.render("messages.html", assigns)
  end
end
```


### Update `router.ex`

and navigate to the 
`lib/app_web/router.ex` file.

