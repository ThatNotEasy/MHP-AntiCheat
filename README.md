# MHP AntiHack System

[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows-blue.svg)](https://windows.com)
[![Build Status](https://img.shields.io/badge/build-Visual%20Studio%202010-yellow.svg)]()

## Overview

MHP AntiHack is a comprehensive anti-cheat system designed specifically for MU Online game servers. This multi-layered security solution provides real-time detection and prevention of various hacking attempts, ensuring fair gameplay and protecting game integrity.

## Features

### 🔒 Multi-Layered Protection
- **Memory Protection** - Advanced memory scanning and dump detection
- **Process Monitoring** - Real-time process enumeration and validation
- **File Integrity** - CRC32 and MD5 verification of game files
- **Network Security** - Encrypted communications with anti-tampering
- **API Hooking Detection** - Unauthorized system API monitoring

### 🛡️ Detection Modules
- **DumpCheck** - Memory dump and debugging detection
- **ExecutableCheck** - Process executable validation
- **FileCheck** - Game file integrity verification
- **WindowCheck** - Unauthorized window detection
- **RegistryCheck** - Registry modification monitoring
- **ThreadCheck** - Thread integrity monitoring
- **MacroCheck** - Automation and macro detection

### 🚀 Advanced Features
- **Real-time Monitoring** - Continuous threat assessment
- **Encrypted Communications** - Secure client-server protocol
- **Self-Protection** - Anti-tampering mechanisms
- **VM Protection** - Themida-based code protection
- **Hardware Fingerprinting** - Unique system identification

## Architecture

### System Components

```
┌─────────────────────────────────────────────────────────┐
│                  MHP AntiHack System                    │
├─────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
│  │ HackServer  │  │ HackClient  │  │   Utilities     │  │
│  │             │  │             │  │                 │  │
│  │ • Real-time │  │ • Main DLL  │  │ • GetClientInfo │  │
│  │   monitoring│  │ • Detection │  │ • GetHackList   │  │
│  │ • List dist.│  │ • Reporting │  │ • GetHardwareId │  │
│  │ • Blacklist │  │ • Protection│  │ • Configuration │  │
│  └─────────────┘  └─────────────┘  └─────────────────┘  │
├─────────────────────────────────────────────────────────┤
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────────┐  │
│  │ HackDetect  │  │ HackVerify  │  │  Data Files     │  │
│  │             │  │             │  │                 │  │
│  │ • Detection │  │ • File      │  │ • Checksum.List │  │
│  │   engine    │  │   validation│  │ • Dump.List     │  │
│  │ • Core      │  │ • Integrity │  │ • Internal.List │  │
│  │   scanning  │  │   checks    │  │ • Window.List   │  │
│  └─────────────┘  └─────────────┘  └─────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

## Installation

### Prerequisites
- **Operating System**: Windows 7/8/10/11
- **Development Environment**: Visual Studio 2010 (for building)
- **Runtime Requirements**: Microsoft Visual C++ 2010 Redistributable

### Quick Setup

1. **Clone or extract the project files**
   ```bash
   # Extract to your desired directory
   MHP-AntiCheat/
   ```

2. **Configure server settings**
   - Edit `TOOLS/ClientInfo.ini` with your server details
   - Run `TOOLS/GetClientInfo.exe` to generate `Main.Info`

3. **Build the solution** (optional)
   ```bash
   # Open Source/AntiHackMU.sln in Visual Studio 2010
   # Build in Release mode for production use
   ```

4. **Deploy components**
   - Copy `MuClient/` files to your MU Online client directory
   - Copy `AntiHackServer/` files to your server directory
   - Copy `TOOLS/` utilities to your management system

## Configuration

### Server Configuration

Edit `AntiHackServer.ini`:
```ini
[ServerInfo]
ServerName=YourServerName
ServerPort=55901
MaxConnections=1000

[Database]
ChecksumList=Data/Checksum.List.db
DumpList=Data/Dump.List.db
InternalList=Data/Internal.List.db
WindowList=Data/Window.List.db

[Security]
EnableBlackList=1
EnableLogging=1
LogLevel=2
```

### Client Configuration

Edit `TOOLS/ClientInfo.ini`:
```ini
[ClientInfo]
CustomerName=YourServer
IpAddress=127.0.0.1
ServerPort=55901
ServerName=YourServerName
ClientName=main.exe
PluginName=HackDetect.dll
VerifyName=vProtect.dll
ClientVersion=1.0.0
ClientSerial=12345678901234567
```

## Building from Source

### Requirements
- Visual Studio 2010 with C++ support
- Windows SDK 7.1
- Microsoft Detours library

### Build Steps

1. **Open Solution**
   ```
   Source/AntiHackMU.sln
   ```

2. **Restore Dependencies**
   - Ensure all third-party libraries are present in `Source/Util/`
   - CryptoPP, Detours, and MAPM libraries must be available

3. **Build Order**
   ```bash
   # Build utilities first
   GetClientInfo
   GetHackList
   GetHardwareId

   # Build core components
   HackDetect
   HackVerify
   HackClient
   HackServer
   ```

4. **Output Directories**
   - `AntiHackServer/` - Server binaries
   - `MuClient/` - Client binaries
   - `TOOLS/` - Utility executables

## Usage

### Starting the Server

1. **Launch AntiHackServer**
   ```bash
   cd AntiHackServer
   AntiHackServer.exe
   ```

2. **Server Interface**
   - Real-time connection monitoring
   - Threat detection display
   - Configuration management menu
   - Blacklist management

### Client Integration

1. **Inject into MU Online**
   - Copy `MuClient/` files to game directory
   - Launch `zMuLauncher.exe` or inject `HackDetect.dll`

2. **Automatic Protection**
   - Client connects to AntiHackServer
   - Downloads latest detection lists
   - Begins real-time monitoring

### Utility Tools

#### GetClientInfo
Generates encrypted client configuration:
```bash
TOOLS/GetClientInfo.exe
# Creates Main.Info with encrypted settings
```

#### GetHardwareId
Generates hardware fingerprint:
```bash
TOOLS/GetHardwareId.exe
# Outputs unique system identifier
```

#### GetHackList
Builds detection databases:
```bash
TOOLS/GetHackList.exe
# Updates hack signatures and patterns
```

## Security Features

### Protection Mechanisms
- **VM Protection** - Themida-based code virtualization
- **Encrypted Communications** - All network traffic encrypted
- **Self-Integrity Checks** - Runtime code validation
- **Anti-Debugging** - Multiple debugger detection methods
- **Memory Encryption** - Sensitive data protection

### Detection Capabilities
- **Memory Scanning** - Signature-based memory detection
- **Process Validation** - Authorized process verification
- **File Monitoring** - Real-time file integrity checks
- **Network Analysis** - Suspicious network activity detection
- **System Hook Detection** - Unauthorized API hooking

## Troubleshooting

### Common Issues

**Server Connection Failed**
- Verify server IP and port configuration
- Check firewall settings
- Ensure AntiHackServer is running

**Client Injection Failed**
- Run as administrator
- Check for conflicting anti-virus software
- Verify game client compatibility

**Detection Lists Not Loading**
- Run GetClientInfo utility
- Check file permissions
- Verify database file integrity

### Debug Mode

Enable debug logging in `AntiHackServer.ini`:
```ini
[Debug]
EnableDebug=1
LogLevel=3
LogFile=Logs/debug.log
```

### Performance Optimization

**Server Performance**
- Adjust `MaxConnections` based on server capacity
- Monitor CPU usage in server interface
- Optimize detection list sizes

**Client Performance**
- Adjust scanning frequency in code
- Monitor memory usage
- Optimize thread priorities

## File Structure

```
MHP-AntiCheat/
├── README.md                    # This file
├── AntiHackServer/              # Server binaries and data
│   ├── AntiHackServer.exe       # Main server application
│   ├── HackDetect.dll          # Detection engine
│   ├── BlackList.txt           # Blocked IPs/users
│   └── Data/                   # Detection databases
├── MuClient/                   # Client binaries
│   ├── vMain.exe              # Protected main executable
│   ├── vProtect.dll           # Protection layer
│   ├── zMuLauncher.exe        # Secure launcher
│   └── zVerify.dll            # Verification DLL
├── Source/                     # Source code
│   ├── AntiHackMU.sln         # Visual Studio solution
│   ├── HackClient/            # Client DLL source
│   ├── HackServer/            # Server source
│   ├── Util/                  # Shared libraries
│   └── [Component sources...]
└── TOOLS/                      # Utility tools
    ├── GetClientInfo.exe      # Configuration generator
    ├── GetHardwareId.exe      # Hardware ID tool
    └── GenHackDump/           # Hack list generators
```

## API Reference

### Protocol Structures

#### Client Information Exchange
```cpp
struct SDHP_CLIENT_INFO_SEND {
    PBMSG_HEAD h;              // Protocol header
    char ClientVersion[8];     // Client version
    char ClientSerial[17];     // Unique client ID
    DWORD HardwareId;          // Hardware fingerprint
};
```

#### Detection Reports
```cpp
struct SDHP_CLIENT_DISCONNECT_SEND {
    PBMSG_HEAD h;              // Protocol header
    char Account[11];          // User account
    char Name[11];             // Character name
    int Type;                  // Disconnection reason
    char Text[100];            // Description
    DWORD ProcessId;           // Process identifier
};
```

## Contributing

### Development Guidelines
1. Follow existing code style and patterns
2. Test all changes thoroughly
3. Update documentation for new features
4. Ensure compatibility with MU Online versions

### Adding Detection Modules
1. Create new module in `Source/HackClient/HackClient/`
2. Implement scanning interface
3. Add to main detection cycle
4. Update server list management

## Version History

- **v1.0.0** - Initial release
  - Core anti-cheat functionality
  - Basic detection modules
  - Server-client architecture

## License

This software is proprietary and confidential. All rights reserved.

## Support

For technical support and questions:
- Review troubleshooting section
- Check server logs for detailed error information
- Verify all configuration files are properly generated

## Security Notice

This anti-cheat system provides comprehensive protection but should be used as part of a broader security strategy including:
- Regular game client updates
- Server-side validation
- Community moderation
- Network security measures

---

**MHP AntiHack System** - Advanced protection for MU Online gaming environments.