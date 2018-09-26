
---
title: From Java 8 to Java 11
date: 2018-09-26  12:38:11
tags: Java
---
  
![1_HQ](https://i.loli.net/2018/09/26/5bab0e7fbd0fa.jpeg)


Moving from Java 8 to Java 11 is trickier than most upgrades. Here are a few of my notes on the process.

(And here are a couple of other blogs - Benjamin Winterberg and Leonardo Zanivan.)

Modules
Java 9 introduced one of the largest changes in the history of Java - modules. Much has been said on the topic, by me and others. A key point is sometimes forgotten however:

You do not have to modularise your code to upgrade to Java 11.

In most cases, code running on the classpath will continue to run on Java 9 and later where modules are completely ignored. This is terrible for library authors, but great for application developers.

So my advice is to ignore modules as much as you can when upgrading to Java 11. Turning your application into Java modules may be a useful thing to consider in a few years time when open source dependencies really start to adopt modules. Right now, attempting to modularise is just painful as few dependencies are modules.

(The main reason I've found to modularise your application is to be able to use jlink to shrink the size of the JDK. But in my opinion, you don't need to fully modularise to do this - just create a single jar-with-dependencies with a simple no-requires no-exports module-info.)

Deleted parts of the JDK
Some parts of the JDK have been removed. These were parts of Java EE and Corba that no longer fitted well with the JDK, or could be maintained elsewhere.

If you use Corba then there is little anyone can do to help you. However, if you use the Java EE modules then the fix for the deleted code should be simple in most cases. Just add the appropriate Maven jars.

On the Java client side, things are more tricky with the removal of Java WebStart. Consider using Getdown or Update4J instead.

Unsafe and friends
Sun and Oracle have been telling developers for years not to use sun.misc.Unsafe and other sharp-edge JDK APIs. For a long time, Java 9 was to be the release where those classes disappeared. But this never actually happened.

What you might get with Java 11 however is a warning. This warning will only be printed once, on first access to the restricted API. It is a useful reminder that your code, or a dependency, is doing something "naughty" and will need to be fixed at some point.

What you will also find is that Java 11 has a number of new APIs specifically designed to avoid the need to use Unsafe and friends. Make it a priority to investigate those new APIs if you are using an "illegal" API. For example, Base64, MethodHandles.privateLookupIn, MethodHandles.Lookup.defineClass, StackWalker and Variable Handles.

Tooling and Libraries
Modules and the new six-monthly release cycle have conspired to have a real impact on the tooling and libraries developers use. Some projects have been able to keep up. Some have struggled. Some have failed.

When upgrading to Java 11, a key task is to update all your dependencies to the latest version. If there hasn't been a release in since Java 9 came out, then that dependency may need extra care or testing. Make sure you've updated your IDE too.

But it is not just application dependencies that need updating, so does Maven (and Gradle too, but I don't know much about Gradle myself). Most Maven plugins have changed major versions to a v3.x, and upgrading Maven itself to v3.5.4 is also beneficial.

Sadly, the core maven team is very small, so there are still some bugs/issues to be solved. However, if your Maven build is sensible and simple enough, you should generally be OK. But do note that upgrading a plugin from a v2.x to a v3.x may involve changes to configuration beyond that just associated with modules. For example, the Maven Javadoc plugin has renamed the argLine property.

A key point to note is the way Maven operates with modules. When the Maven compiler or surefire plugin finds a jar file that is modular (ie. with a module-info.class) it can place that jar on the modulepath instead of the classpath. As such, even though you might intend to run the application fully on the classpath, Maven might compile and test the code partly on the classpath and partly on the modulepath. At present, there is nothing that can be done about this.

Sometimes your build will need some larger changes. For example, you will need to change Findbugs to SpotBugs. And change Cobertura to JaCoCo.

These build changes may take some time - they did for me. But the information available by a simple web search is increasing all the time.

Summary
I've upgraded a number of Joda/ThreeTen projects to support Java 9 or later now. It was very painful. But that is because as a library author I have to produce a jar file with module-info that builds and runs on Java 8, 9, 10 and 11. (In fact some of my jar files run on Java 6 and 7 too!)

Having done these migrations, my conclusion is that the pain is primarily in maintaining compatibility with Java 8. Moving an application to Java 11 should be simpler, because there is no need to stay tied to Java 8.

Comments welcome, but note that most "how to" questions should be on Stack Overflow, not here!
