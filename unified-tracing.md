# The Unified Tracing Platform - Steven Rostedt, VMware Inc

Many faces of tracing: Frtace, Perf, ...

## ftrace

logdev - 1998

* One of the parents of ftrace
* Created during masters thesis
* Highly portable

latency tracer (preempt-realtime patch) - 2004

* From Nadia Yvette Chambers and Ingo Molnar
* Included tracing of functions via mcount
* Function tracing had to be comipled in
* Included the preemption and interrupt disabled latency tracking
* Very basic ring buffer (all events were the same size)

Merged into ftrace in 2008

## Perf - 2009

* Started as profiler
* Added to Linux
* Created own ring buffer
* Hooked into the ftrace infrastructure

## Linux Trace Toolkit - 2000

## LTTng - Linux Trace Toolkit Next Generation - 2006

* Complete rewrite of LTT
* Implemented the original tracepoints

## DTrace - Solaris 10 - 2005

* First to allow scripting in the kernel (custom traces)
* Now owned by Oracle
* Oracle portad to Linux
* Didn't make it to mainline

## SystemTap - 2009

* Red Hat's answer to Dtrace
* Didn't make it to mainline

## BPF (Berkley Packet Filter)

* JIT compiled for x86 in 2011
* Extremely fast customized network packet filtering

## eBPF (Extended BPF)

* Introduced by Alexei Starovoitov - 2014
* Both SystemTap and Dtrace are being ported on-top of eBPF

## Where are we today?

## Can't we have just one tracer?

* Isn't too much choice a problem?
* Wasting effort on multiple approaches
  ** Splitting skill set?
  ** But diversity brings innovation!
* Nothing is one size fits all
* Bulk diversity killed Unix: Too many flavors
* They were proprietary: Could not share features
* Diversity is the strength of OSS

## Commonality

* Trace point: Used by all
* Kprobes: Used by all
* Uprobes: ...

## Progress!

### Babeltrace

* From LTTng
* Parses the Common Trace Format (CTF)
* Goal is to allow any utility to read any tracing data format
* Works with both perf and ftrace
* Works with kprobe and uprobe events

### libtraceevent

* From ftrace
* Parses the trace event format files
* Tells US apps how kernel writes trace events


### libperf

* Wraps `perf_event_open()` system call
  ** Like a large `ioctl()`

## Coming soon

* libftrace
* libtracecmd
* libkshark

## The unified tracing platform

Library abstraction in user space to abstract tracers

## Conclusion

* Tools are not competing with each other
* Each has strengths and weaknesses
* All are open source
* All can utilize each others work
* This is what makes Linux the best OS in the world.


