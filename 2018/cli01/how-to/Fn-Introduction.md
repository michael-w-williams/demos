# Introduction to the Fn Project
The Fn project is an open source serverless compute platform. With Fn, you deploy your functions to an Fn server which automatically executes and manages it. Each function is executed in a Docker container enabling the platform to provide broad support for development languages including Java, JavaScript (Node), Go, Python, Ruby, and others. The Fn client and server are simple and elegant allowing you to run the server either locally on a laptop or in the cloud. The Fn projects provides a strong enterprise focused tool that emphasizes security, scalability, and observability.

## What is Serverless?
Serverless computing is a cloud-computing architecture where applications are broken up into small pieces of code which are dynamically allocated and managed in the cloud. The advantage of this approach is code is called and executed only when needed. This differs from a classic server approach where applications are loaded into a server spending most of their time idle, waiting for requests. Thus, in serverless computing you only need to pay for computing resources you actually use, rather than paying for infrastructure that is mostly idle.

## Why use Serverless?
First, the cost of serverless applications, over the long haul, should be cheaper as fewer resources are wasted in an idle state. In addition, serverless systems should be easier to design and implement as complex issues like scaling, high availability, and security are pushed to the serverless vendor. Large scale vendors take on the tougher issues and economies of scale results in a costs savings. This allows you to just focus on your code and what it needs to do.

## How does Serverless Functions Compare with Microservices?
In serverless, the small piece of code that does all the work is called a Function. And,  a serverless cloud service typically provide functions-as-a-service (FAAS). Thus all the plumbing needed to provision, scale, patch and maintain the environment is provided by the service.

Microservice architectures have been all the rage. Rather than create one large monolithic service, a service is decomposed into smaller services which provide the same set of functions. It simplifies the develop and creation of web services. However, each microservice is still running its' own server which must be scaled and managed. FAAS takes things one step further.

![Monolithic vs Microservices vs Functions](images/fn-mono-to-funcs.png)

Web services have been broken down into smaller and simpler components with each change in the architecture. FAAS architecture holds a great deal of promise in reducing cost and complexity of applications.

## The Fn Architecture
The Fn serverless platform provides an open source implementation of these ideas. For example, a typical Fn implementation might look like this:

![Fn Architecture Diagram](images/fn-architecture.png)

A load balancer provides a front end to several Fn servers. Each server manages and executes function code as needed. Servers can be scaled up or done as needed.

 With Fn, each function is stored in a [Docker](https://www.docker.com) container. A Docker container is a simple virtualized instance of an operating system. Containers can be customized to include just the tools and languages you need to execute your application. Thus, containers are an ideal option for running function code.

 ## Functions with Fn
 Writing a function for Fn is easy. You just create a small chunk of code that does the following:

 * Gets input via STDIN
 * Produces output to STDOUT
 * Logs any errors to STERR

You code is deployed to an Fn server where it is staged and ready to go when a call is made for that function. For example, to create deploy an Fn function create a `myfunc` directory, change into it, and execute these commands:

* `fn init --runtime node`
    * Creates a sample Node.js app in the current directory.
* `fn run`
    * Runs the function locally to test the output.
* `fn deploy --app nodeapp`
    * Deploys your app to the Fn server. The function is now a part of the app "nodeapp" and the function name is picked up from your directory name. In this case "myfunc".
* `fn call nodeapp myfunc`
    * Call the function stored on the Fn server.
* `curl http://localhost:8080/r/nodeapp/myfunc`
    * Make the same call, but this time to an URL and curl.

Now your function is up and running.

### What happens during Deploy
When you deploy your function to an application on Fn server, the following happens:

![Picture of the Deploy Process](images/fn-deploy-details.png)

1. A container is built with your code and the version number is bumped.
2. Your container is pushed to your container registry (DockerHub by default).
3. A route is created to your function on the server.

That's it. When you call the function via the call command or curl, the container is executed and the results are returned to you.

### Fn Makes Function Development Easy
The Fn platform includes helper libraries or FDKs which make function development easier.

![Pictures of supported languages](images/fn-fdks.png)

The FDK provides help by parsing input and writing output in a stadard way, e.g., `JSON`. 

A number of FDKs exist for popular languages Java, Node.js, Python, Go, and Ruby.
