# Projects GSoC 2016

To understand the different areas of this project please take a look at the [roadmap](https://github.com/Greennav/greennav.github.io/blob/master/wiki/Roadmap.md).

## Front end projects

### Refactoring and GUI design

The current webapp consists of different polymer elements. Before working on the integration of new features, it is necessary to rethink the current architecture, redesign the UI and refactor the codebase. Furthermore, documentation, logging and user notifications should be implemented in this GSoC project. A new logo would be nice, too.

- **Difficulty**: Easy
- **Skills**: Polymer, GUI design
- **Mentor**: Fabian Bormann

### Integration of new features

For the webapp, we would like to integrate information regarding weather, traffic, terrain height etc. Since the backend isn't implemented yet, you will create a proof of concept and an interface with the webapp and the back end. This requires communication with your mentor, so those features can be integrated easily upon completion of the GSoC.

- **Difficulty**: Easy
- **Skills**: Polymer, GUI design
- **Mentor**: Fabian Bormann

### Visualization tool

This project aims to create a single web application with polymer to compare different routing algorithms. It gets the information from either a backend, the prototyping tool or both. The steps of each algorithm are shown on a map component, together with statistics and other performance characteristics. Results should be analyzed (eg. via R) and exportable to enable developers to measure their algorithms, compare them and create useful graphics for their papers.

![Dijkstra's Algorithm](http://www.isp.uni-luebeck.de/~schoenfr/greennav/dijkstra.gif)
![A* Algorithm](http://www.isp.uni-luebeck.de/~schoenfr/greennav/astar.gif)

- **Difficulty**: Hard
- **Skills**: Polymer, R, statistics, routing algorithms
- **Mentor**: Max Lorenz

### Prototyping tool

The prototyping tool allows developers to design and test new routing algorithms leveraging the GreenNav framework with all data sources (temperature, terrain height etc) easily. A simple MVP in polymer exists, which can be used as a starting point. Since the tool should be language agnostic to empower a variety of people to test their own ideas and algorithms, the language doesn't really matter. A widely used language is prefered (like Python for example) and communication happens via REST. The data for the algorithm is requested from the database service from the backend and results are visualized using the visualization tool which acts as the primary interface.

- **Difficulty**: Hard
- **Skills**: Polymer, Python (or any other good prototyping language), routing algorithms, REST
- **Mentor**: Fabian Bormann

## Back end projects

### Database service

A database is the integral part of this framework. The service will be written in Golang, with either SQLite (for portable devices) or Postgres as back end. It's tasks are
- Gathering data from
  - OSM
  - NASA (terrain information)
  - Weather services
  - Traffic services
- Creating and updating databases
- Making database queries and providing RPC and REST interfaces for the routing service
- Managing queries (batch queries, ordering, queueing etc)

The challenges are creating/updating the database, evaluating perfomance for different schemas, queries and caching strategies. Also, the service must be accessible via REST (to run standalone on a server) and is the main component for administration of the framework.

- **Difficulty**: ~~Nightmare~~ Very hard
- **Skills**: Database (SQLite3/Postgres), Golang, REST/RPC, Query optimization
- **Mentor**: Max Lorenz

### Routing service

This is the heart of the project. The routing service contains the algorithms (A*, Dijkstra, ...) and communicates with the database service and optionally with the native service. For now, the primary target is to make the service work with an example algorithm (eg. A*), so the foundation for future algorithmic work is laid out. The service communicates via RPC or REST with the database and the native integration service. Actual routes are provided with a REST interface for the front end (webapp or visualization tool).

- **Difficulty**: Medium
- **Skills**: Golang, routing algorithms, REST
- **Mentor**: Max Lorenz

### Native integration service

To use GreenNav on a portable device, the routing service needs information like battery status, speed or the location. In order to gather the information, this service should be easy to adapt to new architectures and provide a thin layer over the actual hardware. Information must be accessible via REST and RPC. As an example, this should work on a Raspberry Pi and Android.

- **Difficulty**: Easy
- **Skills**: Golang, Raspberry Pi, Android (ARM), Hardware
- **Mentor**: Jannes Feye

## Mobile projects

### React native app

We decided to implement GreenNav as a web application and provide a responsive website for mobile devices. But since Facebook launched React Native it's possible to write apps with a native feeling using only one code base using Javascript ES6. So it would be very cool to develop an React Native app that works on Android and iOS. The backend (Database/SQLite, Routing service, Native service) must be bundled as libraries.

- **Difficulty**: Hard
- **Skills**: JavaScript ES6, React Native, Golang, Android, iOS
- **Mentor**: Fabian Bormann

## Own ideas

You have a cool idea that is aligned with our vision (see the roadmap) but is not listed here? We would love to hear it!

- **Difficulty**: Depends
- **Skills**: Whatever is necessary
- **Mentor**: [Mailing list](https://www.isp.uni-luebeck.de/mailman/listinfo/greennav)