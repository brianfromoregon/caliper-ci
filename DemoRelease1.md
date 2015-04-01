# Demo of Release 1 Features #

In this demo I'm playing the role of diligent `java.util.concurrent.ConcurrentHashMap` maintainer with some _serious_ improvements to make :)

You'll see how I use Jenkins to discover and report on performance regressions associated with my changes.

# The Benchmark #
This is my Caliper benchmark to measure the cost of Map initialization, comparing mine to HashMap.


![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/code.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/code.png)


# Jenkins! #

I'm adding a new Jenkins job to run this benchmark and collect the results. First I add a build step to run the benchmark and produce a results file, and then I check the "Publish Caliper microbenchmark results" box to have the plugin find it.



---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/config.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/config.png)


# And then... #

Build #1 succeeds, and is now my baseline.



---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/1a.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/1a.png)

---


Clicking to see detail...


---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/1b.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/1b.png)

---


All is well so far. Now I'm going to check in my super awesome change to CHM.



---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/2a.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/2a.png)

---


Oops, broke the build. Let's see the details.


---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/2b.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/2b.png)

---


I see that I've improved on the number of allocations but I've regressed on the amount of memory being allocated. Time to revert...


---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/3a.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/3a.png)

---


Another failure, why? Jenkins saw that in this build I've regressed on the number of allocations and isn't smart enough to know I'm simply trying to undo. See...


---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/3b.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/3b.png)

---


However when the next build runs there will be no change and this test will pass.


---

![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/4a.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/4a.png)
![http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/4b.png](http://caliper-ci.googlecode.com/svn/docs/release1.0-demo/4b.png)

---



# Fired #

Bad news, my boss is on the mailgroup which Jenkins has been sending the failure notes to and I've just been fired from my position as `java.util.concurrent.ConcurrentHashMap` maintainer on the grounds of "careless checkins" :(