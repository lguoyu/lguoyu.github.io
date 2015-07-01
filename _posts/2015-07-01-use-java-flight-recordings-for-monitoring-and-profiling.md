---
layout: post
title: Use Java Flight Recordings for Monitoring and Profiling
categories: [java]
tags: []
published: True

---

There are so many articles online saying that JMC adds little performance overhead when doing monitoring (less than 1%) and profiling (less than 2%), so I decided to try it out since we are facing a performance issue and I think maybe JMC can help us out. I have to say the documentation of JMC is not good, it took me a little bit time to get my first profiling recording. Note that I mainly focus on JFR instead of JMX console here.

<!--more-->

Recording
===

Record Locally
---

It's pretty easy to start the flight recording locally by appending `-XX:+UnlockCommercialFeatures -XX:+FlightRecorder` to the command line when starting the application, and you can navigate to the process after JMC GUI is lauched.

Record Remotely
---

The controlling of the remote recording is done by JMX, so beyond the JVM options specified above, we also need to open the JMX of the Java application by adding

		-Dcom.sun.management.jmxremote 
		-Dcom.sun.management.jmxremote.port=8899 
		-Dcom.sun.management.jmxremote.ssl=false 
		-Dcom.sun.management.jmxremote.authenticate=false



