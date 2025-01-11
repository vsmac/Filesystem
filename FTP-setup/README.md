# What is FTP?
  FTP stands for File Transfer Protocol, a standard network protocol used for transferring files between a client and a server over a network. FTP is commonly used to upload or download files from a server, manage website content, or share files in an organization.

Here’s a detailed explanation of FTP:
1. How FTP Works

FTP operates using a client-server model. The process involves two main components:

    FTP Client: A software application used by the user to connect to the FTP server.
    FTP Server: A server that stores the files and provides access to clients.

Steps of an FTP Transfer:

    The client connects to the server using FTP credentials (username and password).
    The client can then upload, download, delete, rename, or view files stored on the server.
    Data transfer can occur in two modes:
        Active Mode: The client opens a random port and waits for the server to connect.
        Passive Mode: The server opens a random port, and the client initiates the connection, often used to bypass firewalls.

2. Components of FTP

    Control Connection: Handles commands and responses between the client and server.
    Data Connection: Handles the actual transfer of files.

3. Common Commands in FTP

Some typical FTP commands include:

    USER: Provide a username for authentication.
    PASS: Provide a password for authentication.
    PUT: Upload a file to the server.
    GET: Download a file from the server.
    DELETE: Remove a file on the server.
    LIST: List files and directories on the server.

4. FTP Modes

FTP supports two primary modes of data transfer:

    ASCII Mode: Used for text files; converts line endings between systems.
    Binary Mode: Used for binary files (e.g., images, videos); ensures data integrity without alteration.

5. FTP Protocol Architecture

FTP typically uses two ports:

    Port 21: For the control connection (commands and responses).
    Port 20: For data transfer in active mode.

6. Security Concerns

Traditional FTP transfers data, including login credentials, in plain text, making it insecure. Modern secure alternatives include:

    SFTP (Secure FTP): Uses SSH for encryption.
    FTPS (FTP Secure): Adds SSL/TLS encryption to traditional FTP.

7. Common Use Cases

    Web Development: Uploading files to web servers.
    File Sharing: Sharing files between teams or organizations.
    Backup Systems: Moving backups to remote servers.

8. FTP Clients

Popular FTP clients include:

    FileZilla
    WinSCP
    Cyberduck


Default Ports for ftp

   1. Port 21 (Control Port): Used for sending commands from the client to the server and receiving server responses.
   2. Port 20 (Data Port): Used for transferring files in Active Mode.


                      # FTP INSTALLATION #

# Updates the package list to ensure you have the latest versions available.
sudo apt update 

# Installs the vsftpd package.
sudo apt install vsftpd  # Installs the vsftpd package.

# Starts the vsftpd service immediately.
sudo systemctl start vsftpd  

# Enables the service to start automatically when the system boots.
sudo systemctl enable vsftpd 

# Checks the status of the service (running, stopped, or any errors).
sudo systemctl status vsftpd 
     
      
      • Configure vsftpd

# Edit the configuration file to allow local users to upload and manage files:
    sudo vim /etc/vsftpd.conf
 
# Allows local system users (those with a valid username and password) to log in to the FTP server. 
  local_enable=YES
# Enables write permissions, allowing users to upload files or modify existing files.   
  write_enable=YES

     •  Create a User for FTP Access

# Restart the vsftpd service to apply the changes:
  sudo adduser username

  • Connect to the FTP Server

# Use the ftp command to connect to your FTP server
    ftp your-server-ip

   • Test FTP Operations

After logging in, you can use FTP commands to navigate and manage files. Some useful FTP commands include:

    ls:           # List files on the server.
    get filename: # Download a file from the server.
    put filename: # Upload a file to the server.
    bye:          # Exit the FTP session.

