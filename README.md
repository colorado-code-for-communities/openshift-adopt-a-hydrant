## Screenshot
![Adopt-a-Hydrant](https://github.com/codeforamerica/adopt-a-hydrant/raw/master/screenshot.png "Adopt-a-Hydrant")

## Demo
You can see a running version of the application at
[http://hydrant-mjelen.rhcloud.com/][demo].

[demo]: http://hydrant-mjelen.rhcloud.com/

## Installation

Create OpenShift application

	rhc app create hydrant ruby-1.9

and note the SSH url. Then add PostgreSQL support

	rhc cartridge add postgresql-8.4 --app hydrant

Enter the application directory on your local machine

	cd hydrant

Pull this github repository

	git pull -s recursive -X theirs git://github.com/marekjelen/openshift-adopt-a-hydrant.git

Generate new session secret

    rake secret

Copy&paste the hash into

    .openshift/action_hooks/pre_start_ruby-1.9

Add and commit

  git add . && git commit -m "Deploying Adopt-a-Hydrant"

Push it back up to your gear

	git push

SSH to the SSH url

	ssh <your url>

and enter the directory with application

	cd app-root/repo

and seed the hydrants

	bundle exec rake db:seed

ad that is all ;)

## Contributing
In the spirit of [free software][free-sw], **everyone** is encouraged to help
improve this project.

[free-sw]: http://www.fsf.org/licensing/essays/free-sw.html

Here are some ways *you* can contribute:

* by using alpha, beta, and prerelease versions
* by reporting bugs
* by suggesting new features
* by [translating to a new language][locales]
* by writing or editing documentation
* by writing specifications
* by writing code (**no patch is too small**: fix typos, add comments, clean up
  inconsistent whitespace)
* by refactoring code
* by closing [issues][]
* by reviewing patches
* [financially][]

[locales]: https://github.com/codeforamerica/adopt-a-hydrant/tree/master/config/locales
[issues]: https://github.com/codeforamerica/adopt-a-hydrant/issues
[financially]: https://secure.codeforamerica.org/page/contribute

## Submitting an Issue
We use the [GitHub issue tracker][issues] to track bugs and features. Before
submitting a bug report or feature request, check to make sure it hasn't
already been submitted. When submitting a bug report, please include a [Gist][]
that includes a stack trace and any details that may be necessary to reproduce
the bug, including your gem version, Ruby version, and operating system.
Ideally, a bug report should include a pull request with failing specs.

[gist]: https://gist.github.com/

## Submitting a Pull Request
1. [Fork the repository.][fork]
2. [Create a topic branch.][branch]
3. Add specs for your unimplemented feature or bug fix.
4. Run `bundle exec rake test`. If your specs pass, return to step 3.
5. Implement your feature or bug fix.
6. Run `bundle exec rake test`. If your specs fail, return to step 5.
7. Run `open coverage/index.html`. If your changes are not completely covered
   by your tests, return to step 3.
8. Add, commit, and push your changes.
9. [Submit a pull request.][pr]

[fork]: http://help.github.com/fork-a-repo/
[branch]: http://learn.github.com/p/branching.html
[pr]: http://help.github.com/send-pull-requests/

## Supported Ruby Version
This library aims to support and is [tested against][travis] Ruby version 1.9.3.

If something doesn't work on this version, it should be considered a bug.

This library may inadvertently work (or seem to work) on other Ruby
implementations, however support will only be provided for the version above.

If you would like this library to support another Ruby version, you may
volunteer to be a maintainer. Being a maintainer entails making sure all tests
run and pass on that implementation. When something breaks on your
implementation, you will be personally responsible for providing patches in a
timely fashion. If critical issues for a particular implementation exist at the
time of a major release, support for that Ruby version may be dropped.

## Copyright
Copyright (c) 2012 Code for America. See [LICENSE][] for details.

[license]: https://github.com/codeforamerica/adopt-a-hydrant/blob/master/LICENSE.md

[![Code for America Tracker](http://stats.codeforamerica.org/codeforamerica/adopt-a-hydrant.png)][tracker]

[tracker]: http://stats.codeforamerica.org/projects/adopt-a-hydrant
