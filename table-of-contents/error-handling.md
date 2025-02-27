# 📖 Error Handling

### Use Async-Await or promises for async error handling

Handling async errors in callback style is probably the fastest way to hell (a.k.a the pyramid of doom). The best gift you can give to your code is using Promises with async-await which enables a much more compact and familiar code syntax like try-catch

### Extend the built-in Error object

Some libraries throw errors as a string or as some custom type – this complicates the error handling logic and the interoperability between modules. Instead, create app error object/class that extends the built-in Error object and use it whenever rejecting, throwing or emitting an error. The app error should add useful imperative properties like the error name/code and isCatastrophic. By doing so, all errors have a unified structure and support better error handling. There is `no-throw-literal` ESLint rule that strictly checks that (although it has some [limitations](https://eslint.org/docs/rules/no-throw-literal) which can be solved when using TypeScript and setting the `@typescript-eslint/no-throw-literal` rule)

### Distinguish catastrophic errors from operational errors

Operational errors (e.g. API received an invalid input) refer to known cases where the error impact is fully understood and can be handled thoughtfully. On the other hand, catastrophic error (also known as programmer errors) refers to unusual code failures that dictate to gracefully restart the application

### Handle errors centrally, not within a middleware

Error handling logic such as logging, deciding whether to crash and monitoring metrics should be encapsulated in a dedicated and centralized object that all entry-points (e.g. APIs, cron jobs, scheduled jobs) call when an error comes in

### Document API errors using OpenAPI or GraphQL

Let your API callers know which errors might come in return so they can handle these thoughtfully without crashing. For RESTful APIs, this is usually done with documentation frameworks like OpenAPI. If you're using GraphQL, you can utilize your schema and comments as well

### Exit the process gracefully when a stranger comes to town

When an unknown error occurs (catastrophic error, see best practice 2.3) - there is uncertainty about the application healthiness. In this case, there is no escape from making the error observable, shutting off connections and exiting the process. Any reputable runtime framework like Dockerized services or cloud serverless solutions will take care to restart

### Use a mature logger to increase errors visibility

A robust logging tools like [Pino](https://github.com/pinojs/pino) or [Winston](https://github.com/winstonjs/winston) increases the errors visibility using features like log-levels, pretty print coloring and more. Console.log lacks these imperative features and should be avoided. The best in class logger allows attaching custom useful properties to log entries with minimized serialization performance penalty. Developers should write logs to `stdout` and let the infrastructure pipe the stream to the appropriate log aggregator

### Test error flows using your favorite test framework

Whether professional automated QA or plain manual developer testing – Ensure that your code not only satisfies positive scenarios but also handles and returns the right errors. On top of this, simulate deeper error flows like uncaught exceptions and ensure that the error handler treat these properly (see code examples within the "read more" section)

### Discover errors and downtime using APM products

Monitoring and performance products (a.k.a APM) proactively gauge your codebase or API so they can automagically highlight errors, crashes, and slow parts that you were missing

### Catch unhandled promise rejections

Any exception thrown within a promise will get swallowed and discarded unless a developer didn’t forget to explicitly handle it. Even if your code is subscribed to `process.uncaughtException`! Overcome this by registering to the event `process.unhandledRejection`

### Fail fast, validate arguments using a dedicated library

Assert API input to avoid nasty bugs that are much harder to track later. The validation code is usually tedious unless you are using a modern validation library like [ajv](https://www.npmjs.com/package/ajv), [zod](https://github.com/colinhacks/zod), or [typebox](https://github.com/sinclairzx81/typebox)

### Always await promises before returning to avoid a partial stacktrace

Always do `return await` when returning a promise to benefit full error stacktrace. If a function returns a promise, that function must be declared as `async` function and explicitly `await` the promise before returning it

### Subscribe to event emitters and streams 'error' event

Unlike typical functions, a try-catch clause won't get errors that originate from Event Emitters and anything inherited from it (e.g., streams). Instead of try-catch, subscribe to an event emitter's 'error' event so your code can handle the error in context. When dealing with [EventTargets](https://nodejs.org/api/events.html#eventtarget-and-event-api) (the web standard version of Event Emitters) there are no 'error' event and all errors end in the process.on('error) global event - in this case, at least ensure that the process crash or not based on the desired context. Also, mind that error originating from _asynchronous_ event handlers are not get caught unless the event emitter is initialized with {captureRejections: true}
