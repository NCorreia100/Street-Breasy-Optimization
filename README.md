# Street Breasy Optimization Project
> Street Breasy Project Introduction

![component-screen-capture](listing-page-load-balancer-documentation/images/component-screen-capture.gif)

This repository contains the source for a single component of a real estate listing page built with a microservice architecture (SoA). The component is designed as a full stack service and includes a Node.Js API, a MongoDB database, an Nginx content-cashing proxy and a load-balancer proxy. The API provides different image links to the client depending on a listing id number.


## Readme Contents

- [Requirements and Dependencies](#requirements)
- [Development Setup and Server Provisioning](#development-setup-and-server-provisioning)
- [Performance Optimizations](#performance-optimizations)
- [API Documentation](#api-documentation)
- [Visual Comparison](#visual-comparison)


## Requirements

#### External API Key

- This project makes use of the MapBox API to access static map images. To get an API key visit: https://www.mapbox.com/signup

#### Key Dependencies

- [Node.js](https://nodejs.org/en/) with [Express.js](https://expressjs.com/) web framework
- [MongoDB](https://www.mongodb.com/) database
- [React](https://reactjs.org/docs/getting-started.html) front end framework
- [Eric Meyer's CSS Reset](https://meyerweb.com/eric/tools/css/reset/)

## Development Setup and Server Provisioning

1. Create a server instance to run the project
2. On the remote server, allow traffic through TCP protocol on ports 22 and 80 for SSH and HTTP and ICMP (for ping)
3. VPN to the remote server  
4. On the terminal, once at the desired directory, run the command `git clone https://github.com/HackberryPie/listing-page-load-balancer.git` followed by `cd listing-page-load-balancer`.
5. Run the command `npm install` to download all required modules
6. On a different terminal window run the command `mongod --dbpath [path]` in which path refer to path to a directory of your choice as data storage
7. To start the server run the command `npm start`.
8. To make an API request, on your browser's address bar, enter your remote server's URL (or IP) followed by a single `/` and an interger between `1` and `10000000`
9. Optionally, you may use a tool to start the node server such as [pm2](http://pm2.keymetrics.io/) or [docker](https://docs.docker.com/docker-hub/).
10. Optionally you may also select a different port to receive incoming HTTP requests. To do so, modify the value of `GATEWAY_PORT`. Default is `80`.


## Performance Optimizations

### Optimization goals
The optimization goals for this project were as follows:
 - Decrease latency for a complete page load to not exceed 1 second
 - Increase server capacity to sustain at least 2'000 RPS (requests per second)
 - Diminuish error rate (such as connection time out and port in use)
 - Document metrics akin to each implementation


### Optimization tools / techniques
    - Artillery.js for submiting large waves of requests (and get error rate)
    - Newrelic.js to create reports on the performance of the server (latency and request-rate)
    - Google's DevTools Performance Analyzer
    - Compression.js to apply gzip compression to reduce the response body size 
    - Morgan.js to log API requests and timing to complete the full request-response cycle
    - Babel to transpile JSX code to JavaScript and eariler versions of JavaScript (such as ES6 and ECMAScript2018) to ES5
    - Webpack to compress all code into a single file with the required modules
  

## API Documentation


[Image Carousel API Documentation](documentation/api-documentation.md)













## Author

* [**Nuno Correia**](https://www.linkedin.com/in/nuno-correia-901904132/)




## References

- [Installing MongoDB on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-mongodb-on-ubuntu-18-04)
- [Installing Node on Ubuntu 18.04](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04)
- [ReactCSSTransitionGroup Add-On Documentation](https://reactjs.org/docs/animation.html)
- [Updating React Component State When Props Change](https://reactjs.org/docs/react-component.html#static-getderivedstatefromprops)

