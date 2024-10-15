# What is AsyncAPI Document?

An AsyncAPI document serves as a blueprint for your Event-Driven API, much like an architect’s drawing defines the details of a building. Where REST APIs are like phone calls (request-response), AsyncAPI works more like a radio broadcast (publish-subscribe), optimized for real-time, event-driven communication.
The file format can either be JSON or YAML, but it must stick to a version of YAML that aligns with JSON’s capabilities.

Let's consider this example:

```yaml

asyncapi: 3.0.0
info:
  title: My cool AsyncAPI app
  version: '0.1.0'
channels:
  userSignup:
    address: 'user/signedup'
    messages:
      userSignedupMessage: 
        description: This message is triggered on event of a user sign up.
        payload:
          type: object
          additionalProperties: true
          properties:
            fullName:
              type: string
            email:
              type: string
              format: email
            age:
              type: integer
              minimum: 18
operations:
  publishUserSignedup:
    action: 'send'
    channel:
      $ref: '#/channels/userSignup'
```

The AsyncAPI document is machine-readable which means, other tools can easily understand it and do useful things, like: generating documentation and code, validating the messages that our `My cool AsyncAPI app` sends, and automating the workflows for example- applying API management policies to messages for checking if they're rightly formatted.

An AsyncAPI document provides clear instructions for both machines and developers on how to interact with your Event-Driven API. Similar to how REST APIs use documentation to define endpoints and parameters, AsyncAPI formalizes channels (where events are sent) and message formats, ensuring that everyone and everything knows how to work with your API.
