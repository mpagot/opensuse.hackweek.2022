---
title: Opensuse h4ckweek 2022 AAAA
toc: true
---

# Opensuse h4ckweek 2022 - navigation log

This project is about writing and running a set of tests for a GUI application using openQA.
This project is also about reading and digesting the Wezterm documentation and become a ninja of its lua configuration system.

[Project page](https://hackweek.opensuse.org/projects/give-back-to-wezterm)


## Day 1
This day is mostly dedicated to trace a path

### DONE
In Day1 I manage to create a test skeleton but I miss the target to see Wezterm up and running in a openQA test. The TW base test **boot_to_desktop** keep to fail when running on my personal openQA instance. So too few Wezterm for Day1.
I manage to create this page and setup everything locally on my laptop to locally generate this page but I do not master the Jeklly blog generator yet and I do not like as the page is rendered.

#### Create a webpage to show the progress
 * repo created
 * gh-pages branch created
 * theme selected and create a first index.md
 * add hackweek logo
 * render the page locally:
  1. looking at [testing-your-github-pages-site-locally-with-jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll) to be able to build the page locally.
  2. Some issue as bundle installed jekyll is not found by bundle as running `bundle exec jekyll`.
  3. This one helps: [devhints.io](https://devhints.io/jekyll) but then ...
  4. I face [issues/399](https://github.com/github/pages-gem/issues/399),
  5. workaround using `PAGES_REPO_NWO=michelepagot/opensuse.hackweek.2022` but then ...
  6. I face (issues/8523)[https://github.com/jekyll/jekyll/issues/8523] solved by running `bundle add webrick`

... ok, I have my page served locally and enough Ruby for the moment ...

#### Test Hello World
Create a bare minimal hello world test to deploy a TW and install Wezterm

##### Test code
* maybe tomcat is a good candidate. Use as template these 3 files:
```
  cp schedule/functional/tomcat.yaml schedule/functional/wezterm.yaml
  cp tests/x11/tomcat.pm tests/x11/wezterm.pm
  cp lib/Tomcat/Utils.pm lib/Wezterm/Utils.pm
```

Hackweek test code is published on [wezterm_hackweek](https://github.com/mpagot/os-autoinst-distri-opensuse/tree/wezterm_hackweek)

##### How to run my test?

I have some committed test code and a schedule. How to run them? In particular:
* Where to run? On which openQA instance? Do I need an instance?
* How to configure or trigger? Clone? Start from scratch?

I know about **openqa-clone-custom-git-refspec** but how it works? Which openQA instance to use?

I'd like a job to clone. It should be Tumbleweed based (I'm only aware about wezterm package existing for TW).

Should I keep looking at tomcat test as reference? Where tomcat is running in openQA? On which instance? Generally speaking -giving a test name how to find an execution example?-

###### openQA instance
I already have a openQA personal instance on a private server. Otherwise I should look at [o3](https://openqa.opensuse.org/).
Or maybe I do not need an openQA instance at all [isotovideo](https://kalikiana.gitlab.io/post/2022-03-16-running-standandalone-tests-with-isotovideo/)

###### Should I clone "tomcat"?
* look for string **functional/tomcat** in some of the trigger/bot repo that I'm aware of... no luck.
* look in o3 with its search engine ... no luck.
* ask the oracle: google... [issues/91187](https://progress.opensuse.org/issues/91187) and it has a lot of useful links :-)

###### Should I clone a relevant TW job?
[Group and build](https://openqa.opensuse.org/tests/overview?distri=microos&distri=opensuse&version=Tumbleweed&build=20220625&groupid=1)

First attempt: my first attempt was to clone [GNOME on TW](https://openqa.opensuse.org/tests/2436441)

```
openqa.opensuse.orgopenqa.opensuse.org
openQA: opensuse-Tumbleweed-DVD-x86_64-Build20220625-desktopapps-gnome-x11@64bit test results
openQA is a testing framework mainly for distributions
```

as it seems simple enough: 3 steps, 51 sec ...isn't it? But as result of:

```
% openqa-clone-job --from https://openqa.opensuse.org/tests/2436441 --skip-chained-deps  SCHEDULE=tests/boot/boot_to_desktop
```

![Image](img/first_failure.png)


## Day 2
I hope for myself more Wezterm fun...

### DONE

#### Hackweek webpage
From the github project page configuration I selected the theme **jeklly-theme-minimal**. The theme official documentation is at [minimal](https://github.com/pages-themes/minimal).

### TODO

#### Hackweek webpage
* Split the Jeklly page on multiple page, one for each day
* Fix the formatting to have the logo on the left column
* Create a new separate page where to start developing a hackweek presentation (reveal.js maybe)

#### openQA
* Ask about the failure on my personal openQA instance
* Ask if it is possible to run the test on some existing openQA instance (maybe the o3 public one)
* Keep exploring [isotovideo](https://kalikiana.gitlab.io/post/2022-03-16-running-standandalone-tests-with-isotovideo/)

#### Wezterm
* look at needles
* look at how to generate wezterm.lua

## Backlog and ideas

* Research and contact the opensuse Wezterm package maintainer
* Look at where to start from (openQA)
  - Look at similar test in openQA (firefox in x11 ?? )
  - where to develop (on which openQA instance)?
  - where to let the test run?
  - where to version the test code (test/lib/schedule): in os-autoinst-distri-opensuse or on the wezterm repo directly (I like more the second one but I'm not sure if it is feasible)
* try to start natively to code test in python?
* look at how to trigger:
  - Wezterm github action
  - monitoring osd for Wezterm package

## Documentation and link collection

- [openQA doc](http://open.qa/docs/)
- [Wezterm doc](https://wezfurlong.org/wezterm/)
- [Wezterm repo](https://github.com/wez/wezterm)
- Lua
- [Jekyll and github pages](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)