+++
categories = ["android"]
date = 2020-01-17T20:37:05+05:30
draft = true
slug = "dagger-the-easy-way--part-1"
tags = ["android", "dagger", "tutorial"]
title = "Dagger the easy way - Part 1"
description = "Dagger is universally intimidating to beginners and I want to change it."
+++

This is not your average coding tutorial. I'm going to show you how to write real-world Dagger code and skip all the shit about the implementation details of everything we're using and how Dagger does what it does with the code we give it to work with. If you're interested in that, read up elsewhere after this is done or just [poke me on Twitter](https://twitter.com/MSF_Jarvis) that you really, really wanna know the theoretical aspect of this and I'll grumble and consider it.

With that out of the way, onwards to the actual content. We're going to be building a very simple app that does just one thing, checks if this is the app's first run, and show a Toast with some text depending on whether it was the first run or not. Nothing super fancy here, but with some overkill abstraction I'll hopefully be able to demonstrate a straightforward and understandable use of Dagger.

I've setup a repository at [msfjarvis/dagger-the-easy-way](https://github.com/msfjarvis/dagger-the-easy-way) that shows every logical collection of changes in its own separate commit, and also a PR to go from no DI to Dagger so you can browse changes in bulk as well.

## The mandatory theory

I know what I said, but this is just necessary. Bear with me.

### `Component`

A Component defines an interface that Dagger constructs to know the entry points where dependencies can be injected. It can also hold the component factory that instructs Dagger how to construct said component. A Component *also* holds the list of modules.

### `Module`

A Module is any logical unit that contributes to Dagger's object graph. In simpler terms, any `class` or `object` that has declarations which tell Dagger how to construct a particular dependency, is annotated with `@Module`.

## Getting Started

To get started, clone the `boilerplate` branch of my repository which contains all the useless grunt work already done for you. Use `git clone --branch boilerplate https://github.com/msfjarvis/dagger-the-easy-way` if you're unfamiliar with branch selection during clone.

The repo in this stage is very bare - it has the usual boilerplate and just one class, `MainActivity`. We're going to make this a bit more interesting shortly.

Switch to the `part-1` branch, which has a bit more in terms of commit history and code. This is what we're going to work with.

## Setting up the things
