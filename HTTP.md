### Responses  
HTTP Responses are messages sent from the lient to ther server to ask for a resource or perform an action. A Response is made up of three main parts. 
1. A Request/Status Line
	This returns the HTTP Version number, which shows the HTTP Specification to which the server has tried to make a message comply. A status code or the three digit code you may be familiar with(200, or 404 i.e.) which represents the result of a request. A reason phrase, also known as a status text, which is a readable text that summarizes the meaning of the particular status code.
2. HTTP Headers
	The HTTp header for a servers's repsonse contain the infomration that a client can use to find out mre about hte response itself, and about thee server taht sent the response. This kind of information can be used to assist the client with displaying the response to a user with storing or caching the rtesponse for a future use case, and making furhter requesets to ther server now or in the future. In the case of unsuccesful request, headers cna be used to tell the client what ity must dfo to completre its request succesfully. Syntax typiclaly is contains a empty line after a series of Headers to divide them from the message. 
3. Message Body
	the message body of a response is referred to as a response body. The message bod uare used for most requests. Exceptions code be when a server is respondng to a client request that used the HEAD, a method that only returns the HEADERS and not the response body. or when a server may only be using certain status codes.
	For a response to a sucessful request, the message body contains either the resource requested b the client, or some information about hte status of teh acton requested by teh cleint. For some responeto ao an unsucsseful request, or for an action that he client needs to to take to complete a sucessful request. 


Refrences 
https://www.ibm.com/docs/en/cics-ts/6.x?topic=protocol-http-responses
