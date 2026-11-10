## Payment Workflow

![Payment Workflow](docs/images/payment-lifecycle.png)

# Description
When a request is created, the default state is 'PENDING'. When it is being acted upon, the state changes to 'PROCESSING'. When the processing is complate, it is moved to "SUCCEEDED" if all goes well, or "FAILED" if any of relevant operations involved fails. Or it can move to "REQUIRES_ACTION" if there is something to be done at the payment processor end.