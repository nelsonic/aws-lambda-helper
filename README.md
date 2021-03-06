# aws-lambda-helper
Collection of helper methods for lambda


## Installation
`$ npm install aws-lambda-helper --save`

## Usage
`const helper = require('aws-lambda-helper');`


### getEnvironment

Function to get environment from context object

Example:

```javascript
  const context = {
    invokedFunctionArn: 'arn:123:abs:prod'
  };

  var env = helper.getEnvironment(context); // 'prod';

```

In case of incorrect context or misconfigured function ARN it will return `null`.

### validateWithSchema

Function to validate input data with defined schema

```javascript
  import payloadSchema from '../schemas/validationSchema';

  const data = {
    a: 1,
    b: 'Hello World'
  };

  var result = helper.validateWithSchema(data, payloadSchema); // true

```

In case of validation error it will **throw** an error, so for safest coding practices use `try/catch` statements.

```javascript
  try {
    helper.validateWithSchema(data, payloadSchema);
  } catch (error) {
    // handle an error
  }
```
