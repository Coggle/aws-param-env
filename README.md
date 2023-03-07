[![npm version](https://badge.fury.io/js/aws-param-env-sdkv3.svg)](https://badge.fury.io/js/aws-param-env-sdkv3)

# aws-param-env

Module for loading parameter-store values from AWS SSM into environment variables

This fork has been updated to depend on [aws-param-store-sdkv3](https://github.com/coggle/aws-param-store), in order to support the AWS SDK v3 (and now depends only on the client-ssm module of the sdk).

## Features
* Loads parameters by path
* Runs synchronously to that environment variables can be set before your code loads
* Recursively loads and decodes parameters by default
* Can run inside AWS Lambda environment
* AWS Lambda Node.js 10.x compatible

## Installation
Install via npm.

	npm install aws-param-env-sdkv3 --save

## Getting Started

```js
const awsParamEnv = require( 'aws-param-env-sdkv3' );

awsParamEnv.load( '/my-service-path-in-ssm/env' );
```

If your AWS region is not set in your environment variables, then it can be set programmatically by supplying
options when calling `load()`:

```js
const awsParamEnv = require( 'aws-param-env-sdkv3' );

awsParamEnv.load( '/my-service-path-in-ssm/env', { region: 'us-east-1' } );
```

To load the environment variables automatically from a path, set the `AWS_SSM_ENV_PATH` to the SSM path and the
`AWS_REGION` to the correct AWS region.

```js
// AWS_SSM_ENV_PATH = '/my-services/service1/env', AWS_REGION='us-east-1'
require( 'aws-param-env-sdkv3' );

// environment variables are automatically loaded from the SSM parameter store
```


## License

[BSD-3-Clause](https://en.wikipedia.org/wiki/BSD_licenses)
