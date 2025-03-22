# JSON Schema Validator

A library that validates JSON structure based on a defined schema. It helps ensure that the data being used in your application conforms to a specific format, making your data handling more reliable and predictable. This project is ideal for developers who need to validate JSON data for APIs, configuration files, or any other JSON-based data sources.

## Table of Contents
1. [Installation](#installation)
2. [Usage](#usage)
3. [License](#license)

## Installation

To install the project and its dependencies, run the following command:

```bash
npm install json-schema-validator
```

## Usage

Once the library is installed, you can start using it in your project by importing the validateSchema function.

```typescript
import { validate, isDefined, isOptional } from 'json-schema-validator';

const loginObject = {
    email: 'test@example.com',
    password: 'test'
}

const loginSchema = {
    email: isDefined().isEmail(),
    password: isDefined().isComplexPassword()
}

const loginErrors = validate(loginObject, loginSchema);

const registerObject = {
    firstName: 'TestFName',
    lastName: 'TestLName',
    email: 'test@example.com',
    password: 'password'
}

const registerSchema = {
    firstName: isDefined().isString({ noEmpty: true, max: 50}),
    middleName: isOptional().isString({ noEmpty: true, max: 50 }),
    lastName: isDefined().isString({ noEmpty: true, max: 50 }),
    email: isDefined().isEmail(),
    password: isDefined().isComplexPassword(),
}

const registerErrors = validate(registerObject, registerSchema);

```

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

---

**Copyright (c) 2025 Ovidiu Podina.**
