# GoFortune

A [Fortune](https://en.wikipedia.org/wiki/Fortune_(Unix)) clone using Go!

## Installation

Compile the code into an executable.
```go
go build -o gofortune
```

You can discover the install path by running the go list command, as in the following example:

```go
go list -f '{{.Target}}'
```

Add the Go install directory to your system's shell path.

As an alternative, you can change the install target by setting the GOBIN variable using the go env command:

```go
go env -w GOBIN=/path/to/your/bin
```

Compile and install the package.

```go
go install github.com/dimanyfantakis/gofortune
```

## Usage

Run the application
```go
gofortune
```

Or Add `gofortune` to your `~/.bashrc` file.
If you don't want to get a fortune on every new terminal session but rather once per login then you can add this `bash` script to your `~/.bashrc` file.

```bash
remove_flag_file() {
    rm -f "$flag_file"
}

# Define the flag file path
flag_file="/tmp/.firstrun_$USER"

# If the flag file doesn't exist
if [ ! -f "$flag_file" ]; then
    # Execute the gofortune command
    gofortune

    # Create the flag file in /tmp
    touch "$flag_file"
fi

# Set a trap to remove the flag file upon logout
trap remove_flag_file EXIT
```