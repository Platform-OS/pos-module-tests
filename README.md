# platformOS Tests Module

The goal of this module is allow to write and run tests in liquid.
It can also test sent mails.

## Testing liquid functions

Put your test file in `app/lib/tests/`. File should end with `_test.liquid`, ex. `app/lib/tests/some_function_test.liquid`.
Every test should call at least one assertion.
To run test you need to go to `/_tests`.


## Testing emails

To check sent mails you need to go to `/_sent_mails`
