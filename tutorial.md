<div align="center">

# _Tutorial_ 👩‍💻

</div>

This **step-by-step tutorial** 
guides you through _building_ 
a sleep tracking App from scratch
so you can _understand_ how it works. 
Expect it take around **`20 minutes`** to complete.
Set your pomodoro timer and turn off other distractions!

<br >

## Implementation Note 💡

This App is built using using 
[**`Elixir`**](https://github.com/dwyl/learn-elixir),
[**`Phoenix`**](https://github.com/dwyl/learn-phoenix-framework) 
and 
[**`LiveView`**](https://github.com/dwyl/phoenix-liveview-counter-tutorial#liveview)
because it's one of the simplest ways 
to build mobile-first responsive web applications
from first principals.
Our objective is to create a _useful_ app
as **_fast_ as possible** 
so we can start inputting/saving data.
You will see below, 
that we can get up-and-running
with a **basic interface**,
**saving data** to the database,
**authentication**
and ***deployment***
in **`20 minutes`**. <!-- <sup>1</sup> --> <br />
Anyone who knows basic programming 
(e.g. `Python`, `JavaScript`, etc.)
should be able to follow along.
If you are completely **new** to Phoenix or LiveView,
we recommend starting with the more basic
[LiveView Counter Tutorial](https://github.com/dwyl/phoenix-liveview-counter-tutorial).
If you get stuck, please don't suffer in silence, 
[**open an issue**!](https://github.com/dwyl/sleep/issues). <br />



<!--
<sup>1</sup> 
Other approaches to web app development 
might get you different results ... 
https://twitter.com/iamdevloper/status/787969734918668289
-->
<br />

## 1. Create a New Phoenix App 🆕

In a new terminal window, run the following command:

```sh
mix phx.new app --live --no-mailer --no-dashboard
```

This creates a new Phoenix Web App named **`app`**
with everything setup for `LiveView` support
but  without the mailer (email) or live dashboard
cause we won't be needing either of those features
and we don't want unused/untested code.

When you see the prompt asking you 
to fetch and install the dependencies:

```sh
Fetch and install dependencies? [Yn]
```

Type `y` followed by the `Enter` key.

You should then see:

```sh
* running mix deps.get
* running mix deps.compile
```

To start the Phoenix server:

+ Change working directory into the App, e.g: `cd app`
+ **Install** dependencies with `mix deps.get`
+ **Setup** the database with `mix ecto.setup`
+ **Start** the Phoenix App with `mix phx.server`

You should see output similar to the following in your terminal:

```sh
[info] Running AppWeb.Endpoint with cowboy 2.9.0 at 127.0.0.1:4000 (http)
[debug] Downloading esbuild from https://registry.npmjs.org/esbuild-darwin-64/-/esbuild-darwin-64-0.13.5.tgz
[info] Access AppWeb.Endpoint at http://localhost:4000
[watch] build finished, watching for changes...
```

When you open http://localhost:4000 in your web browser,
you should see see something similar to the following:

![phoenix-framerwork-welcome-page](https://user-images.githubusercontent.com/194400/159679120-8ffd98a2-d0c9-421e-9c15-d9b6e4004cb8.png)

So far so good. 

<br />

### Quick Note on App Naming Conventions 📛

You will often see Phoenix applications 
with the name of the app in the project files
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
if you're working on _multiple_ Phoenix apps _simultaneously_
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
**b)** The word "sleep" has a special significance in Erlang/Elixir
see: [`sleep/1`](https://www.erlang.org/doc/man/timer.html#sleep-1)
so we don't want our IDE constantly suggesting that we 
suspend the process ... <br />
**c)** If we _succeed_ in building a sleep-tracking app, 
we will re-use some of the code in our "main" App. 
[github.com/dwyl/app](https://github.com/dwyl/app)
This means it's easy to 
"lift and shift" the code & tests
without needing to waste time with messy "find & replace".
<br />

If you prefer to namespace your app differently, go for it!

<br />

## Show Me the Code! 👩‍💻

Open the project in your editor/IDE of choice.

<br >

## 2. Create `/live` Directory

Since we are using Phoenix LiveView for this App,
we need to create a new `live` directory 
with the following path:
`lib/app_web/live`

e.g: `mkdir lib/app_web/live`

## 3. Create `app_live.ex` File

Inside that newly created `/live` directory,
create a new file called 
`app_live.ex` 
so the file path is:
`lib/app_web/live/app_live.ex`

_Type_ the following code in the file:

```elixir
defmodule App.AppLive do
  use AppWeb, :live_view

  def mount(_params, _session, socket) do
    {:ok, socket}
  end

  def render(assigns) do
    AppWeb.AppView.render("index.html", assigns)
  end
end
```

If you attempt to compile the project now you will see a warning:


```elixir
warning: AppWeb.AppView.render/2 is undefined 
(module AppWeb.AppView is not available or is yet to be defined)
  lib/app_web/live/app_live.ex:9: App.AppLive.render/1
```

## 4. Create `app_view.ex` File

Create a new file with the path:
`lib/app_web/views/app_view.ex`

Insert the following code into the file:

```elixir
defmodule AppWeb.AppView do
  use AppWeb, :view
end
```

This just tells our new view to `use` all the code 
in the `AppWeb` `:view` module (part of Phoenix).

> If you're _curious_ how `Views` work in `Phoenix`, 
see:
[`guides/views.md`](https://github.com/phoenixframework/phoenix/blob/master/guides/views.md`)


## 5. Edit the `index.html.heex` and `root.html.heex` Templates

First **rename** the **`/page`** folder 
as we won't be using "pages" in this project.

From:
`lib/app_web/templates/page/`
To: 
`lib/app_web/templates/app/`

e.g:
```sh
mv lib/app_web/templates/page lib/app_web/templates/app
```

Then edit the template at `lib/app_web/templates/app/index.html.heex` replacing the contents with the following line:

```html
<h2>App Goes Here!</h2>
```

Finally to make the layout simpler,
Update the `<body>` section of the 
`lib/app_web/templates/layout/root.html.heex` 
file to the following:

```html
<body>
  <header>
    <section class="container">
      <h1>Sleep Tracker!</h1>
    </section>
  </header>
  <%= @inner_content %>
</body>
```

Don't worry, we will improve on both of these files later.


## 6. Update `router.ex`

Open the `lib/app_web/router.ex` file and 
replace the line:

```elixir
    get "/", PageController, :index
```

With:

```elixir
    live "/", AppLive
```

## Checkpoint: Working LiveView App 📍

At this stage,
if you run the project:

```sh
mix phx.server
```

Open the URL http://localhost:4000 
in your Web Browser;
you should see something similar to this:


<img width="726" alt="image" src="https://user-images.githubusercontent.com/194400/159721352-7a53f510-9cce-402a-a7df-5f17e00a129a.png">



## 7. Update Tests

If you attempt to run the tests in the project now:

```sh
mix test
```

One of the tests will fail:


```elixir
Generated app app
..

  1) test GET / (AppWeb.PageControllerTest)
     test/app_web/controllers/page_controller_test.exs:4
     Assertion with =~ failed
     code:  assert html_response(conn, 200) =~ "Welcome to Phoenix!"
     left:  "<!DOCTYPE html>\n<html lang=\"en\">\n  <head>\n    <meta charset=\"utf-8\">\n    <meta http-equiv=\"X-UA-Compatible\" content=\"IE=edge\">\n    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">\n<title data-suffix=\" · Phoenix Framework\">App · Phoenix Framework</title>\n    <link phx-track-static rel=\"stylesheet\" href=\"/assets/app.css\">\n    <script defer phx-track-static type=\"text/javascript\" src=\"/assets/app.js\"></script>\n  </head>\n  <body>\n    <header>\n      <section class=\"container\">\n        <h1>Sleep Tracker!</h1>\n      </section>\n    </header>\n<div data-phx-main=\"true\"> <main class=\"container\">\n  <p class=\"alert alert-info\" role=\"alert\" phx-click=\"lv:clear-flash\" phx-value-key=\"info\"></p>\n\n  <p class=\"alert alert-danger\" role=\"alert\" phx-click=\"lv:clear-flash\" phx-value-key=\"error\"></p>\n<h2>App Goes Here!</h2>\n</main></div>\n  </body>\n</html>"
     right: "Welcome to Phoenix!"
     stacktrace:
       test/app_web/controllers/page_controller_test.exs:6: (test)
```

First given that we won't be using 
`controllers` in this App,
rename the test folder from:
`test/app_web/controllers` to `test/app_web/live`

e.g:
```sh
mv test/app_web/controllers test/app_web/live
```

Now rename the file
`test/app_web/live/page_controller_test.exs`
to
`test/app_web/live/app_live_test.exs`

e.g:
```sh
mv test/app_web/live/page_controller_test.exs test/app_web/live/app_live_test.exs
```

Then open the 
`test/app_web/live/app_live_test.exs`
file and 
replace the entire contents 
with the following test code:

```elixir
defmodule AppWeb.AppLiveTest do
  use AppWeb.ConnCase

  test "GET /", %{conn: conn} do
    conn = get(conn, "/")
    assert html_response(conn, 200) =~ "Sleep Tracker"
  end
end
```

Now when you re-run the tests:

```sh
mix test
```

You will see the tests pass:

```sh
...

Finished in 0.2 seconds (0.1s async, 0.1s sync)
3 tests, 0 failures

Randomized with seed 575721
```



[![HitCount](http://hits.dwyl.com/dwyl/sleep-tutorial.svg?style=flat-square)](http://hits.dwyl.com/dwyl/sleep)