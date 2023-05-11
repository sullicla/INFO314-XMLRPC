# INFO314-XMLRPC

My XML-RPC assignment for INFO 314.

Instructions:

Fork the repository: https://github.com/tedneward/INFO314-XMLRPCLinks to an external site.

Read the instructions in the README.md file to create a Calculator app using the XML-RPC "standard".

 

## Rubric / Stories (10 pts)
# Server (5pts)
A basic scaffolded HTTP server (using the SparkJava project) is provided for you in the JavaServer directory. You are free to use this, or you can use a different project if you choose. Whatever you use, your HTTP endpoint must:

- listen on port 8080
- return a 404 for any URL other than "/RPC"
- return a 405 (Method Not Supported) for any operation other than POST
- the Host must reflect the hostname it is running on
Your XML-RPC endpoint must support five method names:

- add: it should take zero to any number of i4 parameters, returning one i4 result, adding the values together. add with 0 parameters should return 0; add with 1 parameter should return that original value. Otherwise, sum all the parameters.
- subtract: it should take two i4 parameters, returning one i4 result, subtracting the second from the first.
- multiply: it should take zero to any number of i4 parameters, returning one i4 result, multiplying the values together. multiply with 0 parameters should return 1; multiply with 1 parameter should return that original value. Otherwise, multiply all the parameters.
- divide: it should take two i4 parameters, returning one i4 result, dividing the first by the second. If the second parameter is a 0, return a faultCode of 1 and a faultString of "divide by zero".
- modulo: it should take two i4 parameters, returning one i4 result, doing the modulo (remainder) operation. If the second parameter is a 0, return a faultCode of 1 and a faultString of "divide by zero".
To be more clear about add and multiply, an add of 1, 2, 3, 4 should be 1 + 2 + 3 + 4, or 10, and a multiply of 1, 2, 3, 4 would be 1 * 2 * 3 * 4, or 24.

If anything than an i4 is passed to any of these endpoints, return a faultCode of 3 and a faultString of "illegal argument type".

 
### Client (3pts)
Your client must be a console application that takes command-line parameters like so:

java CalcClient localhost 8080

In other words, args[0] should be the server, and args[1] the port. The User-Agent header should be the name of your group.

 

The client then needs to exercise all five of the operations, like so:

- subtract(12, 6) = 6
- multiply(3, 4) = 12
- divide(10, 5) = 2
- modulo(10, 5) = 0
- add(0) = 0
- add(1, 2, 3, 4, 5) = 15
- multiply(1, 2, 3, 4, 5) = 120
In addition, the client should make sure the server responds with errors appropriately:

- add two very large numbers such that it triggers an overflow
- multiply two very large numbers and trigger an overflow
- subtract taking two string parameters should trigger illegal argument faults
- divide any number by 0 and trigger a divide-by-zero fault
 

### Interoperability (2pts)
In order to ensure that your use of XML-RPC is correct, you must demonstrate that your XML-RPC client can work against another person's XML-RPC server, and similarly that another (different) person's client can work against your server. In your project's README, document which other server you interop'ed against, and which client.

Client calling another server, 1 pt. Server called by another client, 1 pt.

### Extra Credit (5pts)
- Write a REST calculator server
- Create an entirely separate HTTP endpoint
- Same five calculator operations
- Same sort of error handling
 

### Submission
Submit the link to your forked repository.
