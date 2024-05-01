# jsonrpc\_patch.py

The `jsonrpc_patch.py` file is used to extend and modify the error handling of a JSON-RPC (Remote Procedure Call) system.

It defines a new enumeration `NewRpcErrorCode` that extends the standard set of JSON-RPC error codes with additional ones specific to the application, such as `AUTHORIZATION_ERROR`, `RATE_LIMIT_ERROR`, and `STREAM_LIMIT_ERROR`.

The `message_map` dictionary is updated to include human-readable messages for these new error codes.

The file then patches the `RpcError` class's `from_json` method. This method is used to create an `RpcError` instance from a JSON payload. The new `from_json` method first checks if the error code in the payload is one of the newly defined error codes. If it is, it creates an `RpcError` instance using the new error code. If the error code is not recognized, it falls back to the original `from_json` method.

This patching allows the JSON-RPC system to recognize and correctly handle the new error codes defined in this file.
