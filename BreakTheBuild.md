## Yikes! ##

People may get uncomfortable talking about performance regression tests failing their builds. Legitimate regressions in performance are difficult to detect, finding them usually involves statistics and thresholds and fuzzy rules. And many times a regression is not a mistake: yes it's a bit slower but now my app can run on a phone! So why would we want our tooling to break a build based on false-positive performance regressions as is being discussed in [Issue 5](http://code.google.com/p/caliper-ci/issues/detail?id=5)?

## Which build? ##

In my projects I don't usually have just one build, I have some tree of dependent build steps. Compilation and static analysis and unit tests come first, then integration tests and perf tests run asynchronously. The upstream builds are annotated and/or promoted with the success of a downstream job via the [Promoted Builds plugin](https://wiki.jenkins-ci.org/display/JENKINS/Promoted+Builds+Plugin), perhaps.

If my perf test build were to fail, I'll get an email (with appropriate verbiage courtesy [email-ext](https://wiki.jenkins-ci.org/display/JENKINS/Email-ext+plugin)) and will click the Jenkins link to investigate. But that's about all. Just like integration tests which can fail from transient errors caused by problematic external resources, perf tests do not necessarily prevent my build from being sent further down the pipe. The consumer and/or gatekeeper of the builds will be very interested to see that there **were** failures in these async jobs, and they'll use their judgement to decide whether or not the build should be blessed.

## Terminology ##

"Breaking the build" is often associated with lava lamps and public shaming (though as an aside there is a better model, your tools should have the ability to only submit your changes to trunk if it passes basic build steps first, and notify **only** you if it doesn't).

I happen to run my perf tests as Jenkins jobs, specific runs of which are called "builds", and marking a run as unstable/failed is a convenient and fitting approach because it lets me use features from loads of other plugins that also speak this language. These builds are not really builds, nothing is built, they should not be hooked to lava lamps.