## Opensuse h4ckweek 2022 - navigation log

[Project page](https://hackweek.opensuse.org/projects/give-back-to-wezterm)

[this page source code](https://github.com/michelepagot/opensuse.hackweek.2022)

![Image](img/computer_color.png)



### Day 1

This day is mostly dedicated to trace a path

#### TO DO

##### Create a webpage to show the progress
* page formatting

##### Test Hello World
Create a bare minimal hello world test to deploy a TW and install Wezterm

#### DONE

##### Create a webpage to show the progress
 * repo created
 * gh-pages branch created
 * theme selected and create a first index.md
 * add hackweek logo
 * looking at (testing-your-github-pages-site-locally-with-jekyll)[https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll] to be able to build the page locally. Some issue as bundle installed jekyll is not found by bundle as running `bundle exec jekyll`. This one helps: [devhints.io](https://devhints.io/jekyll) but then I face (issues/399)[https://github.com/github/pages-gem/issues/399], workaround using `PAGES_REPO_NWO=michelepagot/opensuse.hackweek.2022` but then face (issues/8523)[https://github.com/jekyll/jekyll/issues/8523] solved by running `bundle add webrick`  ... ok, I have my page served locally and enough Ruby for the moment ...



### Backlog and ideas

* Research and contact the opensuse wezterm package mainteiner
* Look at where to start from (openQA)
  - Look at similar test in openQA (firefox in x11 ?? )
  - where to develope (on which openQA instance)?
  - where to let the test run?
  - where to version the test code (test/lib/schedule): in os-autoinst-distri-opensuse or on the wezterm repo directly (I like more the second one but I'm not sure if it is feasable)
* try to start natively to code test in python?
* look at how to trigger:
  - wezterm github action
  - monitoring osd for wezterm package



### Documentation and link collection

openQA doc
 - http://open.qa/docs/

Wezterm doc
 - https://wezfurlong.org/wezterm/

Wezterm repo
 - https://github.com/wez/wezterm

Lua

Jekyll and github pages :
 - https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll

