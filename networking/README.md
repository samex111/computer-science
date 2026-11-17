# Computer Networking

## What problem does networking solve?

An application often needs data or services on another machine. Networking defines how independent devices address one another, move data, establish communication, and deal with delay, loss, and connection failure.

## Why was it created?

Standalone computers could not share information or resources at scale. Networks and layered protocols made communication possible across different hardware and operating systems, while allowing each layer to solve a manageable part of the problem.

## How to study networking

Trace one request from an application to a remote service and back. Identify the layers involved, the data each layer adds, the addressing used, and where latency or failure can occur.

## Topics

- [HTTP and HTTPS](./http/)
- DNS and name resolution
- TCP and UDP
- IP addressing and routing
- TLS and certificates
- Sockets, ports, proxies, and load balancers
- Latency, throughput, packet loss, and congestion

**First lab:** use browser DevTools and tools such as `curl`, `ping`, `traceroute` / `tracert`, and `nslookup`. Observe rather than merely memorize.