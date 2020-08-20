## API Gateway

#### What is an API?
An API is an Application Programming Interface. As an analogy, imagine a couple at a restaurant want to order off the menu. The couple don't want to go to the kitchen and the chef doesn't want to leave the kitchen. The waiter is basically an API - it takes the order to the kitchen to be processed and returns a result.

#### Types of API

**REST APIs (REpresentational State Transfer)**
- Uses JSON

**SOAP APIs (Simple Object Access Protocol)**
- Uses XML

#### What is API Gateway?
A fully managed service that makes it easy for developers to publish, maintain, monitor and secure APIs at any scale.

#### What can it do?
- Expose HTTPS endpoints to define a RESTful API.
- Uses "curl".
- Serverlessly connects to services like Lambda and DynamoDB.
- Send each API endpoint to a different target.
- Run efficiently with low cost.
- Scale effortlessly.
- Track and control usage by API key.
- Throttle requests to prevent attacks.
- Connect to CloudWatch to log all requests for monitoring.
- Maintain multiple versions of your API.

#### How to configure API Gateway

- Define an API (container).
- Define resources and nested resources (URL paths).
- For each resource:
  - Select supported HTTP methods (verbs).
  - Set security.
  - Choose target (such as EC2, Lambda, etc).
- Deploy API to a Stage.
  - Uses API Gateway domain, by default.
  - Can use custom domain.

#### What is API caching?
You can enable API caching in API Gateway to cache your endpoint's response. This can reduce the number of calls made to your endpoint and improve the latency of requests. When this is enabled, API Gateway caches responses for a specified TTL. API Gateway then responds to the request by looking up the endpoint response from the cache instead of making a request to the endpoint.

#### Same Origin Policy

In computing, the **same-origin policy** is a concept in the web app security model. Under this policy, a web browser permits scripts contained in a first web page to access data in a second web page, only if both web pages have the same origin.
This is to prevent Cross-Site Scripting (XSS) attacks.
- Enforced by web browsers.
- Ignored by tools like curl.

#### CORS
Cross-origin resource sharing is a mechanism that allows restricted resources (eg fonts) on a web page to be requested from another domain outside the domain the first resource was served.

- Browser makes an HTTP OPTIONS call for a URL
- Server returns a response with the domains approved to GET this URL
- Error - "Origin policy cannot be read at the remote resource?"
  - You need to enable CORS on API Gateway

#### Exam tips
- Remember what API Gateway is at a high level.
- API Gateway has caching capabilities to increase performance.
- Low cost and scales automatically.
- You can throttle API Gateway to precent attacks.
- You can log results to CloudWatch.
- If you are using Javascript that uses multiple domains with API Gateway, you need CORS on API Gateway.
- CORS is enforced by the client.

#### Advanced tips
- You can import APIs, currently this supports Swagger v2.0 definition files.
- API throttling: By default, API gateway limits the steady state request rate to 10,0000 rps. The max concurrent requests is 5000 per account. If you go over this limit, you will receive a 429 Too Many Request error.
- SOAP Webservice Passthrough configuration is possible.
