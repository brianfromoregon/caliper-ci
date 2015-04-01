[Caliper microbenchmark](http://code.google.com/p/caliper) results integrated into your CI builds. Get it through the [Jenkins update center](http://updates.jenkins-ci.org/update-center.json) or grab it from [their Maven repo](http://maven.jenkins-ci.org/content/repositories/releases/com/brianfromoregon/caliper-ci/).

## Live demo! ##
[This Jenkins job](https://brianfromoregon.ci.cloudbees.com/job/caliper-examples-mini/lastSuccessfulBuild/caliper) builds Caliper from source each week, runs/tracks [this BitSetBenchmark](http://code.google.com/p/caliper/source/browse/examples/src/main/java/examples/BitSetBenchmark.java) and uploads the results to [Caliper Cloud](http://microbenchmarks.appspot.com/run/brianfromoregon@gmail.com/examples.BitSetBenchmark).

## Static demo ##

See the [Release2](Release2.md) page.

![http://caliper-ci.googlecode.com/svn/docs/release2/build-page.png](http://caliper-ci.googlecode.com/svn/docs/release2/build-page.png)



## Changelog ##

  * 2.3 (2012.11.09) [[announcement](https://plus.google.com/u/0/107444811490059715698/posts/BVVFSz2DNMr)]
    * Removed Java7 dependency because Cloudbees cannot install plugins requiring Java7 in their instances, and changing that is not on their roadmap.
    * Source repository moved from google code to [github](https://github.com/jenkinsci/caliper-ci-plugin)
  * 2.2 (2012.03.31) [[announcement](https://plus.google.com/107444811490059715698/posts/as299VaBzt1)]
    * Fix for bug that made it difficult to use non-default result file search pattern.
    * Can upload results to a Caliper Cloud instance.
    * Now requires Java7 JVM. My mistake, this should not have been changed in a "minor" release.
  * 2.1 (2012.02.06) Tiny bug fix in display code. First release to Jenkins update center.
  * 2.0 (2012.01.19) Trend graphs and stats for timing results [[announcement](https://plus.google.com/107444811490059715698/posts/XpU8umGHimu)]
  * 1.0 (2011.10.28) Memory benchmark regression support [[announcement](https://plus.google.com/107444811490059715698/posts/An63ntPXAxD)]

## Thanks! ##
[![](http://www.cloudbees.com/sites/default/files/Button-Built-on-CB-1.png)](https://brianfromoregon.ci.cloudbees.com/job/caliper-ci/)

Cloudbees is hosting the Jenkins instance that runs CI for this plugin and serves the live demo.

