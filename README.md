
This project involves the development of an telnet honeypot that simulates an SSH environment while facilitating client connections through Telnet. The honeypot captures unauthorized access attempts and logs relevant activities to enhance understanding of attacker behaviors.

## Objectives
- Simulate an SSH environment using Telnet for client connections.
- Log all interactions and commands executed by clients.
- Implement security measures to block IP addresses attempting unauthorized access.
- Store logs in a SQLite database for further analysis.

## Technologies Used
- **Programming Language**: C++
- **Database Management**: SQLite
- **Networking**: TCP/IP, Telnet
- **Logging**: Custom logger class for capturing activities

## System Design
### Architecture
The system comprises the following components:
1. **Server**: Listens for incoming Telnet connections and manages client sessions.
2. **Shell**: Mimics an SSH shell environment, handling user commands.
3. **Logger**: Captures and stores log messages into a text file and a SQLite database.
4. **Database**: Stores messages and logs for future analysis.

### Class Structure
- **BaseShell**: An abstract class providing a blueprint for derived shell classes.
- **Shell**: Inherits from `BaseShell` and implements the SSH-like behavior.
- **Logger**: Singleton class for logging messages to both a log file and a database.
- **Server**: Accepts client connections and delegates handling to `Shell`.

## Implementation Details
### Class Definitions
- **BaseShell**: Abstract class defining the shell interface.
- **Shell**: Implements the SSH-like environment for client interactions.
- **Logger**: Manages logging functionality, storing logs in both a text file and a SQLite database.
- **Server**: Manages incoming connections and handles client sessions.

### Main Functionality
- The server listens on a specified port (e.g., 2222) and accepts incoming Telnet connections.
- Upon client connection, a `Shell` instance is created to handle communication.
- The `run` method of `Shell` simulates an SSH environment, prompting for login and password, and handling commands like `ls`, `whoami`, and `cat`.
- Unauthorized access attempts trigger IP blocking, and all interactions are logged.

### Database Interaction
Logs are stored in a SQLite database using the following structure:
- **Messages Table**: Stores unique log messages.
- **Logs Table**: References messages by ID and timestamps.

## Results

- The honeypot successfully simulates an SSH environment using Telnet.

- It captures and logs all client interactions, allowing for analysis of attacker behavior.

- The system effectively blocks IPs that attempt to access sensitive files, enhancing security.

