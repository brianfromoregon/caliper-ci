# Release 2 Features #

This release continues support for memory regression testing, so refer to the DemoRelease1 example to understand how that works.

Starting in 2.2, your Caliper results can be uploaded to a running Caliper Cloud instance such as http://microbenchmarks.appspot.com. See the job configure page.

In addition, I've added to the build results page:
  * A time column to the results table.
  * [Trending graphs](http://code.google.com/p/caliper-ci/issues/detail?id=6) for timing results
  * The build's environment properties

Of note, timing results cannot yet [fail the build](http://code.google.com/p/caliper-ci/issues/detail?id=5).

The new results page remains ugly, but it's richer:

![http://caliper-ci.googlecode.com/svn/docs/release2/ss.png](http://caliper-ci.googlecode.com/svn/docs/release2/ss.png)