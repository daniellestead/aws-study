## X-Ray

X-Ray is a service that collects data about requests that your application serves, and provides tools you can use to view, filter and gain insights int data to identify issues and opportunities for optimisation. For any traced request to your app, you can see detailed info not only about the request and response, but also about calls your application makes to downstream AWS resources, micro-services, databases and HTTP web APIs.

How it works:

- The X-Ray SDK is installed in your application.
- This sends bits of json to the X-Ray Daemon (which can be installed on all operating systems).
- The Daemon takes the json and sends it over to the X-Ray API.
- The API stores all this data and creates the X-Ray visualisation in the console.
- The scripts and tools (such as AWS CLI & SDK) communicate either with the Daemon or the X-Ray API directly.

The X-Ray SDK provides:
- Interceptors to add your code to trace incoming HTTP requests.
- Client handlers to instrument AWS SDK clients that your app uses to call other services.
- An HTTP client to use to instrument calls to other internal and external HTTP web services.

X-Ray integrates with:
- ELB
- API Gateway
- Lambda
- EC2
- Beanstalk

- Java
- Go
- Node.js
- Python
- Ruby
- .Net
