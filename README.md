
### 1. Key Differences: Unary, Server Streaming, Bi-directional Streaming RPC

    - Unary: Single request, single response for simple operations.

    - Server Streaming: Single request, multiple responses for sequence of results.

    - Bi-directional Streaming: Both client and server send streams for interactive, real-time scenarios.


### 2. Security Considerations in Rust gRPC

    - Use TLS with client certificates, JWTs, or OAuth2.
    - Implement role-based checks in service handlers.
    - Enable TLS for transit data encryption.
    - Validate inputs, handle errors securely, avoid log leaks.

### 3. Challenges in Bidirectional Streaming

    - it was challengin when it involves managing multiple async streams safely, preventing backpressure, gracefully handling errors, and ensuring proper closure of tasks and channels to prevent resource leaks.

### 4 Advantages/Disadvantages of tokio_stream::wrappers::ReceiverStream
    Advantages:
    - Simple integration with async channels.
    - Decouples producer/consumer logic.

    Disadvantages:
    - Tuning buffer size.
    - Less control over stream lifecycle and backpressure.


### 5. Structuring Rust gRPC Code for Reuse & Modularity
    - Separate services into modules/files.
    - Define shared types/utilities in common crate/module.
    - Use traits for service logic.
    - Keep business logic separate from transport code.


### 6. Extending MyPaymentService for Complex Logic
    - Validate payment details (amount, user, etc.).
    - Integrate with external payment gateways.
    - Handle asynchronous transaction status updates.
    - Implement error handling and retries.
    - Log transactions and audit trails.


### 7. Impact of gRPC Adoption on Distributed System Architecture
    Pros:

    - Strong cross-language interoperability.
    - Efficient binary serialization (Protocol Buffers).
    - Built-in streaming and multiplexing.
    
    Cons:
    - Requires schema management.
    - Not natively supported in browsers (needs gRPC-Web).
    - More complex setup than REST for simple use cases.

### 8. HTTP/2 (gRPC) vs HTTP/1.1 (REST/WebSocket)
    HTTP/2 Advantages:
    - Multiplexed streams (no head-of-line blocking).
    - Built-in support for streaming.
    - Binary framing (more efficient).
    
    Disadvantages:
    - More complex to debug.
    - Not universally supported by all proxies/firewalls

### 9. REST Request-Response vs gRPC Bidirectional Streaming
    - REST: One request, one response; polling needed for updates.
    - gRPC Streaming: Real-time, low-latency, full-duplex communication; ideal for live data (e.g., chat, telemetry).

### 10. Schema-based (gRPC/Protobuf) vs Schema-less (REST/JSON)
    Schema-based (gRPC/Protobuf):
    - Compile-time type safety.
    - Clear contracts and versioning.
    - Smaller, faster payloads.
    
    Schema-less (REST/JSON):
    - More flexible, easier for rapid prototyping.
    - Can lead to inconsistencies and runtime errors.
    - Larger, slower payloads.
   

