# An Ftrace Primer - Steven Rostedt, VMware

`/sys/kernel/debug`: find the tracing directory there

Also mountable directly

```
mount -t tracefs nodev /sys/kernel/tracing
```

## README

`/sys/kernel/tracing/README`

Changes based on what is compiled in

## Tracers

* nop
* function
* function_graph
* blk
* mmiotrace - trace interactions between drivers and h/w (man-in-the-middle attack between driver and h/w)

## Other tracers

* hwlat - Hardware latencies (I.e. SMI)
* wakeup_dl,rt - Records max wakeup latency (dead-line,real-time)

Does not support live-patching (overhead)

* irqsoff - Records max IRQ latency
* preemptoff - Max preemption disabled latency
* preemptirqsoff - Max preemption / IRQ disabled latency

## current_tracer

```
echo function > /sys/kernel/tracing/current_tracer
echo 0 >/sys/kernel/tracing/tracing_on
cat /sys/kernel/tracing/trace
```

## tracing_on (Caution)

0 = Disable
1 = Enable
Remember space before >

## trace_marker

In C code:

1. Open the trace_marker
1. Write when ready

## Function tracing

* `available_filter_functions` - Functions
* `set_ftrace_filter` - Only captured functions (space delimetered)
* `set_ftrace_notrace` - Removed after above

Minor wildcards supported

```
echo '*lock*' > set_ftrace_filter 
echo '*clock*' > set_ftrace_notrace 
echo function > current_tracer 
echo 1 > tracing_on 
echo 0 > tracing_on 
cat trace
```

## Function graph tracer

```
echo function_graph > current_tracer
```

Don't trust all the times
Adds overhead
Single entity gives accurate time

## Tracing events

Function tracing is great, BUT!

* Doesn't show much data besides functions being called
* No params / vars

Trace Events

* Points in kernel that write into trace buffer
* Record specific data within kernel
* More detailed insights

Grouped by system

```
echo nop > current_tracer 
echo 1 > events/sched/sched_waking/enable 
echo 1 > events/sched/sched_switch/enable 
echo 1 > tracing_on 
echo 1 > tracing_off
more trace
```

Enable all events: use `enable` file in directory

## Filtering events

Too much info!

* Just as bad as not enough

```
echo 'prev_comm == "bash" && prev_state & 0x02' > events/sched/sched_switch/filter 
echo 1 > events/sched/sched_switch/enable 
echo >trace
more trace
```

## Event triggers

* Turn off tracing
* Turn on tracing
* ...

```
echo 'prev_comm == "bash" && prev_state & 0x02' > events/sched/sched_switch/filter 
echo 'stacktrace if prev_comm == "bash" && prev_state & 0x02' > events/sched/sched_switch/trigger 
echo 1 > events/sched/sched_switch/enable 
echo > trace
cat trace
```

Triggers are more difficult to remove

```
echo '!stacktrace' > events/sched/sched_switch/trigger
```

## ftrace - a tool for everyone with BusyBox

So far only `echo` and `cat`

Can be tedios

## trace-cmd

* Executable that interacts with ftrace interfaces
* No need to worry about tracefs
* Can also save the data to a file (using zero-copy with `splice`)
* Uses format files to know how to read the binary data

Forget everything you learned so far

Be in a directory you can write to

```
trace-cmd start -e sched_switch -f 'prev_comm == "bash" && prev_state == 0x02' -R 'stacktrace if prev_comm == "bash" && prev_state & 0x02'
trace-cmd show
```

**AP**: trace-cmd.org: bugzilla: suggest inclusion in busybox

## trace-cmd stat and reset

See what is configured / set

```
tracecmd stat
```

Reset

```
tracecmd reset
```

New command reset and disable

```
trace-cmd start -p nop
```

## Introduction to strace

```
strace ./hello &> out
more out
```

## Lets have a look at execve

```
trace-cmd record -p function_graph -g '*sys_exec*' ./hello
```

Get report (lot's of data)

```
trace-cmd report
```

Exclude interrupts

```
trace-cmd report -I
```

Also exclude softirqs

```
trace-cmd report -IS
```

Only trace a few functions down

```
trace-cmd record -p function_graph -g '*sys_exec*' --max-graph-depth 5 ./hello
```

Trim down some more

```
trace-cmd record -p function_graph -g '*sys_exec*' --max-graph-depth 5 -n _cond_resched ./hello
trace-cmd report -IS
```

Useful stuff

```
trace-cmd report -O tailprint
```

## I want to know what my PC is doing

Let's see the world!

Dump all... KernelShark 1.0

KernelShark created in 2009

* GTK version
* Stalled in development
* Slow on large datasets

Re-written as 2.0, based on Qt


