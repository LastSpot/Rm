# Network Client for Statistical Operations

This project implements a network client that connects to a server and performs statistical operations (minimum, maximum, and median) on sets of numbers. The client communicates with the server using a simple text-based protocol.

## Project Description

The client establishes a TCP connection with a server and processes numerical data based on server requests. It supports three main operations:
- Finding the minimum value in a set of numbers
- Finding the maximum value in a set of numbers
- Calculating the median value in a set of numbers

The client follows a specific protocol:
1. Connects to the server using provided connection details
2. Sends an initial greeting message
3. Processes server requests for statistical operations
4. Responds with calculated results
5. Continues until receiving a termination message

## Requirements

- GCC compiler
- UNIX-like operating system (Linux/macOS)
- Basic network connectivity

## Building the Project

To build the project, simply use the provided Makefile:

```bash
make
```

This will compile the source code and create the executable named `client`.

## Usage

To run the client, use the following command format:

```bash
./client <options> <port> <server_ip>
```

Where:
- `<options>`: Any additional command line options
- `<port>`: The port number to connect to
- `<server_ip>`: The IP address of the server

## Protocol Description

The client implements the following protocol:

1. Initial Connection:
   - Sends: `cs230 HELLO male@umass.edu`
   
2. Processing Loop:
   - Receives: `cs230 STATUS <operation> <num1> <num2> <num3> <num4> <num5>`
   - Where `<operation>` can be:
     - `min`: Find minimum value
     - `max`: Find maximum value
     - `median`: Find median value
   - Responds with: `cs230 <result>`

3. Termination:
   - Receives: `cs230 <status> BYE`
   - Closes connection

## Implementation Details

The client implements three main statistical functions:
- `min()`: Finds the minimum value in an array of 5 numbers
- `max()`: Finds the maximum value in an array of 5 numbers
- `median()`: Calculates the median value in an array of 5 numbers

The program uses standard C socket programming libraries for network communication and includes error handling for socket operations.

## Error Handling

The client includes basic error handling for:
- Socket creation failures
- Invalid addresses
- Connection failures

## Building and Development

The project uses a simple Makefile for compilation. The source code is written in C and follows standard C programming practices. 