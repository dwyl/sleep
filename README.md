<div align="center">

# sleep 💤

![sleep-hero-image](https://user-images.githubusercontent.com/194400/159523182-0db2588a-658d-45ae-8ce3-98c37a47ca72.jpeg)
 

## “_Sleep is the single most effective thing we can do <br /> to reset our brain and body health each day._” <br /> ~ Matthew Walker, Why We Sleep

<br />

[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/dwyl/sleep/Elixir%20CI?label=build&style=flat-square)](https://github.com/dwyl/phoenix-liveview-chat-example/actions/workflows/cy.yml)
[![codecov test coverage](https://img.shields.io/codecov/c/github/dwyl/sleep/main.svg?style=flat-square)](https://codecov.io/github/dwyl/phoenix-liveview-chat-example?branch=main)
[![Hex pm](https://img.shields.io/hexpm/v/phoenix_live_view.svg?style=flat-square)](https://hex.pm/packages/phoenix_live_view)
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat-square)](https://github.com/dwyl/phoenix-liveview-counter-tutorial/issues)
[![HitCount](http://hits.dwyl.com/dwyl/sleep.svg?style=flat-square)](http://hits.dwyl.com/dwyl/sleep)

**Try it**: [**sleepdev.herokuapp.com**](https://sleepdev.herokuapp.com/)
![wake-sleeping-heroku-app](https://liveview-chat-example.herokuapp.com/ping)
</div>

<br />

Sleep is the single most important activity in life;
it restores our tired bodies 
and consolidates neural connections to help form/retain memories.
A good night's sleep 
can dramatically increase effectiveness 
in all areas of your life. 
Tracking your sleep times 
and reflecting on your sleep quality
can help you focus on this vital
aspect of health and longevity.

<br />

# Why? 🤷‍♀️

When you sleep well and feel rested,
you have mental clarity and energy 
to focus on Deep Work tasks.
By contrast if you don't get a good night's sleep
virtually everything about your day
will be worse. 


<br />

# What? 📱 🛌

This App is the simplest possible **sleep tracker**
(_other than using a paper notepad + pen 
or a note taking App on your phone ..._)

A **_deliberately_ basic** version of an App is
commonly referred to as Minimum Viable Product ("MVP")
which means it has the minimum features to be useful,
but leaves a lot enhancements out. 

If you think of a feature/improvement, _please_
[**open an issue**!](https://github.com/dwyl/sleep/issues). <br />
**Contributions/ideas** are **_always_ welcome**
and we're delighted to extend this
in response to feedback!

<br />

# Who? 👤

_Everyone_ that sleeps.

<br />

# When? 🕗

You can start using the MVP _now_ (_tonight_)!

> If you're reading this past **22:00**,
go straight to the "***Try it!***" section
and start recording your sleep _now_.
Bookmark (⭐) the project 
and come back to it tomorrow.

<br />

It's never too late 
to start focusing on your sleep quality.
The benefits of good sleep habits 
will last the rest of your life
and may _extend_ it!

<br />

# How? 👩‍💻

There are 3 steps to this:

1. Try it! (2 mins)
2. Run it! (5 mins)
3. Build it! (20 mins)

Let's get started.

<br />

## 1. _Try_ it! 

Firstly, if you haven't already, 
you can _try_ the App via Heroku:
https://sleepdev.herokuapp.com

# @TODO: insert GIF of _performing_ the actions!

Try the following actions: 

+ **Log _in_**
+ **_Start_** a sleep timer
+ **Stop** the timer - to confirm that it works.
+ **Log _out_** - to confirm that no data is stored in the browser.
+ **Log _back in_** - with the same Google or GitHub account you used to login before.
+ ***Confirm*** your "sleep" session was recorded.

Once you've given the app a quick test,
it's time try _running_ it.

<br />

## 2. _Run_ it! 

Now that you've tried it on Heroku,
if you want to dig deeper,
try running the _finished_ (MVP) on your computer.


## Prerequisites 📝

Make sure you have the following installed:

+ [x] Elixir:
https://elixir-lang.org/install.html
+ [x] Phoenix:
https://hexdocs.pm/phoenix/installation.html
+ [x] Postgres:
https://www.postgresql.org/download

### _Check_ You Have Everything _Before_ Starting

Check you have the _latest version_ of **Elixir**
(_run the following command in your terminal_):

```sh
elixir -v
```

You should see something like:

```sh
Erlang/OTP 24 [erts-12.1.2] [source] [64-bit] [smp:12:12] [ds:12:12:10] [async-threads:1] [jit]

Elixir 1.13 (compiled with Erlang/OTP 22)
```

Check you have the **latest** version of **Phoenix**:

```sh
mix phx.new -v
```

You should see:

```sh
Phoenix v1.6.6
```

_Confirm_ **PostgreSQL** is running (_so the App can store chat messages_)
run the following command:

```sh
lsof -i :5432
```

You should see output _similar_ to the following:

```sh
COMMAND  PID  USER   FD  TYPE DEVICE                  SIZE/OFF NODE NAME
postgres 529  Alex   5u  IPv6 0xbc5d729e529f062b      0t0  TCP localhost:postgresql (LISTEN)
postgres 529  Alex   6u  IPv4 0xbc5d729e55a89a13      0t0  TCP localhost:postgresql (LISTEN)
```

This tells us that PostgreSQL is "_listening_" on TCP Port `5432`
(_the default port_)

With all those "pre-flight checks" performed, let's get _going_!

<br />

## Clone, Install & Run the App!

Open a terminal window and run the following commands:

Clone the project to your computer:

```
git clone git@github.com:dwyl/sleep.git
```

Navigate to the **`sleep`** directory:

```
cd sleep
```


Install the dependencies:

```
mix deps.get
```

_Run_ the app:

```
mix phx.server
```

Open the following URL in your web browser:
http://localhost:4000


You should expect to see the following:

# @TODO: insert screenshot of _finished_ app!

<br />

## 3. _Build_ it! 🚀

Now that you know what the end result 
looks & feels like 
and you have a reference implementation 
that you _know_ works on your computer,
it's time to write some **`code`**

**GOTO**: 
[https://github.com/dwyl/sleep/blob/main/tutorial.md](https://github.com/dwyl/sleep/blob/main/tutorial.md)

<br />


<!-- 

# Research

We have read several books on sleep (_so you don't have to_).

Research findings in byte-size format to follow soon!


### “_Before you sleep, read something that is exquisite, and worth remembering._” ~ <br /> Desiderius Erasmus

## Why Focus on Sleep?

If you aren't sleeping enough
you will not be able to function.

## How Sleep Affects You

> Insert table of good vs. bad sleep.

-->