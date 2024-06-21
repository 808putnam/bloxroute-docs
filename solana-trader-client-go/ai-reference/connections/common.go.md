# common.go

The `common.go` file defines a generic Streamer type and methods associated with it. Here's a breakdown:

1. `Streamer[T any]`: This is a type definition for a function that returns a value of any type `T` and an error. This function can be any function that matches this signature.
2. `func (s Streamer[T]) Channel(size int) chan T`: This method creates a channel of type `T` with a specified size. It then starts a goroutine that continuously calls the Streamer function and sends the returned values into the channel. The channel is returned to the caller.
3. `func (s Streamer[T]) Into(ch chan T)`: This method starts a goroutine that continuously calls the Streamer function and sends the returned values into a provided channel. If the Streamer function returns an error, the channel is closed and the goroutine exits.

In summary, this file provides a way to continuously call a function (that returns a value and an error) and send the returned values into a channel. This can be useful for continuously reading data from a source and providing it to other parts of your program in a concurrent manner.
