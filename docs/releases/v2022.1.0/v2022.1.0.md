---
title: 2022.1.0
parent: Releases
nav_order: 2022010
---

# AW-SDX 2022.1.0

**Release Date:** 06/23/2022  
**Platform Tag:** 1.0.0  

## Major Changes

This first release is considered an MVP (Minimum Viable Product) of the AW-SDX Controller software suite. It consists of the basic implementation and integration of the major components: topology management, data messaging middleware, REST API service, and optimal path computation in a multi-domain exchange network environment. It forms the system core for the L2 and L3 network services and TE (Traffic Engineering) optimization for the next release.

## Packages and Components

### SDX Controller
- A REST API server that exposes endpoints for user applications to query the OXP topology information and post service requests.
- The backend function for interdomain network topology management that includes topology assembly, validation, and updates from different domains via the SDX local controllers.
- The backend function for constrained shortest path computation and breakdowns (to different domains).
- Client subscription to the Pub-Sub server.
- A database backend.

**Repository tag:** `sdx-controller` → `v1.0.1`

### SDX Local Controller
- A REST API server that exposes various endpoints for domain provisioning systems to publish topology models and updates.
- Interaction with the SDX-Controller via the Pub-Sub message queue middleware for topology and connection breakdown messages.
- Client subscription to the Pub-Sub server.

**Repository tag:** `sdx-lc` → `v1.0.1`

### Data Model
- A set of schemes that define the topology and components description as well as requests.
- A suite of software for topology management: parsing, assembly, validation, and conversion to other formats including GRENML and Networks.
- Data model exchange functions between the SDX-Controller and SDX-LC.
- Interfaces to the optimization solver function in the CE (Computation Element) module.

**Repository tag:** `datamodel` → `v1.0.1`

### Path Computation Element
- Optimal solver implementation (based on the Google OR-Solver) for constrained shortest path.
- TE optimization under two different objectives: cost minimization and load balancing.

**Repository tag:** `pce` → `v1.0.1`

### Kytos Topology Interface
- kytos-sdx-topology napp: interface listening to topology changes in Kytos and pushing version/timestamp changes to SDX Local Controller.

**Repository tag:** `kytos-sdx` → `v1.0.1`

## Future Enhancements

### Data Model
- Extension to L2VPN services
- Extension to L3VPN services
- Extension to Measurement and BAPM support

### Computation Element
- An efficient heuristic for large-scale TE requests
- L2VPN protection

### Pub-Sub Message Queue
- Measurement
- BAPM support

### CI/CD subsystem
- Enhance exception handling, logging, and overall code quality
- Establish the testing and review pipeline
- Further streamline deployment in a distributed environment

