---
title: "Overview"
description: ""
lead: ""
date: 2022-11-10T11:35:35+08:00
lastmod: 2022-11-10T11:35:35+08:00
draft: false
images: []
menu:
  docs:
    parent: "reference"
    identifier: "overview-c19c59c7c6d3034de5db0437110210d8"
weight: 015
toc: true
---

[Kindling-java](https://github.com/CloudDectective-Harmonycloud/kindling-java) is an attach agent to collect Java `CPU` / `LOCK` for probe which relies on [async-profiler](https://github.com/CloudDectective-Harmonycloud/async-profiler). Besides it also collect `traceid` generated by SkyWalking agent.

# Features
* [Event] Collect datas by events specified by event argument[`cpu` / `lock` / `traceid`].
* [Plugins] Enhance SkyWalking Agent and print traceId into `/dev/null`.

# How it works
* Jattach copy the `agent jar` and `libasyncprofiler.so` into container.
* Jattach attach agent into application.
* Agent start asyncProfiler by call asyncProfielr API.
    * Load libasyncprofiler.so
    * Execute star``t/stop command
    * Execute print to collect CPU data at fixed rate
* Agent enhance Skywalking agent by asm and print traceid into /dev/null.
    * `Begin / End` life cycle of the `trace`
    * When trace is dispatched into another thread, `begin / end` life cycle of the `runnable execution`.