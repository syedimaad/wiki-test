Project link - <https://gitlab.dailyhunt.in/ios/pulsenet>

PulseNet is a robust, extensible Swift networking SDK designed for
modern iOS applications. It provides a type-safe, builder-based API for
constructing and executing HTTP requests, with built-in support for
retries, error handling, logging, and network metrics.

## Features

- ✅ Type-safe request builder

- 🔄 Automatic retry policy with configurable count & delay

- ⚠️ Comprehensive error handling (HTTP and client-side)

- 🧵 Concurrency support

- 🛑 Full cancellation support (active requests & scheduled retries)

- 📜 Pluggable, configurable logging system

- 📊 Network metrics collection (timing, status, retries, response size,
  etc.)

- 📦 Codable/Decodable response support

## 🏁 Getting Started

### 🔹 Building a Request

Use the `PulseNetRequest.Builder` to construct requests in a fluent,
type-safe manner:

wide760let request = PulseNetRequest.Builder(url: URL(string:
\"https://api.example.com/data\")!, method: .get)
.setHeaders(\[\"Authorization\": \"Bearer token\"\])
.setQueryParams(\[\"q\": \"search\"\]) .setTimeout(15) .setRetryCount(2)
.setRetryDelay(2.0) .build()

------------------------------------------------------------------------

### 🔹 Executing a Request

#### Raw Data response

wide760request.execute { result in switch result { case .success(let
data): // Handle data case .failure(let error): // Handle error
(PulseNetError) } }

#### Decoding to Codable type

wide760struct MyModel: Codable { /\* \... \*/ } request.execute(as:
MyModel.self) { result in switch result { case .success(let model): //
Use your decoded model case .failure(let error): // Handle error } }

------------------------------------------------------------------------

### 🔹 Error Handling

All errors are returned as `PulseNetError`, which provides:

- **code**: A `PulseNetErrorCode` (HTTP or client-side)

- **domain**: The error domain

- **message**: Human-readable error message

- **underlyingError**: The original error, if any

- **httpStatusCode**: The HTTP status code, if available

Example:

wide760if let pnError = error as? PulseNetError { print(pnError.code,
pnError.message) }

------------------------------------------------------------------------

### 🔹 Logging

PulseNet provides a flexible logging system:

- Log levels: `.debug`, `.info`, `.warning`, `.error`

- Plug in a custom logger (conform to `NetworkLoggerConfigurable`)

- Enable/disable logging globally

Configuration:

wide760PulseNetRequest.configureLogger(\[ .level(.debug), .enabled(true)
\])

------------------------------------------------------------------------

### 🔹 Network Metrics

Each request collects metrics (`NetworkMetrics`):

- Request/response size

- Timing (start, end, duration)

- Retry attempts

- Final status code

- Error (if any)

Example:

wide760let metrics = request.metrics

------------------------------------------------------------------------

## 📖 Public API Reference

### **PulseNetRequest**

- `Builder(url:method:)` -- Start building a request

- `setHeaders(_:)`, `setQueryParams(_:)`, `setBody(_:)`,
  `setTimeout(_:)`, `setQueueType(_:)`, `setRetryCount(_:)`,
  `setRetryDelay(_:)` -- Builder methods

- `build()` -- Finalize the request

- `execute(completion:)` -- Execute and get raw `Data`

- `execute(as:completion:)` -- Execute and decode to Codable type

- `metrics` -- Access collected network metrics

- `configureLogger(_:)` -- Configure logging globally

------------------------------------------------------------------------

### **PulseNetError & PulseNetErrorCode**

- `PulseNetError`: `code`, `domain`, `message`, `underlyingError`,
  `httpStatusCode`

- `PulseNetErrorCode`: Includes all standard HTTP status codes and
  client-side errors

------------------------------------------------------------------------

### **Logging**

- `LoggerConfig`: `.level(LogLevel)`,
  `.custom(NetworkLoggerConfigurable)`, `.enabled(Bool)`

- `LogLevel`: `.debug`, `.info`, `.warning`, `.error`

- `NetworkLoggerConfigurable`: Protocol for custom loggers

------------------------------------------------------------------------

### **Metrics**

- `NetworkMetrics`: `requestID`, `url`, `method`, headers, body size,
  timing, retries, status code, response size, error

------------------------------------------------------------------------

### **Retry Policy**

- Automatic retry with configurable **count** and **delay** per request

------------------------------------------------------------------------

## 💡 Example Usage

wide760let request = PulseNetRequest.Builder(url: URL(string:
\"https://api.example.com/user\")!, method: .get) .setTimeout(10)
.setRetryCount(1) .build() request.execute(as: User.self) { result in
switch result { case .success(let user): print(user) case .failure(let
error): print(error) } }

------------------------------------------------------------------------

## 🔄 Execution & Concurrency

### **PulseNetManager**

- Singleton access (`PulseNetManager.shared`) for global request
  execution.

- Manages an internal `OperationQueue` with configurable concurrency
  (`maxConcurrentOperationCount = 4`).

- Ensures thread-safe request execution and concurrent request
  management.

### **PulseOperation**

- Subclass of `Operation` for granular control of request lifecycle.

- Supports retries, cancellation, and metrics recording.

- Manages its own execution state (`isExecuting`, `isFinished`).

- Runs asynchronously (`isAsynchronous = true`).

------------------------------------------------------------------------

## ⏱ Retry Policy

- Retries are **scheduled with delay** (`RetryPolicy.executeWithRetry`).

- Retries stop after reaching `retryCount`.

- On each retry:

  - `NetworkLogger` logs attempt number.

  - Cancelable retry via stored `retryCancellation`.

- Final failure calls `handleFinalFailure()`.

------------------------------------------------------------------------

## 🛑 Cancellation

- Cancels the active `URLSessionDataTask`.

- Cancels scheduled retries (`retryCancellation`).

- Immediately marks operation as `finished`.

Usage Example:

wide760let request = PulseNetRequest.Builder(url: someURL, method:
.get).build() let operation = PulseOperation(requestConfig: request,
requestIdentifier: request.requestIdentifier) { result in // Handle
result } PulseNetManager.shared.queue.addOperation(operation) // Later
operation.cancel()
