# Contributing to Ruby

Ruby has a vast and friendly community with hundreds of people contributing to
a thriving open-source ecosystem. This guide is designed to cover ways for
participating in the development of CRuby.

There are plenty of ways for you to help even if you're not ready to write
code or documentation.  You can help by reporting issues, testing patches, and
trying out beta releases with your applications.

## How To Report

If you've encountered a bug in Ruby please report it to the redmine issue
tracker available at [bugs.ruby-lang.org](https://bugs.ruby-lang.org/).  Do
not report security vulnerabilities here, there is a [separate
channel](#label-Reporting+Security+Issues) for them.

There are a few simple steps you should follow in order to receive feedback on
your ticket.

*   If you haven't already, [sign up for an
    account](https://bugs.ruby-lang.org/account/register) on the bug tracker.

*   Try the latest version.

    If you aren't already using the latest version, try installing a newer
    stable release. See [Downloading
    Ruby](https://www.ruby-lang.org/en/downloads/).

*   Look to see if anyone already reported your issue, try [searching on
    redmine](https://bugs.ruby-lang.org/projects/ruby-trunk/issues) for your
    problem.

*   If you can't find a ticket addressing your issue, [create a new
    one](https://bugs.ruby-lang.org/projects/ruby-trunk/issues/new).

*   Choose the target version, usually current. Bugs will be first fixed in
    the current release and then [backported](#label-Backport+Requests).

*   Fill in the Ruby version you're using when experiencing this issue (`ruby
    -v`).

*   Attach any logs or reproducible programs to provide additional
    information. Reproducible scripts should be as small as possible.

*   Briefly describe your problem.  A 2-3 sentence description will help give
    a quick response.

*   Pick a category, such as core for common problems, or lib for a standard
    library.

*   Check the [Maintainers
    list](https://bugs.ruby-lang.org/projects/ruby/wiki/Maintainers) and
    assign the ticket if there is an active maintainer for the library or
    feature.

*   If the ticket doesn't have any replies after 10 days, you can send a
    reminder.

*   Please reply to feedback requests. If a bug report doesn't get any
    feedback, it'll eventually get rejected.


### Reporting to downstream distributions

You can report downstream issues for the following distributions via their bug
tracker:

*   [debian](http://bugs.debian.org/cgi-bin/pkgreport.cgi?src=ruby-defaults)
*   [freebsd](http://www.freebsd.org/cgi/query-pr-summary.cgi?text=ruby)
*   [redhat](https://bugzilla.redhat.com/buglist.cgi?bug_status=NEW&bug_status
    =ASSIGNED&bug_status=REOPENED&bug_status=MODIFIED)

*   [macports](http://trac.macports.org/query?status=assigned&status=new&statu
    s=reopened&port=~ruby)

*   etc (add your distribution bug tracker here)


### Platform Maintainers

For platform specific bugs in Ruby, you can assign your ticket to the current
maintainer for a specific platform.

The current active platform maintainers are as follows:

* mswin64 (Microsoft Windows): NAKAMURA Usaku (usa)
* mingw32 (Minimalist GNU for Windows): Nobuyoshi Nakada (nobu)
* IA-64 (Debian GNU/Linux): TAKANO Mitsuhiro (takano32)
* AIX: Yutaka Kanemoto (kanemoto)
* FreeBSD: Akinori MUSHA (knu)
* Solaris: Naohisa Goto (ngoto)
* RHEL, CentOS: KOSAKI Motohiro kosaki
* macOS: Kenta Murata (mrkn)
* cygwin, bcc32, djgpp, wince, ...: none. (Maintainer WANTED)


## Reporting Security Issues

Security vulnerabilities receive special treatment since they may negatively
affect many users. There is a private mailing list that all security issues
should be reported to and will be handled discretely. Email the
mailto:security@ruby-lang.org list and the problem will be published after
fixes have been released. You can also encrypt the issue using [the PGP public
key](https://www.ruby-lang.org/security.asc) for the list.

## Reporting Other Issues

If you're having an issue with the website, or maybe the mailing list, you can
contact the webmaster to help resolve the problem.

The current webmaster is:

*   Hiroshi SHIBATA (hsbt)


You can also report issues with the ruby-lang.org website on the issue
tracker:

*   [issue tracker](https://github.com/ruby/www.ruby-lang.org/issues)


## Resolve Existing Issues

As a next step beyond reporting issues you can help the core team resolve
existing issues. If you check the Everyone's Issues list in GitHub Issues, you
will find a lot of issues already requiring attention. What can you do for
these? Quite a bit, actually:

When a bug report goes for a while without any feedback, it goes to the bug
graveyard which is unfortunate. If you check the [issues
list](https://bugs.ruby-lang.org/projects/ruby-trunk/issues) you will find
lots of delinquent bugs that require attention.

You can help by verifying the existing tickets, try to reproduce the reported
issue on your own and comment if you still experience the bug. Some issues
lack attention because of too much ambiguity, to help you can narrow down the
problem and provide more specific details or instructions to reproduce the
bug. You might also try contributing a failing test in the form of a patch,
which we will cover later in this guide.

It may also help to try out patches other contributors have submitted to
redmine, if gone without notice. In this case the `patch` command is your
friend, see `man patch` for more information. Basically this would go
something like this:

    cd path/to/ruby/trunk
    patch -p0 < path/to/patch

You will then be prompted to apply the patch with the associated files. After
building ruby again, you should try to run the tests and verify if the change
actually worked or fixed the bug. It's important to provide valuable feedback
on the patch that can help reach the overall goal, try to answer some of these
questions:

*   What do you like about this change?
*   What would you do differently?
*   Are there any other edge cases not tested?
*   Is there any documentation that would be affected by this change?


If you can answer some or all of these questions, you're on the right track.
If your comment simply says "+1", then odds are that other reviewers aren't
going to take it too seriously. Show that you took the time to review the
patch.

## How To Request Features

If there's a new feature that you want to see added to Ruby, you will need to
write a convincing proposal and patch to implement the feature.

For new features in CRuby, use the ['Feature'
tracker](https://bugs.ruby-lang.org/projects/ruby-trunk/issues?set_filter=1&tr
acker_id=2) on ruby-trunk. For non-CRuby dependent features, features that
would apply to alternate Ruby implementations such as JRuby and Rubinius, use
the [CommonRuby tracker](https://bugs.ruby-lang.org/projects/common-ruby).

When writing a proposal be sure to check for previous discussions on the topic
and have a solid use case. You will need to be persuasive and convince Matz on
your new feature. You should also consider the potential compatibility issues
that this new feature might raise.

Consider making your feature into a gem, and if there are enough people who
benefit from your feature it could help persuade ruby-core. Although feature
requests can seem like an alluring way to contribute to Ruby, often these
discussions can lead nowhere and exhaust time and energy that could be better
spent fixing bugs. Choose your battles.

A good template for a feature proposal should look something like this:

* Abstract: Summary of your feature
* Background: Describe current behavior and why it is problem. Related work, such as
    solutions in other language helps us to understand the problem.

* Proposal: Describe your proposal in details
* Details: If it has complicated feature, describe it
* Usecase: How would your feature be used? Who will benefit from it?
* Discussion: Discuss about this proposal. A list of pros and cons will help start
    discussion.

* Limitation: Limitation of your proposal
* Another alternative proposal: If there are alternative proposals, show them.
* See also: Links to the other related resources


### Slideshow

At the Ruby Developer Meeting in Japan, committers discuss Feature Proposals
together in Tokyo. We will judge proposals and then accept, reject, or give
feedback for them. If you have a stalled proposal, making a slide to submit is
good way to get feedback.

Slides should be:

*   One-page slide
*   Include a corresponding ticket number
*   MUST include a figure and/or short example code
*   SHOULD have less sentence in natural language (try to write less than 140
    characters)

*   It is RECOMMENDED to itemize: motivation/use case, proposal, pros/cons,
    corner case

*   PDF or Image (Web browsers can show it)


Please note:

*   Even if the proposal is generally acceptable, it won't be accepted without
    writing corner cases in the ticket

*   Slide's example: DevelopersMeeting20130727Japan


## Backport Requests

When a new version of Ruby is released, it starts at patch level 0 (p0), and
bugs will be fixed first on the trunk branch. If it's determined that a bug
exists in a previous version of Ruby that is still in the bug fix stage of
maintenance, then a patch will be backported. After the maintenance stage of a
particular Ruby version ends, it goes into "security fix only" mode which
means only security related vulnerabilities will be backported. Versions in
End-of-life (EOL) will not receive any updates and it is recommended you
upgrade as soon as possible.

If a major security issue is found or after a certain amount of time since the
last patch level release, a new patch-level release will be made.

When submitting a backport request please confirm the bug has been fixed in
newer versions and exists in maintenance mode versions. There is a backport
tracker for each major version still in maintenance where you can request a
particular revision merged in the affected version of Ruby.

Each major version of Ruby has a release manager that should be assigned to
handle backport requests. You can find the list of release managers on the
[wiki](https://bugs.ruby-lang.org/projects/ruby/wiki/ReleaseEngineering).

### Branches

Status and maintainers of branches are listed on the
[wiki](https://bugs.ruby-lang.org/projects/ruby/wiki/ReleaseEngineering).

## Running tests

In order to help resolve existing issues and contributing patches to Ruby you
need to be able to run the test suite.

CRuby uses subversion for source control, you can find installation
instructions and lots of great info to learn subversion on the
[svnbook.red-bean.com](http://svnbook.red-bean.com/). For other resources see
the [ruby-core documentation on
ruby-lang.org](https://www.ruby-lang.org/en/community/ruby-core/).

This guide will use git for contributing.  The [git
homepage](http://git-scm.com/) has installation instructions with links to
documentation for learning more about git. There is a mirror of the subversion
repository on [github](https://github.com/ruby/ruby).

Install the prerequisite dependencies for building the CRuby interpreter to
run tests.

*   C compiler
*   autoconf
*   bison
*   gperf
*   ruby - Ruby itself is prerequisite in order to build Ruby from source. It
    can be 1.8.


You should also have access to development headers for the following
libraries, but these are not required:

*   Tcl/Tk
*   NDBM/QDBM
*   GDBM
*   OpenSSL
*   readline/editline(libedit)
*   zlib
*   libffi
*   libyaml
*   libexecinfo (FreeBSD)


Now let's build CRuby:

*   Checkout the CRuby source code:

        git clone git://github.com/ruby/ruby.git ruby-trunk

*   Generate the configuration files and build:

        cd ruby-trunk
        autoconf
        mkdir build && cd build # its good practice to build outside of source dir
        mkdir ~/.rubies # we will install to .rubies/ruby-trunk in our home dir
        ../configure --prefix="${HOME}/.rubies/ruby-trunk"
        make up && make install


After adding Ruby to your PATH, you should be ready to run the test suite:

    make test

You can also use `test-all` to run all of the tests with the RUNRUBY
interpreter just built. Use TESTS or RUNRUBYOPT to pass parameters, such as:

    make test-all TESTS=-v

This is also how you can run a specific test from our build dir:

    make test-all TESTS=drb/test_drb.rb

You can run `test` and `test-all` at once by `check` .

    make check

For older versions of Ruby you will need to run the build setup again after
checking out the associated branch in git, for example if you wanted to
checkout 1.9.3:

    git clone git://github.com/ruby/ruby.git --branch ruby_1_9_3

Once you checked out the source code, you can update the local copy by:

    make up

Or, update, build, install and check, by just:

    make love

## Contributing Documentation

If you're interested in contributing documentation directly to CRuby there is
a wealth of information available at
[documenting-ruby.org](http://documenting-ruby.org/).

There is also the [Ruby Reference
Manual](https://bugs.ruby-lang.org/projects/rurema) in Japanese.

## Contributing A Patch

### Deciding what to patch

Before you submit a patch, there are a few things you should know:

*   Pay attention to the maintenance policy for stable and maintained versions
    of Ruby.

*   Released versions in security mode will not merge feature changes.
*   Search for previous discussions on ruby-core to verify the maintenance
    policy

*   Patches must be distributed under Ruby's license.
*   This license may change in the future, you must join the discussion if you
    don't agree to the change


To improve the chance your patch will be accepted please follow these simple
rules:

*   Bug fixes should be committed on trunk first
*   Format of the patch file must be a unified diff (ie: diff -pu, svn diff,
    or git diff)

*   Don't introduce cosmetic changes
*   Follow the original coding style of the code
*   Don't mix different changes in one commit


First thing you should do is check out the code if you haven't already:

    git clone git://github.com/ruby/ruby.git ruby-trunk

Now create a dedicated branch:

    cd ruby-trunk
    git checkout -b my_new_branch

The name of your branch doesn't really matter because it will only exist on
your local computer and won't be part of the official Ruby repository. It will
be used to create patches based on the differences between your branch and
trunk, or edge Ruby.

### Coding style

Here are some general rules to follow when writing Ruby and C code for CRuby:

*   Indent 4 spaces for C with tabs for eight-space indentation (emacs
    default)

*   Indent 2 space tabs for Ruby
*   Do not use TABs in ruby codes
*   ANSI C style for 1.9+ for function declarations
*   Follow C90 (not C99) Standard
*   PascalStyle for class/module names.
*   UNDERSCORE_SEPARATED_UPPER_CASE for other constants.
*   Capitalize words.
*   ABBRs should be all upper case.
*   Do as others do


### ChangeLog

Although not required, if you wish to add a ChangeLog entry for your change
please note:

You can use the following template for the ChangeLog entry on your commit:

    Thu Jan  1 00:00:00 2004  Your Name  <yourmail@example.com>

    	* filename (function): short description of this commit.
    	  This should include your intention of this change.
    	  [bug:#number] [mailinglist:number]

    	* filename2 (function2): additional description for this file/function.

This follows [GNU Coding Standards for Change
Logs](http://www.gnu.org/prep/standards/html_node/Change-Logs.html#Change-Logs
), some other requirements and tips:

*   Timestamps must be in JST (+09:00) in the style as above.
*   Two spaces between the timestamp and your name. Two spaces between your
    name and your mail address.

*   One blank line between the timestamp and the description.
*   Indent the description with TAB. 2nd line should begin with TAB+2SP.
*   Write a entry (*) for each change.
*   Refer to redmine issue or discussion on the mailing list.
*   For GitHub issues, use [GH-#] (such as [Fixes GH-234]
*   One blank line between entries.
*   Do as other committers do.


You can generate the ChangeLog entry by running `make change`

When you're ready to commit, copy your ChangeLog entry into the commit
message, keeping the same formatting and select your files:

    git commit ChangeLog path/to/files

In the likely event that your branch becomes outdated, you will have to update
your working branch:

    git fetch origin
    git rebase remotes/origin/master

Now that you've got some code you want to contribute, let's get set up to
generate a patch. Start by forking the github mirror, check the [github docs
on forking](https://help.github.com/articles/fork-a-repo) if you get stuck
here. You will only need a github account if you intend to host your
repository on github.

Next copy the writable url for your fork and add it as a git remote, replace
"my_username" with your github account name:

    git remote add my_fork git@github.com:my_username/ruby.git
    # Now we can push our branch to our fork
    git push my_fork my_new_branch

In order to generate a patch that you can upload to the bug tracker, we can
use the github interface to review our changes just visit
https://github.com/my_username/ruby/compare/trunk...my_new_branch

Next, you can simply add '.patch' to the end of this URL and it will generate
the patch for you, save the file to your computer and upload it to the bug
tracker. Alternatively you can submit a pull request, but for the best chances
to receive feedback add it is recommended you add it to redmine.

Since git is a distributed system, you are welcome to host your git repository
on any [publicly accessible hosting
site](https://git.wiki.kernel.org/index.php/GitHosting), including [hosting
your
own](https://www.kernel.org/pub/software/scm/git/docs/user-manual.html#public-
repositories) You may use the ['git
format-patch'](http://git-scm.com/docs/git-format-patch) command to generate
patch files to upload to redmine.  You may also use the ['git
request-pull'](http://git-scm.com/docs/git-request-pull) command for
formatting pull request messages to redmine.