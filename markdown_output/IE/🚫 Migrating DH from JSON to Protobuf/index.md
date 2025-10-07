**VERDICT: DROPPED / NOT IMPLEMENTED**

**Reason:** Since there is negligible difference between the data sizes
of compressed JSON and Protobuf, combined with the effort and overhead
clients will have to endure to replace json with proto, there is no
benefit in pursuing this path any further.

## Why This Matters for iOS

- Improves performance and memory efficiency on mobile devices

- Reduces payload sizes, benefiting network usage

- Provides strict schema enforcement through `.proto` definitions

------------------------------------------------------------------------

## Step-by-Step Implementation for iOS

### 1. Integrate SwiftProtobuf

Add SwiftProtobuf to the project via Swift Package Manager:

Target only the `SwiftProtobuf` product.

------------------------------------------------------------------------

### 2. Install protoc and Swift plugin

Install the required tools for generating Swift files from `.proto`
definitions:

brew install swift-protobuf // may need sudo

Ensure `protoc-gen-swift` is available in your PATH.

------------------------------------------------------------------------

### 3. Define .proto Files

Define Protobuf schemas corresponding to your existing JSON models.

Example:

syntax = \"proto3\"; package api; message User { string id = 1; string
name = 2; int32 age = 3; bool is_active = 4; } message APIResponseUser {
int32 code = 1; User data = 2; }

------------------------------------------------------------------------

### 4. Generate Swift Files

Run the `protoc` command to generate `.pb.swift` files:

protoc \\
\--swift_out=Visibility=Public,KeepProtoFieldNames=true,ProtoPathModuleMappings=off:./Generated
\\ \--proto_path=./Protos \\ ./Protos/User.proto

Add the generated `.pb.swift` files to your Xcode project.

**Full script**

#!/bin/bash set -e PROTO_DIR=\"./proto\" BIN_DIR=\"./bin\" mkdir -p
\"\$BIN_DIR\" protoc \--proto_path=\"\$PROTO_DIR\" \\
\--encode=models.APIResponseUser \\ \"\$PROTO_DIR/User.proto\" \<
\"\$PROTO_DIR/example_data.textproto\" \> \"\$BIN_DIR/response.bin\"
echo \"✅ response.bin generated at \$BIN_DIR/response.bin\"

------------------------------------------------------------------------

### 5. Replace Codable with SwiftProtobuf

Update your model usage:

**Before (Codable):**

struct User: Codable { let id: String let name: String let age: Int let
isActive: Bool } struct APIResponse\<T: Codable\>: Codable { let code:
Int let data: T }

**After (Protobuf):**

var user = Api_User() user.id = \"u123\" user.name = \"Alice\" user.age
= 30 user.isActive = true var response = Api_APIResponseUser()
response.code = 200 response.data = user

------------------------------------------------------------------------

### 6. Networking with Alamofire 4.0

Protobuf requires sending and receiving binary data. Alamofire 4.0 does
not support raw bodies directly with `.request(...)`, so use a custom
`URLRequestConvertible`:

struct ProtobufRequest: URLRequestConvertible { let url: String let
data: Data func asURLRequest() throws -\> URLRequest { var request =
URLRequest(url: URL(string: url)!) request.httpMethod = \"POST\"
request.setValue(\"application/x-protobuf\", forHTTPHeaderField:
\"Content-Type\") request.httpBody = data return request } }

Usage:

let requestData = try? user.serializedData() let request =
ProtobufRequest(url: \"https://api.example.com/user\", data: requestData
?? Data()) Alamofire.request(request)

To decode:

Alamofire.request(\"https://api.example.com/user\").responseData {
response in guard let data = response.data else { return } do { let
parsed = try Api_APIResponseUser(serializedData: data)
print(parsed.data.name) } catch { print(\"Decoding error: \\(error)\") }
}

------------------------------------------------------------------------

## Challenges and Considerations

### Generic APIResponse

Protobuf does not support generics. Each model must have a corresponding
concrete wrapper:

message APIResponseUser { int32 code = 1; User data = 2; } message
APIResponseOrder { int32 code = 1; Order data = 2; }

Alternatives:

- Use `google.protobuf.Any` for dynamic payloads (with type unpacking)

### Optional Fields

Primitive fields do not track presence unless explicitly marked
`optional`:

optional string email = 5;

Ensure you use `protoc` \>= 3.12 and SwiftProtobuf \>= 1.14 for optional
support.

### Debugging

Binary format is not human-readable. Use `protoc --decode` to inspect
messages:

protoc \--proto_path=. \--decode=api.APIResponseUser Protos/User.proto
\< bin/response.bin

### Migration Strategy

- Start with new features or low-risk endpoints

- Dual support (JSON and Protobuf) via API versioning

- Gradual model-by-model conversion

------------------------------------------------------------------------

### Related

true
