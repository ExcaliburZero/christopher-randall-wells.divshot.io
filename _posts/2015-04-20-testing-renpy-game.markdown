---
layout: post
title:  "Automatically testing a Ren'Py game using Travis CI"
author: "Christopher Randall Wells"
image: "/images/travis_ci_with_renpy.png"
date:   2015-04-20 21:45:00
categories: github travis-ci renpy
---
Recently I was working on making a visual novel with a few other people using the [Ren'Py](http://www.renpy.org/) visual novel engine. While working on the game, I realized that I might be able to automate some of the testing of it using [Travis CI](https://travis-ci.org). After a bit of Google searching and a good bit of trial and error, I was able to put together a script that would allow for automated testing of the game using the Lint script that Ren'Py provides.

If you are not familiar with Travis CI, it is a continuous integration service that is used to test projects that are hosted online. Essentially, what that means is that it is a website that allows people to test their program by running user-written scripts and attempting to build the program. It creates a log of the checks that it does, and gives you a notification if it comes across any errors or problems.

Travis CI is often used with [Github](https://github.com/), a service that allows you to host the source code of programs using Git repositories. When you host your game on a Github repository and set up Travis CI to work with it, whenever you push any changes you make to to the game to Github, Travis CI will check over the code using the scripts that you set it to use.

Note that if you are unfamiliar with Github and [Git](http://git-scm.com/), you may want to look up some tutorials on how to use them, as they are somewhat complex, but are very useful tools for development.

In this article I will show you how to set up Travis CI to run Ren’Py’s Lint script which will check your game for various types of errors in its coding. I will also show you how to setup Travis CI to have it attempt to build your game using the Ren’Py launcher, which will check to make sure that the game can be built without any errors occurring. Travis CI won’t fully test your game, but it will perform a number of checks on it to look for possible errors.

Note that Github and Travis CI are free for open source programs, so you can use them for free if you make your game’s source code public. But if you don’t want to make your source code public, they do offer paid plans for private repositories and testing.

Also note that the following implementation of this system works with the game's source code being hosted on Github and using Travis CI, but you may be able to find other ways to implement this system.

## Instructions
After you have gotten your game's source code on Github, you are going to want to then enable Travis CI for the repository of the game. This can be done by going to [Travis CI](https://travis-ci.org) and logging in with your Github account, then going to your profile page and selecting the grey box next to the repository for the game so that it becomes green with a check-mark in it.

Next you are going to want to make a ".travis.yml" file for the repository. The one I used for a game I was working on (Ganbatte) is below:

{% highlight yaml %}
language: python
python:
  - "2.7"
# command to install dependencies
install:
  - cd ..
  - wget http://www.renpy.org/dl/6.99.1/renpy-6.99.1-sdk.tar.bz2
  - tar xf renpy-6.99.1-sdk.tar.bz2
  - rm renpy-6.99.1-sdk.tar.bz2
  - mv renpy-6.99.1-sdk renpy
  - cd renpy
# command to run tests
script: ./renpy.sh "../ganbatte/" lint && ./renpy.sh launcher distribute "../ganbatte/"
{% endhighlight %}

The script that I used should be able to be easily adapted for your game. But you should replace all instances of "ganbatte" with the name of your repository. For instance if your repository was "user123/fun_visual_novel", then you would change all instances of "ganbatte" to "fun_visual_novel".

I will now go over what the different parts of the script do.

### Language declaration
{% highlight yaml %}
language: python
python:
    - "2.7"
{% endhighlight %}

This section of the script lets Travis CI know to use Python 2.7 when testing code for the game. This section is not necessarily needed, but may come in handy if you want to run anything related to Ren'Py using Python.

Note that if you do not include a language declaration like this one, Travis CI will default to Ruby as the language it loads by default.

### Install commands
{% highlight yaml %}
install:
  - cd ..
  - wget http://www.renpy.org/dl/6.99.1/renpy-6.99.1-sdk.tar.bz2
  - tar xf renpy-6.99.1-sdk.tar.bz2
  - rm renpy-6.99.1-sdk.tar.bz2
  - mv renpy-6.99.1-sdk renpy
  - cd renpy
 {% endhighlight %}

This section of the code tells Travis CI to install Ren'Py. This specific implementation of the script has Travis CI install Ren'Py 6.99.1 . You can change the version of Ren'Py that it installs by changing the download link in the "wget" statement and the names of the "renpy-6.99.1-sdk" and "renpy-6.99.1-sdk.tar.bz2" folders to match the appropriate names of the corresponding folders in the version of Ren'Py that you want to use.

### Test command
{% highlight yaml %}
script: ./renpy.sh "../ganbatte/" lint && ./renpy.sh launcher distribute "../ganbatte/"
{% endhighlight %}

This section of the code is what actually tests the game. First it runs the game through Lint via the Ren'Py Launcher "./renpy.sh". Then if it passes through the Lint script it attempts to build the game.

Note that it is in this section of the code that you will need to change all instances of "ganbatte" to the name of the game you are testing.


## Conclusion
Once you have the ".travis.yml" file setup, and Travis CI enabled for the game's repository the system should now be working. Now whenever you push changes to your Github repository, or when someone makes a pull request, the repository or pull request respectively will be run through the Lint script and will be test built by Travis CI.

For more information on working with Ren'Py in a setting similar to this, you may want to check out Tumblr user dlksk's guide on [getting Ren'Py to run on the Raspberry PI](http://dlksk.tumblr.com/post/107500026059/getting-renpy-to-run-on-the-raspberry-pi). Even if you aren't working with Raspberry PI it is a helpful guide on installing Ren'Py via terminal commands. I used it to help put together the ".travis.yml" file above.

If you need to find more information on using Travis CI, then you may want to check out the [Travis CI Documentation](http://docs.travis-ci.com/).
