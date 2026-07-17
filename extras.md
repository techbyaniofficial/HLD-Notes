When could you use gRPC?

Suppose your company has two internal services.

Order Service
        |
        |
Inventory Service

Currently:

restTemplate.exchange(
    "http://inventory/checkStock",
    ...
);

Since you own both services, you can change them.

Order Service
       |
     gRPC
       |
Inventory Service

Now Order Service calls:

StockResponse response =
        inventoryStub.checkStock(request);

Much faster.

Rule for interviews
External APIs

Examples:

Google Maps API
Razorpay
PhonePe
Stripe
PayPal

➡️ Mostly REST.

You cannot switch them to gRPC.

Internal Microservices

Examples:

Order Service

Inventory Service

Notification Service

Payment Service

➡️ You can choose:

REST
gRPC
Kafka
Interview Question

Interviewer: Can we replace RestTemplate with gRPC?

Good answer:

Only if both the client and server are under our control and both support gRPC. If the API belongs to a third-party provider like Razorpay or Google Maps and only exposes REST endpoints, then we must continue using REST. gRPC is mainly used for communication between internal microservices where we control both ends.
