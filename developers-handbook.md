# Developer's Handbook

## Table of Contents

* [Welcome](#welcome)
* [Philosophy](#philosophy)
* [Process and Communication](#process-and-communication)
  * [GitHub](#github)
* [Day One](#day-one)
* [Prototyping](#prototyping)
  * [Further Reading](#further-reading)
* [Documentation](#documentation)
* [Stack](#stack)
  * [Backend](#backend)
  * [Frontend](#frontend)
  * [Frameworks](#frameworks)
  * [Services](#services)
* [Standards](#standards)
  * [PHP](#php)
  * [JavaScript](#javascript)
* [Tooling](#tooling)
  * [Build Tools](#build-tools)
  * [Editor](#editor)
* [Testing](#testing)
  * [Continuous Integration](#continuous-integration)
* [Monitoring](#monitoring)
  * [Sentry](#sentry)
  * [Pingdom](#pingdom)
  * [New Relic](#new-relic)
  * [Google Analytics](#google-analytics)
* [Launch Policy](#launch-policy)
* [Performance](#performance)
  * [Other Profiling Tools](#other-profiling-tools)
  * [Further Reading](#further-reading)
* [Finer Details](#finer-details)
  * [SSL](#ssl)
  * [Canonical URL's](#canonical-urls)
  * [Further Reading](#further-reading)
* [Must Watch](#must-watch)
* [Must Listen](#must-listen)
* [Must Read](#must-read)
* [Further Resources](#further-resources)
  * [Tutorials](#tutorials)
  * [Podcasts](#podcasts)
  * [Newsletters](#newsletters)
  * [Websites](#websites)

### Welcome

**This document, and our company, is a work in progress.**

Changes, suggestions and disagreements are more than welcome! Feel free to send
a pull request :)

Consider these guidelines the baseline for new products and services.  If you
decide not to implement one of these practices, please communicate that with
your team.

### Philosophy

Much of how we work is inspired by the [Lean Startup
Principles](http://theleanstartup.com/principles), we love building minimum
viable products, measuring, learning and iterating over that cycle.

> “Make it work ➤ Make it right ➤ Make it fast”
— [DHH](https://twitter.com/dhh)

If there were a battle between pragmatism and architectural purism, we'd be
team pragmatism all the way! Perfectly architected code is great, but that is
not our goal as a business. We have to meet business requirements and strive to
make users happier and more productive. At the end of the day, code is just
a means to an end.

> “You're better off with a kick-ass half than a half-assed whole.”
— [DHH](https://twitter.com/dhh)

### Process and Communication

**Never, ever, [go dark](http://blog.codinghorror.com/dont-go-dark/).**

Everything, absolutely everything, happens on
[Slack](https://wearenext.slack.com/) and
[GitHub](https://github.com/orgs/we-are-next/dashboard).

#### GitHub

**[Check In Early, Check In
Often](http://blog.codinghorror.com/check-in-early-check-in-often/)**

> “Developers who work for long periods -- and by long I mean more than a day
> -- without checking anything into source control are setting themselves up
> for some serious integration headaches down the line.” — [Jeff Atwood](http://en.wikipedia.org/wiki/Jeff_Atwood)

The GitHub News Feed is in some ways the news feed of our company. Don't work
in a vacuum, **if the code isn't checked into source control, it doesn't
exist.**

There's a big difference between broken code and incomplete code. If your code
is incomplete [work in
a branch](http://jonrohan.codes/fieldnotes/dead-simple-git-workflow-for-agile-teams/),
nobody is going to judge your work. Incomplete code shows progress, thinking
and attempts at implementation. No code shows nothing.

### Day One

Dedicate the first day of a *new project* to getting the environment setup.

- Create a GitHub repo
- Provision a staging server
- Setup automatic deployment
- Setup continuous integration
- Add tests for code style and linting errors
- Integrate error tracking
- Integrate Google Analytics
- Configure Slack integrations
- Document these things in the readme
- Send the url to your team

### Prototyping

We place incredible value on prototyping because prototypes are a common ground
that encourage discussion and colaboration.  Developers, designers, writers,
marketers, business owners - everyone understands prototypes.

We use [Invision](http://www.invisionapp.com/) because it’s the easiest way for
us to stitch static images into experience that people can use and comment on.

#### Further Reading

- [Why We Prototype](http://cognition.happycog.com/article/why-we-prototype)
- [The Skeptic’s Guide To Low-Fidelity
  Prototyping](http://www.smashingmagazine.com/2014/10/06/the-skeptics-guide-to-low-fidelity-prototyping/)

### Documentation

> “A project without documentation is like a project that doesn't exist.”
— [Verbose](https://github.com/verbose/)

The bare minimum, in terms of documentation, is a readme that has instructions
for getting a new developer up an running with your project, able to contribute
code and get that code onto a production or staging server.

A good way to test this is to ask someone who's not working on the project to
fix a bug or add a feature - but they're not allowed to ask for help. That'll
soon put your documentation to the test! The aim here is to reduce the [bus
factor](http://en.wikipedia.org/wiki/Bus_factor) and encourage collaboration.

Beyond a readme the best kind of documentation you can have is [clean
code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_1?ie=UTF8&qid=1432230912&sr=8-1&keywords=clean+code).

_Bonus points for [keeping a changelog](http://keepachangelog.com/)._

### Stack

#### Backend

- Ubuntu
- Nginx
- PHP 5.6+
- MySQL
- Memcache

#### Frontend

- HTML
- Less
- JavaScript

#### Frameworks

- [Laravel](http://laravel.com/)
- [Node](https://nodejs.org/)
- [React](https://facebook.github.io/react/)

#### Services

- [Travis CI](https://magnum.travis-ci.com/) for Continuous Integration.
- [Digital Ocean](https://www.digitalocean.com/) for hosting.
- [Laravel Forge](https://forge.laravel.com/) for server provisioning.
- [Envoyer](https://envoyer.io/) for fancy deployments.
- [Google Analytics](http://www.google.co.za/analytics/) for user tracking.
- [Sentry](https://app.getsentry.com/) for error reporting.
- [Cloudinary](http://cloudinary.com/) for image manipulation and hosting.
- [New Relic](http://newrelic.com/) for server monitoring.
- [Browserstack](https://www.browserstack.com) for browser testing.

### Standards

#### PHP

All PHP code must conform to [PSR-1](http://www.php-fig.org/psr/psr-1/),
[PSR-2](http://www.php-fig.org/psr/psr-2/) and
[PSR-4](http://www.php-fig.org/psr/psr-4/). In addition, all PHP should be free
of any linting errors. See [phplint](https://www.npmjs.com/package/phplint) as
a faster alternative to using php's native linter.

#### JavaScript

All JavaScript code, browser or other-wise, must conform to our standard
[ESLint](http://eslint.org/) configuration, which you can get
[here](https://github.com/we-are-next/javascript).

### Tooling

#### Build Tools

All of our build tools are written in JavaScript and run on Node, using either
[Grunt](http://gruntjs.com/), [Gulp](http://gulpjs.com/) or just plain old
[NPM](https://www.npmjs.com/).

If possible, `npm install` and `npm start` should be all that's required to get
your project up and running.

##### Further Reading

- [How to Use npm as a Build Tool](http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/)

#### Editor

You're welcome to use any editor that you like. We already have Sublime, Vim,
and WebStorm users in house, yay! With this freedom comes responsibilty though,
please make sure you add an [EditorConfig](http://editorconfig.org/) to your
project so that our editors can play along nicely.

If your editor provides handy tooling and plugins, please make sure that you
have the equivalent setup on CI to bring consistency across different
environment.

### Testing

All project tests should be setup to run with `npm test`.

Testing is a massive subject, but the important note here is that it is
irresponsible of us as professionals to not write automated tests. We have
different preferences as to when we write tests, how to write tests, what tests
should actually test... but the important thing is that there *are* tests.

Dont' aim for 100% code coverage, we aren't launching space rockets here,
well.. not yet. Try have at least some integration tests that make sure
important routes return a `200 OK` HTTP response code.

Laravel ships with an example test that makes sure your home page responds
successfully. Having this test setup and running on a continuous integration
server is **infinitely** better than having no tests at all.

Treat each new bug as an opportunity to create a [regression
test](http://en.wikipedia.org/wiki/Regression_testing) and gradually increase
your code coverage.

#### Continuous Integration

Continuous integration is mandatory on every project. It should be configured
as early on in the project as possible, preferably day one. Even if all that's
happening is linting and style checking - that's great!

We have a [Travis Pro](https://magnum.travis-ci.com/) account, use it, go crazy
:)

Remember, this isn't just for us. We often have external collaborators on code
and have no control over their development environment or tooling.

### Monitoring

It is of utmost importance that before code is running on a server all our
standard monitoring tools are installed. This includes staging servers. Without
this data we are operating blind as we have no data to base any decisions or
discussions on.

These services cost money and the decision to not use one of them should be an
explicit one agreed to by each party involved. The implications of not
monitoring something for whatever reason need to be well understood.

#### Sentry

We use [Sentry](https://app.getsentry.com/) for tracking exceptions.
Make sure to add user information when it's available. Tracking exceptions down
their occurrences with individual users is incredibly useful.

#### Pingdom

We use [Pingdom](https://www.pingdom.com/) for uptime monitoring. Pingdom's
real user metrics are also useful for measuring performance in scenarios where
New Relic isn't available.

Uptime monitoring allows us to proactively communicate with the client about
an outage and what we are doing to fix it. This puts a positive spin on what
could otherwise be a negative experience.

#### New Relic

If we're managing the servers on a project then please make sure New Relic is
installed. Forge can do this for you :)

#### Google Analytics

We use [Google Analytics](http://www.google.co.za/analytics/) for tracking
custom events and page views. Make sure you get a tracking code from your
product owner. Refuse to launch without one, even on staging.

### Launch Policy

When we launch, things get real. We can never be 100% certain things will go
smoothly for launch so we need to follow a couple of principles for when we
launch or release major updates.

1. Never release anything major on a Friday
2. Get someone else to user test your work (this includes them running your
   test suite)
3. Make sure you are available on release days, don't make other commitments
4. Go through the [Web Developer Checklist](http://webdevchecklist.com/)
5. Keep an eye on Sentry notifications and Google Analytics

Plan for outages. Ask your project lead about the design requirements for
4xx/5xx pages and implement them. Test that these pages work and that they will
be called in the event of 4xx/5xx errors actually happening. Ask your project
lead about static fallback pages that can be engaged at critical points of the
application:

1. Is there a static page we can enable, for the homepage, if we need to make
   changes to the actual homepage during peak traffic?
2. Is there a static page we can enable, for user profiles, if we need to make
   changes to the actual profile pages during peak traffic?
3. Is there a static page we can enable if the commerce/news/whatever
   application is having a bad day?

### Performance

Make sure everyone is clear as to performance expectations on a project.  As
a baseline, make sure you've tested your project using the following tools and
team members are aware of the general performance results.

- [WebPagetest](http://www.webpagetest.org/)
- [PageSpeed](https://developers.google.com/speed/pagespeed/)
- [Pingdom Tools](http://tools.pingdom.com/)

#### Other Profiling Tools

- [tmi](https://www.npmjs.com/package/tmi)
- [CSS Stats](http://cssstats.com/)
- [Laravel Debugbar](https://github.com/barryvdh/laravel-debugbar)

#### Further Reading

- [Perf.Rocks](http://perf.rocks/)
- [Performance Calendar](http://calendar.perfplanet.com/)
- [How Users Perceive the Speed of The Web](https://www.youtube.com/watch?v=2ksXo2_Lfl0)

### Finer Details

#### SSL

SSL is mandatory on any project that expects user input.  It is ultimately the
clients call as there is a financial cost, but it would be unprofessional of us
to not educate them of the implications.

- Use the [Mozilla SSL Configuration
  Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/),
  even if you've installed the certificate with Forge.
- Test the installation with the [Thawte SSL Certificate
  Checker](https://ssltools.thawte.com/checker/views/certCheck.jsp).
- Test browser support using [Browserstack](https://www.browserstack.com), we
  have a paid account for this very reason.

##### Further Reading

- [Deprecating Non-Secure HTTP](https://blog.mozilla.org/security/2015/04/30/deprecating-non-secure-http/)

#### Canonical URL's

For canonical urls we use www without trailing slashes.

eg. [http://www.wearenext.co.za/people](http://www.wearenext.co.za/people)

To use or not use trailing slash's is a subjective matter.  We have decided
against using them because they aren't as aesthetically pleasing, add an
extra character to url's and often lead to extra work in configuring web
servers.

Regardless of trailing slash or not, either should work, but the incorrect url
should perform a 301 Permanent Redirect to the canonical url.

- http://wearenext.co.za redirects to http://www.wearenext.co.za
- http://wearenext.co.za/people/ redirects to http://www.wearenext.co.za/people

#### Further Reading

- [Why use www?](http://www.yes-www.org/why-use-www/)
- [To slash or not to slash](http://googlewebmastercentral.blogspot.com/2010/04/to-slash-or-not-to-slash.html)

### Must Watch

- [Product development = tradeoffs](https://www.youtube.com/watch?v=znBtzBAS9Bo)
- [How GitHub Uses GitHub to Build GitHub](https://www.youtube.com/watch?v=qyz3jkOBbQY)
- [How Designers Destroyed the World](https://vimeo.com/68470326)

### Must Listen

- [Tiny Decisions and Emergent Design](http://fullstackradio.com/episodes/16/)
- [Architecture, Patterns and Design](http://fullstackradio.com/episodes/9/)

### Must Read

- [The Lean Startup](http://theleanstartup.com/)
- [The Clean Coder](http://www.amazon.com/Clean-Coder-Conduct-Professional-Programmers/dp/0137081073/ref=sr_1_1)
- [Clean Code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
- [Rework](http://www.amazon.com/Rework-Jason-Fried/dp/0307463745/ref=sr_1_5)
- [Getting Real](http://www.amazon.com/Getting-Real-Jason-Fried-ebook/dp/B0053KHGWM/ref=asap_bc?ie=UTF8)

### Further Resources

**[A curated list of awesome lists](https://github.com/sindresorhus/awesome)**
is a great place to start!

#### Tutorials

We have a paid [Laracasts](https://laracasts.com/) account, use it :)

#### Podcasts

[Awesome Podcasts](http://github.com/wayneashleyberry/awesome-podcasts)

#### Newsletters

[Awesome Newsletters](https://github.com/wayneashleyberry/awesome-newsletters)

#### Websites

- [A List Apart](http://alistapart.com/)

### Zombie Apocalypse

In case of a Zombie Apocalypse or an equally catastrophic end of world event,
you have the freedom to stop working and focus on your survival. We highly
recommend the [Zombie Survival
Guide](http://www.amazon.com/Zombie-Survival-Guide-Max-Brooks-ebook/dp/B003WE9WRI/ref=sr_1_1?ie=UTF8&qid=1416475767&sr=8-1&keywords=zombie+survival+guide),
get the hardcover, your Kindle's not gonna last long without electricity.
