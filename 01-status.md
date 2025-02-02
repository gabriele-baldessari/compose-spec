## Status of this document

This document specifies the Compose file format used to define multi-containers applications. Distribution of this document is unlimited.

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](https://tools.ietf.org/html/rfc2119).

### Requirements and optional attributes

The Compose specification includes properties designed to target a local [OCI](https://opencontainers.org/) container runtime,
exposing Linux kernel specific configuration options, but also some Windows container specific properties, as well as cloud platform features related to resource placement on a cluster, replicated application distribution and scalability.

We acknowledge that no Compose implementation is expected to support **all** attributes, and that support for some properties
is Platform dependent and can only be confirmed at runtime. The definition of a versioned schema to control the supported
properties in a Compose file, established by the [docker-compose](https://github.com/docker/compose) tool where the Compose
file format was designed, doesn't offer any guarantee to the end-user attributes will be actually implemented.

The specification defines the expected configuration syntax and behavior, but - until noted - supporting any of those is OPTIONAL.

A Compose implementation to parse a Compose file using unsupported attributes SHOULD warn user. We recommend implementors
to support those running modes:

* default: warn user about unsupported attributes, but ignore them
* strict: warn user about unsupported attributes and reject the compose file
* loose: ignore unsupported attributes AND unknown attributes (that were not defined by the spec by the time implementation was created)

