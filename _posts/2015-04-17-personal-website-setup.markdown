---
layout: post
title:  "Setting up a Personal Website on a Budget of Zero"
author: "Christopher Randall Wells"
image: "/images/personal_website_on_budget.png"
date:   2015-04-17 19:34:00
categories: web-design jekyll git github divshot
---
Recently I decided to make myself a personal website, as I figured that it would become useful as I entered college and eventually in my career as well. Unfortunately, as I was a high school senior who wasn't really into spending money on the internet, I had to do so in a way that was free, but still looked decently professional. Throughout the process of researching for and working on my website I learned a little bit about making personal websites on a budget of zero dollars and zero cents.

## Jekyll
Before I had started any work on the website I had decided to use [Jekyll](http://jekyllrb.com/) to generate it. I had worked with Jekyll before on an earlier project, and it proved to be very helpful in terms of easily making changes to the website. With Jekyll, if I wanted to change the header or footer of my website I could so by just editing one file, as opposed to having to edit all the files of my website (which I would've liked had to do if I decided to go with using just basic HTML and CSS coding).

While Jekyll its self uses Ruby coding, working with Jekyll on a basic level does not really require too much, if any, knowledge of Ruby. For the most part, Jekyll uses HTML and [Kramdown](http://kramdown.gettalong.org/) to code most of the website's pages. Jekyll also uses CSS and SASS to handle most of the styling of the website.

Using Jekyll, I was able to easily build my website off of the base template provided by default, thus I did not have to deal with taking the time to code basic the site structure. With Jekyll I was also able to easily generate a static version of my website so that I could upload it to my web host.

## Git & GitHub
I decided to use [Git](http://git-scm.com/) and [GitHub](https://github.com/) in the development of my website in order to keep better track of the development process and to use some of the useful features of Git and GitHub. Luckily I was already somewhat familiar with both from earlier projects that I worked on.

With Git, I would be able to keep a log of all of the changes that I make to the website, so I would be able to locate problematic code more easily. Git's branches feature would also allow me to work on different parts of the website separately at the same time. I would also be able to do work on the website in isolated branches in order to be sure to keep a working master branch, in case any changes I made caused issues.

With GiHub I would be able to host the Git repository I had for the website online. By keeping a copy of the website's source code online I would always be able to clone the repository from GitHub in case anything happened to my local copy of the source code. While in order to be able to host my source code for free on GitHub I had to host it publicly, I figured that hosting it publicly wouldn't likely be a problem, since I was just using the website for personal use, thus the downsides of keeping the source code online would likely be minimal.

I also decided to use GitHub because of the various features that it provides for Git repos. Using GitHub's issue tracker I would be able to create notes on things that I want to add to the websites and changes I plan to make in the future. GitHub's pulse and analytics graphs would also allow me to keep better track of how much work I have done on the website over time. I also could use GitHub's integration with [Travis CI](https://travis-ci.org/) to have my website's code run through [htmlproofer](https://github.com/gjtorikian/html-proofer) every time I update the GitHub repository. In order to make sure that the website builds and runs properly.

## Divshot
While I had already done some work with Jekyll, Git, and GitHub, I had not yet had much experience with web hosting. After doing a bit of research on web hosting websites, I eventually settled on [Divshot](https://divshot.com/). During my research I had found a few other hosting websites that I could've used, such as [Heroku](https://www.heroku.com/) and [Amazon S3](http://aws.amazon.com/s3/), however I ended up deciding to use Divshot.

With Divshot I would be able to have my static website hosted for free. Since I didn't plan on getting a custom domain name I found that Divshot's default subdomain for hosted websites is `websitenamehere.divshot.io`, which in my opinion looks somewhat more professional than most web hosting subdomains, especially with its use of the `.io` top-level domain.

In addition, Divshot was advertised to work well with Jekyll. I found that it was somewhat easy to push my Jekyll-based website to Divshot using the `jekyll build && divshot push` command to easily build and push the static site.

## Conclusion
By using the free programs Git and Jekyll, as well as the websites GitHub, Travis CI, and Divshot, I was able to create a free personal website for myself.

While I was able to make the website for free, if I ever do decide to invest some money in my website I'd likely use it to buy a proper custom domain name. Git, GitHub, Jekyll, and Travis CI are all fairly solid programs and websites without the need to purchase any paid membership. But getting a custom domain name would be the next logical improvement in the website's development that would require the investing of money.
