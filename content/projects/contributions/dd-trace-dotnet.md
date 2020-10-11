---
title: "Datadog .NET Tracer"
link: "https://github.com/datadog/dd-trace-dotnet"
image: "/images/dd_logo_h_rgb.png"
description: "Automatically instruments .NET applications to capture and send traces to Datadog."
featured: true
tags: [".NET","Datadog","APM","OpenTelemetry","OpenTracing"]
weight: 100
sitemap: 
    priority : 0.8
---

### Project
The Datadog .NET Tracer is the Datadog-provided APM solution for .NET applications. APM solutions generate traces to represent business transactions and they contain multiple spans which each represent one logical segment of execution, which may be an outbound HTTP request or a database transaction.

The Datadog .NET Tracer provides automatic instrumentation that will automatically generate traces for a number of popular .NET libraries so that users can get immediate value without changing the application code. Developers may also use the Datadog.Trace library to create additional instrumentation or add supplemental instrumentation to their traces.

The project consists of two main components:
1. A Datadog.Trace .NET library that provides the API for generating traces, adding information to traces, and flushing them to Datadog
2. A CLR Profiler that provides the automatic instrumentation feature. The profiler gets initialized by the .NET runtime at program start, registers for JIT compilation events to monitor what method calls are being made, and, when a supported integration is called, performs IL modification to generate spans with the appropriate information upon entering and finish the span upon exiting.

### Contributions
I've been one of the main contributors since May 2019. Significant contributions to the library include:
- Implementing automatic injection of trace ID's into application logs
- Inserting a startup hook (using IL modification by the CLR Profiler) to launch a safety probe and (if safe) initialize automatic instrumentation
- Diagnosing and fixing critical IL modification bugs to provide safer automatic instrumentation
- Removing third-party assembly dependencies from the Datadog.Trace library to provide safer automatic instrumentation when running on the .NET Framework
