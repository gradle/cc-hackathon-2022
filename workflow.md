# Suggested Workflow

> This document gives an overview of the suggested workflow for participating in the Configuration Cache Hackathon.
>
> For common questions and answers, see the [FAQ](faq.md).
>
> This document may be updated any time during the event.

## Become familiar with the Configuration Cache feature

See [Configuration Cache](https://docs.gradle.org/nightly/userguide/configuration_cache.html#config_cache) in the Gradle Docs.

It is important that you understand its benefits, but also the requirements and constraints it imposes on the programming model of Gradle builds.

## Become familiar with the Gradle contribution guide

The guide is available [here](https://github.com/gradle/gradle/blob/master/CONTRIBUTING.md). More specifically, pay attention to these sections:
* [Follow the Code of Conduct](https://github.com/gradle/gradle/blob/master/CONTRIBUTING.md#follow-the-code-of-conduct)
* [Setting up your development environment](https://github.com/gradle/gradle/blob/master/CONTRIBUTING.md#setting-up-your-development-environment)
* [Creating commits and writing commit messages](https://github.com/gradle/gradle/blob/master/CONTRIBUTING.md#creating-commits-and-writing-commit-messages)
* [Submitting Your Change](https://github.com/gradle/gradle/blob/master/CONTRIBUTING.md#submitting-your-change)
* [Fixing DCO failures/Signing Off Commits After Submitting a Pull Request](https://github.com/gradle/gradle/blob/master/CONTRIBUTING.md#fixing-dco-failuressigning-off-commits-after-submitting-a-pull-request)

## Review unclaimed issues and find one you would like to fix

Issues that are available to be picked up will be under the "Unclaimed Issues" column of the [Hackathon board](https://github.com/orgs/gradle/projects/43/). Find an issue you would like to fix, then claim it by commenting on the Github issue letting the organization team know you want to work on it. Claimed issues will be granted on a first-come-first-serve basis. The organization team will then assign the GitHub issue to you and move it from the "Unclaimed Issues" to the "Claimed Issues" column on the Hackathon board.

## Reproduce the test failure on your local environment

### Fork the Gradle repository on Github.

The repo is at https://github.com/gradle/gradle. Forking the master branch only is sufficient.

### Run the documentation test suite locally

Every issue includes the `./gradlew ...` command to reproduce the failures locally under a section titled "How to reproduce".  

Once you execute the suggested command locally, you should see the same problems that are described on the issue. 

### Find the configuration cache report in the test result report

See [FAQ](faq.md#where-do-i-find-the-configuration-cache-report).

### Review the configuration cache report

Read the configuration cache report to understand the issue causing it to fail (it should match what is described on the issue under a section titled "Test failure details").
 
## Investigate how to fix the issue

The configuration report will often refer you to the section of the documentation that covers the issue(s) with the snippet you are trying to fix. The documentation may include a recommended solution for most common issues. Also, the [FAQ](faq.md) lists common problems and corresponding typical fixes.

### Read the example fixes to get some inspiration

We have some example PRs fixing common cases in some of the snippets. 

* avoid using `Project` to perform file system operations during execution ([link](https://github.com/gradle/gradle/pull/21555/files#r948986470))
* avoid accessing the `configurations` object during execution ([link](https://github.com/gradle/gradle/pull/21555/files#r948983984))

## Write the solution and validate it locally

### Re-run the tests

If your fix is good, if you re-issue the `./gradlew ...` command again, the tests should now be passing.

Running a build in the snippet project (with `--configuration-cache`) twice should confirm things work both while storing the cache entry (first run) and loading the existing cache entry (second run).

## Create a PR with your solution

Create a draft PR with your fix, ideally annotating it with any comments that may help reviewers understand the reason behind your changes (in most cases, a link to the corresponding problem pattern on the [FAQ](faq.md) would be enough).

Also, don't forget to remove the tests you fixed from the list of known broken tests (see [`testsToBeFixedForConfigurationCache`](https://github.com/gradle/gradle/blob/8dc15820bb8471dac12555738ca31d238314b451/subprojects/docs/build.gradle#L753) in the docs build.gradle file).

For bonus points, consider generating the [documentation locally](faq.md#how-to-build-the-docs-locally-so-i-can-find-and-fix-consistency-issues-with-the-prose) and reviewing (and adjusting) the prose that surrounds the snippets you changed to ensure they remain consistent with your changes.

##  Mark your submission as ready

Show your submission is ready for review by marking your PR as ready for review.

## Get help on the Slack channel

At any time, don't hesitate to reach out to the [Hackathon channel](https://app.slack.com/client/TA7ULVA9K/C013WEPGQF9) if you have questions (technical or about the rules). The Gradle Build Tool team and fellow Hackathon participants should be able to get you unstuck!
