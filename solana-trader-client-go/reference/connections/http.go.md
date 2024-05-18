# http.go

The `http.go` file defines several functions for making HTTP GET and POST requests and handling their responses. Here's a breakdown:

1. `HTTPError`: This struct represents an HTTP error, with fields for the error code, details, and message.
2. `HTTPGetWithClient[T protoreflect.ProtoMessage]`: This function makes an HTTP GET request to a specified URL using a provided http.Client. It sets several headers, including an authorization header and headers for the SDK name and version. It then sends the request and handles the response. If the response status is not OK, it unmarshals the error from the response. If the status is OK, it unmarshals the response body into a provided ProtoMessage.
3. `HTTPPostWithClient[T protoreflect.ProtoMessage]`: This function is similar to `HTTPGetWithClient`, but it makes a POST request and includes a body. The body is marshaled into JSON and included in the request.
4. `httpUnmarshalError`: This function reads the body of an HTTP response and returns it as an error.
5. `httpUnmarshal[T protoreflect.ProtoMessage]`: This function reads the body of an HTTP response and unmarshals it into a provided ProtoMessage using the protojson package.

In summary, this file provides functions for making HTTP requests and handling their responses, with support for protobuf messages.
