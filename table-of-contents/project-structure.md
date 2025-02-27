# 📖 Project Structure

**Root Directory**:

* Configuration and setup files such as `README.md`, `docker-compose.yml`, `.dockerignore` `package.json`, TypeScript, Linters configuration files.

**Directories**:

* **`migrations`**: Migration scripts for database changes.
* **`prisma`**: Prisma ORM configuration.
* **`src`**:
  * **`config`**: Application configuration files.
  * **`constants`**: Constants used across the application.
  * **`decorators`**: Custom decorators for API responses and serialization.
  * **`filters`**: Custom exception filters.
  * **`interceptors`**: Request interceptors for serialization and transformation.
  * **`main.ts`**: Application entry point.
  * **`modules`**: Core application modules (app, auth, casl, health, user).
  * **`providers`**: Service providers (prisma, s3, sqs).
  * **`tests`**: Testing utilities and specifications.

\
Our project employs a layered architecture, ensuring clear separation of concerns and enhancing maintainability. Each module in our application follows the service repository pattern, including a controller, service, and repository:

1. **Controller**: Manages incoming requests and directs them to the appropriate service.
2. **Service**: Contains the business logic of the application.
3. **Repository**: Handles data access and interaction with the database.

This Service-Repository pattern promotes organized and scalable code management, making our system robust and easy to maintain.

Here’s an example of our basic project structure:

```
├── README.md
├── docker-compose.yml
├── jest-e2e.json
├── migrations
├── nest-cli.json
├── package-lock.json
├── package.json
├── prisma
│   └── schema.prisma
├── src
│   ├── config
│   │   ├── app.config.ts
│   │   ├── jwt.config.ts
│   │   ├── s3.config.ts
│   │   ├── sqs.config.ts
│   │   └── swagger.config.ts
│   ├── constants
│   │   └── errors.constants.ts
│   ├── decorators
│   │   ├── api-base-response.decorator.ts
│   │   ├── api-default-response.decorator.ts
│   │   ├── api-ok-base-response.decorator.ts
│   │   └── serialize.decorator.ts
│   ├── filters
│   │   ├── access-exception.filter.ts
│   │   ├── all-exception.filter.ts
│   │   ├── bad-request-exception.filter.ts
│   │   ├── base-exception.filter.ts
│   │   ├── not-found-exception.filter.ts
│   │   ├── throttler-exception.filter.ts
│   │   ├── validation-exception-factory.ts
│   │   ├── validation-exception.filter.ts
│   │   └── validation.exception.ts
│   ├── interceptors
│   │   ├── serialize.interceptor.ts
│   │   └── transform.interceptor.ts
│   ├── main.ts
│   ├── modules
│   │   ├── app
│   │   │   ├── app.module.ts
│   │   │   └── app.roles.ts
│   │   ├── auth
│   │   │   ├── auth.controller.ts
│   │   │   ├── auth.d.ts
│   │   │   ├── auth.guard.ts
│   │   │   ├── auth.module.ts
│   │   │   ├── auth.permissions.ts
│   │   │   ├── auth.service.ts
│   │   │   ├── dto
│   │   │   │   ├── jwt-tokens.dto.ts
│   │   │   │   ├── refresh-token.dto.ts
│   │   │   │   ├── sign-in.dto.ts
│   │   │   │   └── sign-up.dto.ts
│   │   │   ├── entities
│   │   │   │   └── tokens.entity.ts
│   │   │   ├── skip-auth.guard.ts
│   │   │   ├── token.repository.ts
│   │   │   └── token.service.ts
│   │   ├── casl
│   │   │   ├── access.guard.ts
│   │   │   ├── access.service.ts
│   │   │   ├── actions.enum.ts
│   │   │   ├── casl.config.ts
│   │   │   ├── casl.constants.ts
│   │   │   ├── casl.d.ts
│   │   │   ├── casl.module.ts
│   │   │   ├── decorators
│   │   │   │   ├── casl-conditions.ts
│   │   │   │   ├── casl-query-authorize.ts
│   │   │   │   ├── casl-subject.ts
│   │   │   │   ├── casl-user.ts
│   │   │   │   ├── index.ts
│   │   │   │   └── use-ability.ts
│   │   │   ├── factories
│   │   │   │   ├── ability.factory.ts
│   │   │   │   ├── subject-hook.factory.ts
│   │   │   │   ├── user-hook.factory.spec.ts
│   │   │   │   └── user-hook.factory.ts
│   │   │   ├── index.ts
│   │   │   ├── interfaces
│   │   │   │   ├── ability-metadata.interface.ts
│   │   │   │   ├── authorizable-user-meta.interface.ts
│   │   │   │   ├── authorizable-user.interface.ts
│   │   │   │   ├── casl-request-cache.interface.ts
│   │   │   │   ├── hooks.interface.ts
│   │   │   │   ├── options.interface.ts
│   │   │   │   ├── permissions.interface.ts
│   │   │   │   └── request.interface.ts
│   │   │   └── proxies
│   │   │       ├── conditions.proxy.ts
│   │   │       ├── context.proxy.ts
│   │   │       ├── request.proxy.ts
│   │   │       ├── subject.proxy.ts
│   │   │       └── user.proxy.ts
│   │   ├── health
│   │   │   ├── health.controller.ts
│   │   │   └── health.module.ts
│   │   └── user
│   │       ├── entities
│   │       │   ├── user-base.entity.ts
│   │       │   └── user.entity.ts
│   │       ├── user.controller.ts
│   │       ├── user.hook.ts
│   │       ├── user.module.ts
│   │       ├── user.permissions.ts
│   │       ├── user.repository.ts
│   │       └── user.service.ts
│   ├── providers
│   │   ├── prisma
│   │   │   ├── custom
│   │   │   │   ├── custom-prisma-options.ts
│   │   │   │   ├── custom-prisma.constants.ts
│   │   │   │   ├── custom-prisma.module.ts
│   │   │   │   ├── custom-prisma.service.ts
│   │   │   │   └── index.ts
│   │   │   ├── custom-prisma-options.ts
│   │   │   ├── custom-prisma.constants.ts
│   │   │   ├── custom-prisma.module.ts
│   │   │   ├── custom-prisma.service.ts
│   │   │   ├── index.ts
│   │   │   ├── interfaces
│   │   │   │   ├── index.ts
│   │   │   │   └── prisma-module-options.interface.ts
│   │   │   ├── middlewares
│   │   │   │   ├── create-user.middleware.ts
│   │   │   │   └── logging.middleware.ts
│   │   │   ├── prisma-client-exception.filter.ts
│   │   │   ├── prisma.constants.ts
│   │   │   ├── prisma.module.ts
│   │   │   └── prisma.service.ts
│   │   ├── s3
│   │   │   ├── s3.module.ts
│   │   │   └── s3.service.ts
│   │   └── sqs
│   │       ├── castom-message.ts
│   │       ├── sqs.constants.ts
│   │       ├── sqs.decorators.ts
│   │       ├── sqs.module.ts
│   │       ├── sqs.service.ts
│   │       └── sqs.types.ts
│   └── tests
│       ├── common
│       │   └── user.mock.functions.ts
│       ├── e2e
│       │   ├── common
│       │   │   ├── make-request.ts
│       │   │   └── routes.ts
│       │   ├── context
│       │   │   ├── base-context.ts
│       │   │   └── default-context.ts
│       │   ├── interfaces
│       │   │   ├── admin-user.interface.ts
│       │   │   └── make-request.interface.ts
│       │   ├── modules
│       │   │   ├── auth
│       │   │   │   ├── index.ts
│       │   │   │   └── modules
│       │   │   │       ├── auth-logout.ts
│       │   │   │       ├── auth-refresh.ts
│       │   │   │       ├── auth-sign-in.ts
│       │   │   │       └── auth-sign-up.ts
│       │   │   └── user
│       │   │       ├── index.ts
│       │   │       └── modules
│       │   │           ├── users-me-get.ts
│       │   │           ├── users-me-patch.ts
│       │   │           └── users.ts
│       │   ├── root.e2e-spec.ts
│       │   └── test.service.ts
│       ├── mocks
│       │   ├── token.service.mock.ts
│       │   └── user.repository.mock.ts
│       └── specs
│           ├── auth.service.spec.ts
│           └── user.service.spec.ts
├── tsconfig.build.json
└── tsconfig.json

```
