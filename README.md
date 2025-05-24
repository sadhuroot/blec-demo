<div align="center">

# BLEC - Bluetooth Low Energy Command & Control Framework

[![Swift](https://img.shields.io/badge/Swift-5.9-orange.svg?style=flat-square)](https://swift.org)
[![Platform](https://img.shields.io/badge/Platform-macOS%20|%20Linux%20|%20Windows-blue.svg?style=flat-square)](https://github.com/yourusername/BLEC)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
[![Version](https://img.shields.io/badge/Version-1.0.0-brightgreen.svg?style=flat-square)](https://github.com/yourusername/BLEC/releases)
[![Security](https://img.shields.io/badge/Security-Research-red.svg?style=flat-square)](docs/SECURITY.md)

![image](https://github.com/user-attachments/assets/32e7b1c0-8910-46c0-ba04-6dfb1462ca6d)


**Advanced BLE Security Research & Penetration Testing Framework**

[Features](#-features) • [Hardware](#-hardware-testing) • 

</div>

---

## 🎯 Overview

BLEC is a cutting-edge Bluetooth Low Energy (BLE) Command & Control framework designed for security researchers, penetration testers, and IoT security professionals. Built with Swift, it provides a comprehensive suite of tools for BLE device analysis, vulnerability research, cross-platform agent deployment, and covert operations management.

### 🌟 Why BLEC?

- **Multi-Platform Support**: Deploy agents on Linux, Windows, and macOS
- **Advanced BLE Capabilities**: Support for Bluetooth 5.3 with PHY modes (1M, 2M, Coded)
- **Security Research Tools**: Built-in CVE hunting and vulnerability analysis
- **Stealth Operations**: Encrypted C2 channels with configurable beaconing
- **Modern Architecture**: Built with Swift for performance and safety
- **Air-Gapped C2**: Full reverse shell capabilities over BLE without internet connectivity

## 🚀 Features

### Core Modules

<table>
<tr>
<td width="50%">

#### 🔍 BLE Scanner
- **Multi-PHY Support**: 1M, 2M, and Coded PHY modes
- **Real-time RSSI Monitoring**: Signal strength visualization
- **Service Discovery**: GATT services and characteristics enumeration
- **Packet Capture**: Export to PCAP format
- **Device Fingerprinting**: Identify device types and capabilities

</td>
<td width="50%">

#### 🚀 Agent Builder
- **Cross-Platform**: Linux (x86_64, ARM64), Windows, macOS
- **Binary Optimization**: Strip symbols, UPX compression
- **Persistence**: Systemd, Windows Services, LaunchDaemons
- **Anti-Analysis**: String obfuscation, anti-debugging
- **Custom Payloads**: Extensible plugin architecture

</td>
</tr>
<tr>
<td width="50%">

#### 🐛 CVE Hunter
- **BT5 Packet Analysis**: Identify protocol violations
- **Fuzzing Engine**: Template-based and generational fuzzing
- **Known Vulnerabilities**: KNOB, BIAS, BlueFrag detection
- **Automated Reporting**: Generate CVE-ready reports
- **PoC Generation**: Automatic exploit code creation

</td>
<td width="50%">

#### 🔒 Network Tunneling
- **SSH Forwarding**: Local and remote port forwarding
- **SOCKS5 Proxy**: Dynamic application-level gateway
- **Multi-Hop**: Chain multiple proxies
- **Traffic Analysis**: Monitor bandwidth and connections
- **Auto-Reconnect**: Maintain persistent tunnels

</td>
</tr>
</table>

### Security Features

- **🔐 Encryption**: AES-256-GCM for C2 channels, ChaCha20-Poly1305 optional
- **🔑 Authentication**: Ed25519 signatures, certificate pinning
- **🛡️ Stealth**: Configurable beacon intervals, traffic shaping
- **🔍 Anti-Forensics**: Log sanitization, process hiding
- **📊 Monitoring**: Real-time agent status, health checks
- **📡 Air-Gapped Operations**: Full C2 capabilities over BLE-only connections

## 🔬 Hardware Testing

BLEC has been extensively tested with custom firmware devices to ensure compatibility and demonstrate advanced capabilities. Our testing infrastructure showcases real-world attack scenarios and defensive research.

### Development & Testing Infrastructure

<table>
<tr>
<th>Device</th>
<th>Role</th>
<th>Configuration</th>
<th>Purpose</th>
</tr>
<tr>
<td><strong>nRF5340 DK</strong><br>(Development Kit)</td>
<td>🛠️ Primary Development Platform</td>
<td>• Dual-core architecture<br>• Zephyr RTOS<br>• Custom firmware development</td>
<td>• Main development board<br>• Firmware testing & debugging<br>• Protocol implementation<br>• Flash other devices</td>
</tr>
<tr>
<td><strong>nRF52840-MDK #1</strong></td>
<td>📡 Central (Coded PHY)</td>
<td>• Central mode<br>• Coded PHY (Long Range)<br>• Custom C2 firmware</td>
<td>• C2 relay node<br>• Long-range communication<br>• Command forwarding</td>
</tr>
<tr>
<td><strong>nRF52840-MDK #2</strong></td>
<td>🎯 Peripheral (Coded PHY)</td>
<td>• Peripheral mode<br>• Coded PHY (Long Range)<br>• Agent firmware</td>
<td>• Remote agent<br>• Receives commands<br>• Executes payloads</td>
</tr>
<tr>
<td><strong>nRF52840 Dongle</strong><br>(PCA10059)</td>
<td>🔍 Sniffer (2M PHY)</td>
<td>• Monitor mode<br>• 2M PHY<br>• Wireshark integration</td>
<td>• Packet capture<br>• Protocol analysis<br>• Real-time monitoring</td>
</tr>
<tr>
<td><strong>WCH BLE Analyzer</strong></td>
<td>📻 Multi-Channel Scanner</td>
<td>• Channels 37, 38, 39<br>• Coded PHY<br>• Simultaneous capture</td>
<td>• Advertisement scanning<br>• Channel hopping analysis<br>• PHY layer debugging</td>
</tr>
<tr>
<td><strong>Ubertooth One</strong></td>
<td>🛡️ Security Analysis</td>
<td>• Full spectrum<br>• Raw packet access<br>• Custom firmware</td>
<td>• Additional analysis<br>• Security research<br>• Protocol fuzzing</td>
</tr>
<tr>
<td><strong>Raspberry Pi 5</strong></td>
<td>🎯 Target/Victim</td>
<td>• Ubuntu 23.10<br>• BLEC Agent installed<br>• No internet connection</td>
<td>• Demonstrates persistence<br>• Air-gapped C2<br>• Real-world scenario</td>
</tr>
<tr>
<td><strong>MacBook Pro M Series</strong></td>
<td>🏢 C2 Server</td>
<td>• BLEC Framework<br>• Command center<br>• Multi-device control</td>
<td>• Primary C2 server<br>• Agent management<br>• Real-time monitoring</td>
</tr>
</table>

### Attack Scenario: Air-Gapped Raspberry Pi Compromise

```
┌─────────────────────────────────────────────────────────────────┐
│                        ATTACK SCENARIO                           │
│              Air-Gapped Raspberry Pi 5 Compromise               │
└─────────────────────────────────────────────────────────────────┘

                    ┌─────────────────┐
                    │   MacBook M     │
                    │  (C2 Server)    │
                    │                 │
                    │ ┌─────────────┐ │
                    │ │    BLEC     │ │
                    │ │  Framework  │ │
                    │ └──────┬──────┘ │
                    └────────┼────────┘
                             │ Commands
                             ▼
                    ┌─────────────────┐
                    │  nRF52840-MDK   │
                    │   (Central)     │
                    │  Coded PHY LR   │◄─── Long Range
                    └────────┬────────┘     ~1km+
                             │
                 ╔═══════════▼═══════════╗
                 ║   BLE Coded PHY       ║
                 ║  Encrypted Channel    ║
                 ╚═══════════┬═══════════╝
                             │
                    ┌────────▼────────┐
                    │  nRF52840-MDK   │
                    │  (Peripheral)   │
                    │  Coded PHY LR   │
                    └────────┬────────┘
                             │ Relay
                             ▼
                    ┌─────────────────┐
                    │ Raspberry Pi 5  │
                    │   (Target)      │
                    │ ┌─────────────┐ │
                    │ │ BLEC Agent  │ │     ❌ No Internet
                    │ │  (Active)   │ │     ✅ BLE Only
                    │ └─────────────┘ │     🔄 Persistent
                    │                 │
                    │ "Air-Gapped"    │
                    └─────────────────┘

     ┌─────────────────────────────────────────────────┐
     │              MONITORING LAYER                    │
     ├─────────────────┬─────────────────┬─────────────┤
     │  nRF52840       │ WCH Analyzer   │ Ubertooth   │
     │  PCA10059       │                │    One      │
     │ (2M PHY Sniff)  │ (3-CH Coded)   │ (Analysis)  │
     └─────────────────┴─────────────────┴─────────────┘
```



### Technical Implementation Details

#### nRF5340 DK - Development Platform
```c
// Main development board configuration
// Used for developing and testing all firmware
typedef struct {
    nrf5340_network_core_t net_core;  // Handles BLE stack
    nrf5340_app_core_t app_core;      // Handles application logic
    ble_config_t config;
} dev_platform_t;

// Flash other devices from nRF5340
nrfjprog --family NRF53 --program agent.hex --chiperase --verify
```

#### Coded PHY Configuration
```c
// nRF52840-MDK Central configuration
ble_gap_phys_t const phys = {
    .tx_phys = BLE_GAP_PHY_CODED,
    .rx_phys = BLE_GAP_PHY_CODED,
};

// Extended range parameters
ble_gap_opt_t gap_opt;
gap_opt.preferred_phys.tx_phys = BLE_GAP_PHY_CODED;
gap_opt.preferred_phys.rx_phys = BLE_GAP_PHY_CODED;
```



### Security Implications

This setup demonstrates:

1. **📡 Long-Range BLE C2**: Coded PHY enables communication up to 1km+
2. **🔒 Air-Gap Bypass**: Complete C2 functionality without network connectivity
3. **🔄 Persistence**: Agent survives reboots and maintains BLE beacon
4. **📊 Multi-Layer Monitoring**: Comprehensive packet analysis across all PHY modes
5. **🛠️ Rapid Development**: nRF5340 DK enables quick firmware iteration

### Performance Metrics

<table>
<tr>
<th>Metric</th>
<th>1M PHY</th>
<th>2M PHY</th>
<th>Coded PHY (S=8)</th>
</tr>
<tr>
<td>Range</td>
<td>~100m</td>
<td>~50m</td>
<td>~1000m+</td>
</tr>
<tr>
<td>Data Rate</td>
<td>1 Mbps</td>
<td>2 Mbps</td>
<td>125 kbps</td>
</tr>
<tr>
<td>Power Usage</td>
<td>Medium</td>
<td>High</td>
<td>Low</td>
</tr>
<tr>
<td>C2 Latency</td>
<td>~50ms</td>
<td>~25ms</td>
<td>~200ms</td>
</tr>
</table>



### Interactive Mode

<img width="1493" alt="Screenshot 2025-05-22 at 16 35 48" src="https://github.com/user-attachments/assets/fcffc9c0-911f-43c5-af11-8e8d023dda29" />

**C2 Operations Menu:**
1. **Deploy Master/Controller (Real-time)** - Launch central command node
2. **Deploy Slave/Implant (Real-time)** - Deploy peripheral agent
3. **Advanced Auto-switch Mode** - Dynamic role switching
4. **Stealth Beacon Broadcast** - Covert BLE advertising
5. **BLE Scanner (Device Discovery)** - Scan for nearby devices

**Agent Management:**
6. **Deploy New Implant** - Build and deploy new agents
7. **View Connected Agents** - Monitor active connections
8. **Agent Shell Access** - Direct command execution

**System Options:**
9. **Configuration & Settings** - Framework configuration
10. **View Connection Logs** - Activity monitoring
11. **Help / Documentation** - Built-in help system
12. **Exit** - Safely terminate framework


#### Main Menu: C2 Dashboard

<img width="1525" alt="Screenshot 2025-05-22 at 16 39 08" src="https://github.com/user-attachments/assets/486a1832-9808-41b4-bb87-3e7c8396edd5" />


The main C2 dashboard provides a comprehensive overview of the BLEC framework's operational status:

**Visual Elements:**

  - **Mode**: Current operational state (Active/Inactive)
  - **Agents**: Total agent count and active connections
  - **Local IP**: C2 server IP address
  - **Timestamp**: Current date and time

**Active Connections Panel:**
- Live list of connected agents with:
  - Agent names and identifiers
  - Connection status indicators
  - IP addresses and connection timestamps



#### BLE Device Discovery

<img width="1481" alt="Screenshot 2025-05-22 at 16 14 22" src="https://github.com/user-attachments/assets/e72c2e5e-9080-413f-bbc8-e8e61defeabf" />


The BLE Scanner module provides comprehensive device discovery capabilities:

**Discovery Process:**
- **Real-time Scanning**: Continuously discovers BLE devices in range



**Discovered Devices Display:**
- **Device List**: Shows all discovered BLE devices with:
  - Device name (or "Unknown" if not advertised)
  - UUID address
  - RSSI signal strength with color coding:
    - 🟢 Green: Excellent signal (-50 dBm or better)
    - 🟡 Yellow: Good signal (-70 to -50 dBm)
    - 🟣 Purple: Fair signal (-85 to -70 dBm)
    - 🔴 Red: Poor signal (below -85 dBm)
  - Supported PHY modes
  - Advertisement data



**Device Categories Identified:**
- **🛠️ Development Boards**: nRF52840, ESP32,  - Used for custom firmware
- **📱 Mobile Devices**: iPhones, Android phones - Potential targets
- **🎧 Audio Devices**: AirPods, Sony headphones - Often vulnerable
- **⌚ Wearables**: Fitness trackers, smartwatches - Health data exposure
- **🏠 IoT Devices**: Smart locks, doorbells - Critical security implications
- **💻 Computers**: MacBooks, tablets - High-value targets
- **🔑 Trackers**: Tile, AirTags - Location privacy concerns

**Interactive Features:**
- **Connect to Device**: Select any discovered device for connection
- **Service Enumeration**: Automatically enumerate GATT services
- **Export Results**: Save scan results in JSON format
- **Continuous Monitoring**: Real-time updates as devices appear/disappear

**Advanced Capabilities:**
- **Extended Advertisement**: Detects Bluetooth 5.0+ extended advertising
- **Manufacturer Data**: Decodes manufacturer-specific data
- **Service UUIDs**: Lists advertised services
- **TX Power**: Shows transmit power levels when available


**Configuration Management:**
```
Current Configuration for nRF52840-MDK Central
════════════════════════════════════════

C2 Server: 10.222.20.205:8443
Beacon Interval: 60 seconds
Encryption: AES-256-GCM
Persistence: Enabled
PHY Modes: 1M, 2M, Coded

Change settings:
1. C2 Server
2. Beacon Interval
3. Encryption
4. Persistence
5. PHY Modes
0. Back to main menu

Select setting to change: _
```


**Encryption Key Rotation:**
```
Rotate Encryption Keys
════════════════════════════════════════

Current Key: [********************]
New Key: [********************]

Key rotation process:
1. Generate new key pair
2. Distribute public key to all agents
3. Instruct agents to rotate keys
4. Confirm key rotation status

Start key rotation? [Y/n]: Y

[*] Generating new key pair...
[*] Distributing public key...
[*] Instructing agents to rotate keys...
[*] Confirming key rotation status...

✅ Key rotation completed successfully!
```



### Logging & Monitoring

<img width="1547" alt="Screenshot 2025-05-22 at 16 43 20" src="https://github.com/user-attachments/assets/ed3c0c10-07b6-4c59-80ac-fc8775803cf0" />


The Diagnostics module provides tools for monitoring and troubleshooting the BLEC framework:

**Logging Features:**
- **Real-time Logs**: View logs as they are generated
- **Log Levels**: Set log verbosity (Error, Warning, Info, Debug)
- **Log Rotation**: Automatic log file rotation and compression
- **Remote Logging**: Send logs to a remote syslog server

**Monitoring Features:**
- **Agent Status**: Real-time status of all agents
- **Resource Usage**: Monitor CPU, memory, and network usage
- **Connection History**: View past connections and data transfer
- **Error Rates**: Monitor for abnormal error rates or failures





## 📊 Architecture

```
┌─────────────────────────────────────────────────────┐
│                   CLI Layer                         │
│         (Interactive UI, Command Processing)        │
└─────────────────────┬───────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────┐
│                 BLECCore Layer                      │
│        (Business Logic, Service Orchestration)      │
├─────────────────────────────────────────────────────┤
│ BLE Scanner │ Agent Builder │ C2 Server │ CVE Hunter│
│ Net Tunnels │ Configuration │ Diagnostics │ Crypto  │
└─────────────────────┬───────────────────────────────┘
                      │
┌─────────────────────▼───────────────────────────────┐
│                Platform Layer                       │
│        (CoreBluetooth, Network, FileSystem          │
└─────────────────────────────────────────────────────┘
```

### Component Details

- **CLI Layer**: User interface, command parsing, output formatting
- **BLECCore**: Core services, business logic, data models
- **Platform Layer**: OS-specific implementations, hardware access


### Security Features

1. **Encrypted Communications**
   - AES-256-GCM for C2 channels
   - TLS 1.3 for network connections
   - Ed25519 for authentication

2. **Operational Security**
   - Configurable beacon intervals
   - Traffic shaping to mimic legitimate BLE
   - Process name randomization

3. **Data Protection**
   - Automatic log sanitization
   - Secure credential storage
   - Memory-safe Swift implementation



## 🚀 Agent Deployment Workflow

### Step 1: Building the Agent Binary

<img width="1389" alt="Screenshot 2025-05-22 at 16 33 46" src="https://github.com/user-attachments/assets/1df099f6-d15e-41a1-94dc-61398cf7ca50" />


The agent building process creates a custom binary for the target system:


### Step 2: Uploading Agent to Target

<img width="1493" alt="Screenshot 2025-05-22 at 16 35 42" src="https://github.com/user-attachments/assets/9a7fe821-88a3-485e-b777-883ae8026535" />


Deploy the built agent to the target system:



### Step 3: Executing Commands on Target

<img width="1547" alt="Screenshot 2025-05-22 at 16 41 37" src="https://github.com/user-attachments/assets/c1419f38-a385-4e79-a043-8a6460a29c16" />




The complete workflow from building to command execution:

```
┌─────────────────────┐
│   1. BUILD AGENT    │
│                     │
│ $ blec agent build  │
│   --os linux        │
│   --arch arm64      │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  2. DEPLOY AGENT    │
│                     │
│ $ blec agent deploy │
│   --target IP       │
│   --user pi         │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│ 3. EXECUTE COMMANDS │
│                     │
│ $ blec agent        │
│   interact          │
│   rpi5-agent        │
└─────────────────────┘
```
