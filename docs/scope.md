## How the gateway works

![Merchant Application](docs/images/Payment-Gateway-Design.png)


# Description
A user sends a payment request to the API Gateway. And then there are several operations that happen down the pipeline.
1. The user must be authenticated
2. Check for idempotency to prevent duplicate requests
3. Orchestrate payment to send the request to the provider if the previous steps went well.
4. The state of the request is updated to "PROCESSING" now.
5. Events are published to the queue. This state is used for loose-coupling of the system.

## Domain Entities
1. PaymentRequest
2. Ledger
3. Merchant
4. Logs
