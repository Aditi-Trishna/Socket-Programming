# Socket-Programming
A socket is one endpoint of a two way communication link between two programs running on the network (commonly known for client and server interaction). It is bound to have a port number so that TCP layer can indentify the destination of the data.
Key Components

· Socket: An endpoint for communication, defined by an IP address and a port number.

· Server: Listens for incoming connections on a specific port.

· Client: Initiates a connection to a server on a specific port.

Basic Steps Involved

1. Create a Socket:

· Use the socket() function to create a socket.

· Specify the address family (e.g., AF_INET for IPv4), socket type (e.g., SOCK_STREAM for TCP), and protocol (usually 0 for default).

2. Bind (Server Only):

· Associate the socket with a specific address and port using the bind() function.

3. Listen (Server Only):

· Indicate that the socket is ready to accept connections using the listen() function.

4. Accept (Server Only):

· Accept an incoming connection from a client using the accept() function.

5. Connect (Client Only):

· Establish a connection to the server using the connect() function.

6. Send/Receive Data:

· Use functions like send() and recv() to exchange data between the client and server.

7. Close the Socket:

· Close the socket using the close() function when communication is complete.

Socket Types

· TCP (Transmission Control Protocol): Reliable, connection-oriented protocol.

· UDP (User Datagram Protocol): Unreliable, connectionless protocol.









TCP is used in the following project to make connection betwen clients and server.



There are 3 components i.e Utility, Server, Client. Each component wil have 3 files:

- .h files for function declaration.

- .cpp file for fucntion definition and logical operations.

- main.cpp file for executing the code.


These are the following files and steps involved in the making the connection:



Utilities.Cpp

Header Files:

#include<iostream>

#include <cstring>

#include <netinet/in.h>

#include <arpa/inet.h>


Purpose: Provides utility functions for network programming.

Functions:

createIPv4Address

· Purpose: Creates a sockaddr_in structure representing an IPv4 address.

· Parameters:

· const char *ip: The IP address as a string. An empty string indicates INADDR_ANY.

· int port: The port number.

· Returns: A pointer to the newly created sockaddr_in structure.

· Throws: std::invalid_argument if the IP address or port is invalid.

createTCPIpv4Socket

· Purpose: Creates a TCP/IPv4 socket.

· Returns: The file descriptor of the created socket.

· Throws: std::runtime_error if an error occurs while creating the socket.











Server.cpp


File:

#include <iostream>

#include <unistd.h>

#include <thread>

#include <sstream>

#include <cstring>

#include "../NetworkUtilities/Utitlies.h"


Purpose: Implements a basic echo server that accepts incoming connections and broadcasts messages to all connected clients.

Classes:

ServerError

· Purpose: Represents an error that occurred within the server.

Functions:

startAcceptingIncomingConnections

· Purpose: Continuously accepts incoming connections and spawns threads to handle them.

· Parameters:

· int serverSocketFD: The file descriptor of the server socket.

receiveAndPrintIncomingData

· Purpose: Receives data from a client socket and broadcasts it to all connected clients.

· Parameters:

· int socketFD: The file descriptor of the client socket.

acceptIncomingConnection

· Purpose: Accepts an incoming connection and creates an AcceptedSocket structure.

· Parameters:

· int serverSocketFD: The file descriptor of the server socket.

· Returns: A pointer to the newly created AcceptedSocket structure.






Client.cpp

Header Files:

#include <iostream>

#include <unistd.h>

#include <thread>

#include <sstream>

#include <cstring>

#include "../NetworkUtilities/Utitlies.h"


Purpose: Implements a basic chat client that connects to a server and allows users to send and receive messages.

Functions:

readConsoleEntriesAndSendToServer

· Purpose: Reads console input and sends it to the server.

· Parameters:

· int socketFD: The file descriptor of the socket connected to the server.

startListeningAndPrintMessagesOnNewThread

· Purpose: Starts a new thread to listen for incoming messages.

· Parameters:

· int socketFD: The file descriptor of the socket connected to the server.

listenAndPrint

· Purpose: Listens for incoming messages and prints them to the console.

· Parameters:

· int socketFD: The file descriptor of the socket connected to the server.


Brief Overview/ Conclusion:


This documentation provides a comprehensive overview of the codebase, including the Utilities.cpp Server.cpp Client.cpp files. It outlines the purpose of each file, describes the functions and their parameters, and provides essential information for understanding the code's functionality.

While this documentation serves as a foundational guide, it's important to note that additional details, such as specific error handling mechanisms, code examples, and architectural overviews, can further enhance its value.
