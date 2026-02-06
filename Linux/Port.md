nc -l -v -k -p 1433

|Option|Description|
|---|---|
|`-l`|Listen mode. Sets up a listening socket.|
|`-p`|Local port. Specifies the target port number to connect to.|
|`-u`|UDP mode. Enables UDP instead of TCP.|
|`-z`|Zero-I/O mode. Scans and detects open ports on the target host.|
|`-v`|Verbose mode. Provides detailed command output.|
|`-w`|Timeout. Sets a timeout value for connections.|
|`-e`|Execute. Runs a specified command after establishing a connection.|
|`-n`|Numeric-only mode. Disables DNS resolution.|
|`-k`|Keep open. Keeps the connection open when the client disconnects.|
|`-c`|Shell command. Executes a command as a single argument to the shell.|

Then you can run telnet or curl telnet:// command to test the connection