# [Developer’s Handbook](http://www.wearenext.co.za/readme/developers-handbook/)

## Table of Contents

* [Welcome](#welcome)
* [Philosophy](#philosophy)
  * [Monolith First](#monolith-first)
* [Process and Communication](#process-and-communication)
  * [GitHub](#github)
  * [Workflow](#workflow)
* [Documentation](#documentation)
* [Stack](#stack)
  * [Server](#server)
  * [Client](#client)
  * [Frameworks](#frameworks)
* [Standards](#standards)
  * [PHP](#php)
  * [JavaScript](#javascript)
  * [Versioning](#versioning)
* [Tooling](#tooling)
  * [Build Tools](#build-tools)
  * [Text Editor](#text-editor)
* [Testing](#testing)
  * [Continuous Integration](#continuous-integration)
* [Monitoring](#monitoring)
  * [Exception Tracking](#exception-tracking)
  * [Uptime Monitoring](#uptime-monitoring)
  * [Server Monitoring](#server-monitoring)
  * [Analytics](#analytics)
* [Launch Policy](#launch-policy)
* [Performance](#performance)
* [Finer Details](#finer-details)
  * [SSL + TLS](#ssl-tls)
  * [Canonical URLs](#canonical-urls)
* [Remote Working](#remote-working)
* [Must Watch](#must-watch)
* [Must Listen](#must-listen)
* [Must Read](#must-read)
* [Learning more](#learning-more)
* [Zombie Apocalypse](#zombie-apocalypse)

## Welcome

Welcome to the Next Developer’s Handbook!

This is a [living documentation](https://en.wikipedia.org/wiki/Living_document)
about our best practices, technology stack and development standards. It is
important that these guidelines are considered the baseline for new products
and services. Deciding against any of these practices should be discussed with
your team first. Similarly, if a project grows big enough to warrant new
workflows, technologies or systems, please discuss it with your team first.

Changes and suggestions are welcome! Please do send a [pull
request](https://github.com/we-are-next/readme/pulls) or [create an
issue](https://github.com/we-are-next/readme/issues/new) :)

## Philosophy

> “Make it work ➤ Make it right ➤ Make it fast”
– [DHH](https://twitter.com/dhh/status/600667857639309313)

Much of how we work is inspired by the [Lean Startup
Principles](http://theleanstartup.com/principles), we love building minimum
viable products, measuring, learning and iterating over that cycle.

We love writing beautiful code! Beauty, however, is in the eye of the beholder.
For us, beautiful code is code that is simple, sturdy, well tested and works.

### Monolith First

> “I see you have a poorly structured monolith. Would you like me to convert it
> into a poorly structured set of microservices?” – [Architect Clippy](https://twitter.com/architectclippy/status/570025079825764352)

Modules, packages, libraries and micro services are all great things but they
are not the starting point.

We always take the approach of building monoliths first. Once we understand
module boundaries and how the application is structured we can then start
destructuring, refactoring and extracting functionality into little pieces if
required.

- [MonolithFirst — Martin Fowler](http://martinfowler.com/bliki/MonolithFirst.html)
- [MicroservicePremium — Martin Fowler](http://martinfowler.com/bliki/MicroservicePremium.html)
- [RailsConf 2015 — Opening Keynote](https://www.youtube.com/watch?v=KJVTM7mE1Cc&amp;t=1316)
- [10+ Years of Rails with DHH](https://changelog.com/145/)

## Process and Communication

> Don’t go dark. Don’t be that guy in the room. Hiding your code until it’s
> “done” may feel safer, but it isn’t. – [Jeff Atwood](http://blog.codinghorror.com/dont-go-dark/)

If it’s not on [Slack](https://wearenext.slack.com/) or
[GitHub](https://github.com/orgs/we-are-next/dashboard), it didn’t happen.

### GitHub

> “Developers who work for long periods -- and by long I mean more than a day
> -- without checking anything into source control are setting themselves up
> for some serious integration headaches down the line.” – [Jeff Atwood](http://blog.codinghorror.com/about-me/)

**[Check In Early, Check In
Often](http://blog.codinghorror.com/check-in-early-check-in-often/)**

The GitHub News Feed is in some ways the news feed of our company. Don’t work
in a vacuum, **if the code isn’t checked into source control, it doesn’t
exist.**

There’s a big difference between broken code and incomplete code. If your code
is incomplete [work in
a branch](http://jonrohan.codes/fieldnotes/dead-simple-git-workflow-for-agile-teams/),
nobody is going to judge your work. Incomplete code shows progress, thinking
and attempts at implementation. No code shows nothing.

### Workflow

Our projects are usually small enough for the [GitHub
Flow](https://guides.github.com/introduction/flow/) to work perfectly for us!
This keeps things simple as well as inclusive, allowing designers and product
owners to collaborate with us :)

If the decision has been made to use a different method of collaboration
using Git then please make sure everyone in your team is aware of that.

- [Understanding the GitHub Flow](https://guides.github.com/introduction/flow/)
- [GitHub Flow](http://scottchacon.com/2011/08/31/github-flow.html)
- [Git Workflows That Work](http://blog.endpoint.com/2014/05/git-workflows-that-work.html)
- [GitHub Flow in the Browser](https://help.github.com/articles/github-flow-in-the-browser/)

## Documentation

> “A project without documentation is like a project that doesn’t exist.”
– [Verbose](https://github.com/verbose/)

The bare minimum, in terms of documentation, is a readme that has instructions
for getting a new developer up an running with your project, able to contribute
code and get code onto a production or staging server.

Beyond a readme the best kind of documentation you can have is [clean
code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882).

If you’re writing code that other people depend on, for example a library or
package, then [keeping a changelog](http://keepachangelog.com/) is a very good
idea.

## Stack

### Server

- Ubuntu
- Nginx
- PHP 5.6+
- MySQL
- Memcache

### Client

- HTML
- Less/Sass
- JavaScript

### Frameworks

- [Laravel](http://laravel.com/)
- [Node](https://nodejs.org/)

## Standards

### PHP

All PHP code must conform to [PSR-1](http://www.php-fig.org/psr/psr-1/),
[PSR-2](http://www.php-fig.org/psr/psr-2/) and
[PSR-4](http://www.php-fig.org/psr/psr-4/).

All PHP must be run through a linter, such as [phplint](https://www.npmjs.com/package/phplint).

### JavaScript

All JavaScript code, must conform to our [ESLint](https://github.com/we-are-next/javascript)
ruleset.

### Versioning

When writing packages or modules, they must be versioned using [Semantic
Versioning](http://semver.org/). We do this to communicate changes to people
depending on your code.

Given a version number MAJOR.MINOR.PATCH, increment the:

1. MAJOR version when you make incompatible API changes,
2. MINOR version when you add functionality in a backwards-compatible manner,
3. and PATCH version when you make backwards-compatible bug fixes.

## Tooling

### Build Tools

**`npm install` and `npm start` should be all that’s required to get your
dependencies installed and a development server running.**

All of our build tools are written in JavaScript and run on Node, using either
[Grunt](http://gruntjs.com/), [Gulp](http://gulpjs.com/) or just plain old
[NPM](https://www.npmjs.com/).

Check out [How to Use npm as a Build
Tool](http://blog.keithcirkel.co.uk/how-to-use-npm-as-a-build-tool/) as an
excellent example of keeping things simple.

### Text Editor

You’re welcome to use any text editor or IDE that you like, but please ship
an [EditorConfig](http://editorconfig.org/) file with your project. This will
help our different editors play nicely together.

## Testing

**All project tests must run with the `npm test` command.**

Testing is a massive subject, but the important note here is that it is
irresponsible of us as professionals to not write tests. We have different
preferences as to when we write tests, how to write tests, what we should
actually test… but the important thing is that there *are* tests.

Don’t aim for 100% code coverage, we aren’t launching space rockets here! Try
have at least some integration tests that make sure important routes return
a `200 OK` HTTP response code.

Laravel ships with an [example
test](https://github.com/laravel/laravel/blob/6df868a123a8445de1aceba1349c550b1247aff0/tests/ExampleTest.php)
that checks if the home page responds successfully. Having this test setup and
running on a continuous integration server is **infinitely** better than having
no tests at all.

Treat each new bug as an opportunity to create a [regression
test](http://en.wikipedia.org/wiki/Regression_testing) and gradually increase
your code coverage.

### Continuous Integration

We use [Travis Pro](https://magnum.travis-ci.com/) for continuous integration.

CI is mandatory on every project. It should be configured as early on in the
project as possible, preferably day one. Even if all that’s happening is
linting and style checking – that’s great!

Remember, this isn’t just for us. We often work with external collaborators and
have no control over their development environment or tooling.

## Monitoring

Before any code is running on a server, all standard monitoring tools must be
installed. This includes staging servers.

### Exception Tracking

We use [Sentry](https://app.getsentry.com/) for tracking exceptions.
Make sure to add user information when it’s available. This allows us to be
proactive with clients and offer much better customer support.

### Uptime Monitoring

We use [Pingdom](https://www.pingdom.com/) for uptime monitoring. Pingdom’s
real user metrics are also useful for measuring performance in scenarios where
New Relic isn’t available.

Uptime monitoring allows us to proactively communicate with the client about
an outage and what we are doing to fix it. This puts a positive spin on what
could otherwise be a negative experience.

### Server Monitoring

We use [New Relic](http://newrelic.com/) for server monitoring.

If we’re managing the servers on a project then please make sure New Relic is
installed. Forge can do this for you :)

### Analytics

We use [Google Analytics](http://www.google.co.za/analytics/) for tracking
custom events and page views. Make sure you get a tracking code from your
product owner. Refuse to launch without one, even on staging.

## Launch Policy

When we launch, things get real. We can never be 100% certain things will go
smoothly for launch so we need to follow a couple of principles for when we
launch or release major updates.

1. Never release anything major on a Friday
2. Get someone else to test your work
3. Make sure you are available on release days, don’t make other commitments
4. Keep an eye on Sentry notifications and Google Analytics

**Plan for outages.** Ask your project lead about the design requirements for
4xx/5xx pages and implement them. Test that these pages work and that they will
be called in the event of 4xx/5xx errors actually happening.

## Performance

Make sure everyone is clear as to performance expectations on a project. As
a baseline, make sure you’ve tested your project using the following tools and
team members are aware of the results as well as bottlenecks or areas of
improvement.

- [WebPagetest](http://www.webpagetest.org/)
- [PageSpeed](https://developers.google.com/speed/pagespeed/)
- [Pingdom Tools](http://tools.pingdom.com/)
- [tmi](https://www.npmjs.com/package/tmi)
- [CSS Stats](http://cssstats.com/)
- [Laravel Debugbar](https://github.com/barryvdh/laravel-debugbar)

Performance is a massive topic, but here are some useful places to start
learning and reading up on the subject.

- [Perf.Rocks](http://perf.rocks/)
- [Performance Calendar](http://calendar.perfplanet.com/)
- [How Users Perceive the Speed of The Web](https://www.youtube.com/watch?v=2ksXo2_Lfl0)

## Finer Details

### HTTPS + TLS

TLS over HTTPS is mandatory on any project that involves user input. It is ultimately the
clients call as there is a minor financial cost. It would, however, be
unprofessional of us to not educate them of the implications.

- Use the [Mozilla SSL Configuration
  Generator](https://mozilla.github.io/server-side-tls/ssl-config-generator/),
  even if you’ve installed the certificate with Forge.
- Test the installation with the [Thawte SSL Certificate
  Checker](https://ssltools.thawte.com/checker/views/certCheck.jsp).
- Test browser support using [BrowserStack](https://www.browserstack.com), we
  have a paid account for this very reason.

[10 Reasons To Use HTTPS](https://medium.com/so-now-you-know/10-reasons-to-go-https-a2cba5734bb6)

### Canonical URLs

For canonical urls we [use www](http://www.yes-www.org/why-use-www/) without
trailing slashes.

e.g. [http://www.wearenext.co.za/people](http://www.wearenext.co.za/people)

To use or not use trailing slashes is a subjective matter. We have decided
against using them because they aren’t as aesthetically pleasing, add an
extra character to URLs and often lead to extra work in configuring web
servers.

[Trailing slash or not](http://googlewebmastercentral.blogspot.com/2010/04/to-slash-or-not-to-slash.html), either should work, but the incorrect URL
should ideally perform a 301 Permanent Redirect to the canonical URL.

```
http://wearenext.co.za → http://www.wearenext.co.za
```

```
http://wearenext.co.za/people/ → http://www.wearenext.co.za/people
```

## Remote Working

We want you to be able to work wherever you’re going to get work done. Next has
had a remote working policy since day one. Which you can read about in depth here.
But with much freedom comes *some* responsibility.

- **Notice**: Tell people in advance when you’re wanting to work remotely
- **Communication**: Be more communicative than you’d ordinarily be to make up for the fact that we can’t walk past your computer, bump into you at the watercooler or smell your cologne
- **Going AFK**: Tell us what you’re doing, tell people when you’re stepping away from the keyboard
- **Share your work**: when it’s work in progress, when it’s done, when it’s not working out
- **Save** your code – often

Remote working is kind of a new thing for many people who join us, so we wrote a separate [remote handbook](remote-handbook.md) which you can read about in depth.

## Must Watch

- [Product development = tradeoffs](https://www.youtube.com/watch?v=znBtzBAS9Bo)
- [How GitHub Uses GitHub to Build GitHub](https://www.youtube.com/watch?v=qyz3jkOBbQY)

## Must Listen

- [Tiny Decisions and Emergent Design](http://fullstackradio.com/episodes/16/)
- [Architecture, Patterns and Design](http://fullstackradio.com/episodes/9/)
- [Awesome Podcasts](http://github.com/wayneashleyberry/awesome-podcasts)

## Must Read

- [The Lean Startup](http://theleanstartup.com/)
- [The Clean Coder](http://www.amazon.com/Clean-Coder-Conduct-Professional-Programmers/dp/0137081073)
- [Clean Code](http://www.amazon.com/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882)
- [Rework](http://www.amazon.com/Rework-Jason-Fried/dp/0307463745)
- [Getting Real](http://www.amazon.com/Getting-Real-Jason-Fried-ebook/dp/B0053KHGWM)
- [Awesome Newsletters](https://github.com/wayneashleyberry/awesome-newsletters)

## Learning more

We have a paid [Laracasts](https://laracasts.com/) account, use it :)

## Zombie Apocalypse

In case of a Zombie Apocalypse or an equally catastrophic end of world event,
you have the freedom to stop working and focus on your survival. We highly
recommend the [Zombie Survival
Guide](http://www.amazon.com/Zombie-Survival-Guide-Max-Brooks-ebook/dp/B003WE9WRI),
get the hardcover, your Kindle’s not gonna last long without electricity.
