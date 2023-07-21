## Shared Run Configurations Example

This project serves as a simple example and test to check that different IDE configuration tools allow teams to share configs for debuggers, recommended project settings/plugins, and more.

The goal is that team members should be able to spin up large projects with many test/debug tasks across different environments within a monorepo or similar project structure with multiple entry points or test/debug builds.

A key to this is that often teams and debug configurations will require secret values such as keys, database connection strings, and more.

## Getting started

1. Make sure you have Node installed and if necessary check that your IDE is able to debug a simple project.
2. Copy the 3 `*.env.sample` files into their respective non-committed `.env` files:

```sh
cp .local.env.sample .local.env && cp .staging.env.sample .staging.env && cp .test.env.sample .test.env
```

## Lauch/Debug Configurations

The sharable configurations should be the following and print the following results (formatted as JSON `{VAR_1, VAR_2, VAR_3, VAR_4}` values)

1. Launch <No Env> - this will print undefined for all env values unless you have defined them in the shell that opened your IDE (or similar global environment profile)
2. Launch <Hardcoded> - this will print `{VAR_1: 'ide-1', VAR_2: 'ide-2', VAR_3: 'ide-3', VAR_4: 'ide-4'}` and all env values are set in the committed launch/run config
3. Launch <.local.env> - this will print values based on the values in `.local.env` the program can either fail to start or work like `<No Env>` if the env file doesn't exist
4. Launch <.staging.env> - this will print values based on the values in `.staging.env` the program can either fail to start or work like `<No Env>` if the env file doesn't exist
5. Launch <.test.env> - this will print values based on the values in `.test.env` the program can either fail to start or work like `<No Env>` if the env file doesn't exist
6. Override <.local.env> - this should try to read from `.local.env` and then set `VAR_1` in the shared launch configuration to document what happens if a value is defined in both the launch config and .env file