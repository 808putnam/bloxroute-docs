# http\_error.py

The `http_error.py` file defines a custom exception class `HttpError` and a helper function `map_response`.

The `HttpError` class is a custom exception that is raised when an HTTP request fails. It includes the HTTP status code, a message describing the error, and a list of details about the error. The class also includes a class method `from_json` that creates an `HttpError` instance from a JSON payload.

The `map_response` function is an asynchronous function that takes an HTTP response and a destination object (an instance of a `betterproto.Message` subclass). If the HTTP response status is not 200 (indicating an error), it raises an `HttpError` with the status code and the response text. If the response status is 200, it tries to create an `HttpError` from the response JSON. If this fails (because the response JSON does not represent an error), it converts the response JSON to a dictionary and uses it to update the destination object.
