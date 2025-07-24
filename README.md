# platformOS Tests Module

The goal of this module is allow to write and run tests in liquid.
It can also test sent mails.

## Installation

The platformOS Tests Module is available on the [Partner Portal Modules Marketplace](https://partners.platformos.com/marketplace/pos_modules/130).

### Prerequisites

Before installing the module, please ensure you have [pos-cli](https://github.com/mdyd-dev/pos-cli#overview) installed. This tool is essential for managing and deploying platformOS projects.

### Installation Steps

1. **Navigate to your project directory** where you want to install the Tests Module.

2. **Run the installation command**:

```bash
   pos-cli modules install tests
   pos-cli modules download tests
```

This command installs the Tests Module and updates or creates the `app/pos-modules.json` file in your project directory to track module configurations.

## Testing liquid functions

Put your test file in `app/lib/tests/`. File name should end with `_test.liquid`, ex. `app/lib/tests/some_command_test.liquid`.
Every test should call at least one assertion.

``` liquid
{% liquid
  assign data = '{ "foo": "bar" }' | parse_json
  function object = 'some_command', object: data

  function contract = 'modules/tests/assertions/valid_object', contract: contract, object: object, field_name: 'object'
%}
```
To run test you need to go to `/_tests`.

### Assertions

- modules/tests/assertions/blank
- modules/tests/assertions/equal
- modules/tests/assertions/invalid_object
- modules/tests/assertions/not_presence
- modules/tests/assertions/not_valid_object
- modules/tests/assertions/object_contains_object
- modules/tests/assertions/presence
- modules/tests/assertions/valid_object

If you want you can test the function results with liquid conditions and then in case of invalid state you have to run 
``` liquid
function contract = 'modules/tests/helpers/register_error', contract: contract, field_name: field_name, message: 'some error message'
```


### Runing tests in CI

TODO


## Testing emails

To check sent mails you need to go to `/_sent_mails`
