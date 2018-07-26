# FTP File Server via Socket Programming in Python

This is a file server written in Python 2.7, which makes use of Python's socket module. It enables the transfer of any file type.

All the packages used in this implementation are included in the standard library.

### Usage

To run the server/client, call the appropriate program from the terminal. Each program will display a short message on startup:
```
> python server.py

Welcome to the FTP server.

To get started, connect a client.
```
```
> python client.py

Welcome to the FTP client.

Call one of the following functions:
CONN           : Connect to server
UPLD file_path : Upload file
LIST           : List files
DWLD file_path : Download file
DELF file_path : Delete file
QUIT           : Exit

Enter a command:
```
As indicated, the first thing that needs to be done is to connect the client to the server. To do this, just enter the command CONN:
```
Enter a command: CONN
```
The client will then attempt a connection. If successful a message will appear:
```
Enter a command: Connect

Sending a server request...
Connection successful
```
After that, all other commands can be entered through the client. Messages will display the progress of the request on both the client and server end. For example, to upload a file 'my_file.mp4', use the following command:
```
Enter a command: UPLD my_file.mp4
```
All standard file paths also work:
```
Enter a command: UPLD C:\Users\...\folder\my_file.mp4
```

When the server receives a file, it puts it in the same folder that it is in. Likewise, when the LIST command is used the server searches for files in the same folder that it is located in.

### Notes

- This code is quite well documented, so hopefully it's all understandable, even if my code isn't of the highest quality.
- There is some exception handling, but it's very generic. It gets the job done, but more specific handling would give better error diagnostics.
- Make sure that you quit the client properly, i.e. with the command QUIT. Otherwise, if the client is restarted without also restarting the server, attempting to establish a server will fail.
- This implementation isn't the most efficient when it comes to sending amount sent. There is a lot of auxiliary sending of strings. This was done just to get the program working. If you want to contribute a fix to this that makes sure the client and server don't get out of sync, feel free!
