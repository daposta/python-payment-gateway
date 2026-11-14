## Payment Workflow

![Payment Workflow](docs/images/payment-lifecycle.png)

# Description
When a request is created, the default state is 'PENDING'. When it is being acted upon, the state changes to 'PROCESSING'. When the processing is complate, it is moved to "SUCCEEDED" if all goes well, or "FAILED" if any of relevant operations involved fails. Or it can move to "REQUIRES_ACTION" if there is something to be done at the payment processor end.

# Concerns
1. When the provider times out, we leave the record at "PROCESSING"
2. We distingish between failed payment and unkown payment outcome based on the status.
3. When a payment has multiple attempts, making the operation idempotency protects us from duplication of requests.
4. When the webhook is arrives before then provider response, then we might need to retry it.
5. Ledger posting happens when the status of the payment has changed to "SUCCEEDED"
6. Refunds and reversals are implemented using the Saga pattern where we issue conter-operations events