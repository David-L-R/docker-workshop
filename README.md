![docker logo](https://user-images.githubusercontent.com/31222514/232439594-66e31ac6-e1cd-4424-a173-77688e02e81b.png)

# DOCKER

## What

Docker enables consistent and portable application deployment by packaging software with its dependencies, eliminating the reliance on pre-installed components on a machine. This ensures applications run seamlessly across different environments, streamlining development, and reducing compatibility issues.

Docker is an open-source platform that automates the deployment, scaling, and management of applications by using containers. Containers are lightweight, portable, and self-sufficient units that include an application and its dependencies, allowing it to run consistently across different environments. Docker simplifies and streamlines the process of creating, packaging, and deploying applications in containers.

## Why

Docker is needed for several reasons, including:

1. Consistency: Docker containers ensure that applications run the same way, regardless of the environment they are deployed in. This consistency helps to minimize the "it works on my machine" problem, which often occurs when software behaves differently on development, testing, and production environments.

1. Portability: Docker containers can be easily moved between different systems, as they contain all the dependencies required to run the application. This portability simplifies the deployment process and makes it easier to share and distribute applications.

1. Isolation: Docker allows for better isolation between applications, as each container runs independently from the others. This isolation reduces the risk of conflicts between different applications or dependencies, making it easier to manage and maintain multiple applications on a single system.

1. Scalability: Docker facilitates horizontal scaling by making it easy to create multiple instances of a containerized application. This scalability allows for better load balancing and handling of traffic spikes, ultimately improving application performance.

1. Efficiency: Containers are generally more resource-efficient than virtual machines, as they share the host system's kernel and do not require a separate operating system for each application. This efficiency translates into lower resource usage and faster start-up times for containerized applications.

# Setup

All these information is confusing... Let's look at a concrete example. 

When we run our Node/React applications we start by installing packages. To do that we are using `npm install`. But, we actually assume the machine we are running this code on has `npm` installed. 

So how do we make sure that no matter where we run our code - our local machine, or an external server, the code will run correctly? 

Docker come to save the day!

