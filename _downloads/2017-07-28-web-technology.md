---
layout: download
title: Web Technology
subtitle: Class materials and downloads homepage of Web Technology. This page serves the files provided by lecturer RSH and those our contributors find to be helpful to everyone of us.
lastupdate: 2017-07-30 12:00:00
tutor: RSH
comments: true
---

**PS** *Example, yet to be updated...*

**Robust Distributed System Nucleus (rDSN)** is a framework for quickly building robust distributed systems. It has a microkernel for pluggable components, including applications, distributed frameworks, devops tools, and local runtime/resource providers, enabling their independent development and seamless integration. The project was originally developed for Microsoft Bing, and now has been adopted in production both inside and outside Microsoft.

* [PPT][rDSN Full Introduction](https://github.com/imzhenyu/rDSN/raw/master/resources/rDSN.full.2016.10.pdf)
* [What are the existing modules I can immediately use?](#existing)
* [What scenaios are enabled by combining these modules differently?](#scenarios)
* [How does rDSN build robustness?](#novel)
* [Related papers](#papers)
* [[Case](https://github.com/imzhenyu/rocksdb)] RocksDB made replicated using rDSN!
* [[Tutorial](https://github.com/Microsoft/rDSN/wiki/Tutorial:-one-box-cluster)] A one-box cluster demo to understand how rDSN helps service registration, deployment, monitoring etc..
* [[Tutorial](https://github.com/Microsoft/rDSN/wiki/Tutorial:-Build-A-Single-Node-Counter-Service)] Build a counter service with built-in tools (e.g., codegen, auto-test, fault injection, bug replay, tracing)
* [[Tutorial](https://github.com/Microsoft/rDSN/wiki/Tutorial:-Build-A-Scalable-and-Reliable-Counter-Service)] Build a scalable and reliable counter service with built-in replication support
* [API Reference](http://imzhenyu.github.io/rDSN/documents/v1/html/index.html)
* [Installation](https://github.com/Microsoft/rDSN/wiki/Installation)


### <a name="existing">Existing pluggable modules (and growing) </a>

The core of rDSN is a service kernel with which we can develop (via [Service API](http://imzhenyu.github.io/rDSN/documents/v1/html/group__service-api.html) and [Tool API](http://imzhenyu.github.io/rDSN/documents/v1/html/group__tool-api.html)) and plugin lots of different application, framework, tool, and local runtime modules, so that they can seamlessly benefit each other. Here is an incomplete list of the pluggable modules.

| Pluggable modules | Description | Release |
|--------|-------------|------|
| [dsn.core](https://github.com/Microsoft/rDSN/tree/master/src/core) | rDSN service kernel | [1.0.0](https://github.com/Microsoft/rDSN/releases/tag/v1.0.0) |
| [dsn.dist.service.stateless](https://github.com/imzhenyu/rDSN.dist.service/tree/master/src/app_daemon)      | scale-out and fail-over for stateless services (e.g., micro services) | [1.0.0](https://github.com/imzhenyu/rDSN.dist.service/releases/tag/v1.0.0) |
| [dsn.dist.service.stateful.type1](https://github.com/imzhenyu/rDSN.dist.service/tree/master/src/replica_server) | scale-out, replicate, and fail-over for stateful services (e.g., storage) | [1.0.0](https://github.com/imzhenyu/rDSN.dist.service/releases/tag/v1.0.0) |
| [dsn.dist.service.meta_server](https://github.com/imzhenyu/rDSN.dist.service/tree/master/src/meta_server)    | membership, load balance, and machine pool management for the above service frameworks | [1.0.0](https://github.com/imzhenyu/rDSN.dist.service/releases/tag/v1.0.0) |
| [dsn.dist.uri.resolver](https://github.com/Microsoft/rDSN/tree/master/src/plugins/dist.uri.resolver)           | a client-side helper module that resolves service URL to target machine | [1.0.0](https://github.com/Microsoft/rDSN/releases/tag/v1.0.0) |
| [dsn.dist.traffic.router](https://github.com/imzhenyu/rDSN.dist.traffic.router)         | fine-grain RPC request routing/splitting/forking to multiple services (e.g., A/B test) | todo |
| [dsn.tools.common](https://github.com/Microsoft/rDSN/tree/master/src/plugins/tools.common)                | deployment runtime (e.g., network, aio, lock, timer, perf counters, loggers) for both Windows and Linux; simple toollets, such as tracer, profiler, and fault-injector | [1.0.0](https://github.com/Microsoft/rDSN/releases/tag/v1.0.0) |
| [dsn.tools.nfs](https://github.com/Microsoft/rDSN/tree/master/src/plugins/tools.nfs)                   | an implementation of remote file copy based on rpc and aio | [1.0.0](https://github.com/Microsoft/rDSN/releases/tag/v1.0.0) |
| [dsn.tools.emulator](https://github.com/Microsoft/rDSN/tree/master/src/plugins/tools.emulator)              | an emulation runtime for whole distributed system emulation with auto-test, replay, global state checking, etc. | [1.0.0](https://github.com/Microsoft/rDSN/releases/tag/v1.0.0) |
| [dsn.tools.hpc](https://github.com/imzhenyu/rDSN.tools.hpc)                   | high performance counterparts for the modules as implemented in tools.common | todo |
| [dsn.tools.explorer](https://github.com/imzhenyu/rDSN.tools.explorer)              | extracts task-level dependencies automatically | [1.0.0](https://github.com/imzhenyu/rDSN.tools.explorer/releases/tag/v1.0.0) |
| [dsn.tools.log.monitor](https://github.com/imzhenyu/rDSN.tools.log.monitor)           | collect critical logs (e.g., log-level >= WARNING) in cluster | [1.0.0](https://github.com/imzhenyu/rDSN.tools.log.monitor/releases/tag/v1.0.0) |
| [dsn.app.simple_kv](https://github.com/Microsoft/rDSN/tree/master/src/plugins/apps.skv)                    | an example application module | [1.0.0](https://github.com/Microsoft/rDSN/releases/tag/v1.0.0) |
