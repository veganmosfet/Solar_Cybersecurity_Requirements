# Solar_Cybersecurity_Requirements
This is a collection of cybersecurity requirements for connected grid tie solar inverters.

## Scope, Applicability and Definitions

These requirements apply for solar power plants consisting of:
* The solar inverter
* The gateway. This device - which may be included in the inverter - is the bridge between the cloud (via the home router) and the inverter.
* The cloud platform accessible via a web client or an app. App security is out of scope. Note that testing the cloud plattform is only partly possible, so that not all requirements can be fully tested.

Block diagram here.

Notes:
* *must* or *shall* are used for mandatory positiv requirements.
* *must not* is used for mandatory negativ requirements.


## Gateway & Inverter

Note: the word *device* is used here for gateway and/or inverter.

### Secure Communication

1. Communication between gateway and cloud shall be protected by TLS version >= 1.2. with enforced mutual authentication.
2. Individual client certificates shall be used on the gateway side.
3. The gateway private key shall be protected (confidentiality) inside the device. This can be done either with an separate secure element or an internal secure enclave inside the processor system.
4. The Root CA of the cloud platform used for server authentication shall be protected (integrity) inside the device. 
5. If a WiFi access point is used for device parametrization, it shall implement WPA3 security with **individual** initial password protection.
6. It shall be possible to switch off the Access Point. 
7. If any other wireless communication is used (e.g. Bluetooth), state of the art security shall be implemented.
8. The device must not implement proprietary wireless communication. 

### Authentication and Authorization

1. Accessing or changing **any** device data or parameters shall be protected by a user-password (this applies both for local and remote access).
2. Initial Passwords shall be individual.
3. The user shall be prompted to change the initial password.
4. Password minimum entropy shall be enforced.
5. Password reset shall only be triggered with physical device interaction (e.g. pressing a key on the device).

### Secure Firmware Update

1. Firmware update images shall implement a cryptographic signature.
2. This signature shall be based eithier on assymmetric cryptography (global key is allowed) or symmetric cryptography (e.g. CMAC) with device-individual key.
3. A rollback protection mechanism shall be implemented.
4. The update image signature shall be checked **before** installing any update.
   
### Secure Boot

1. CPU and DSP implemented in the devices shall implement secure boot.
2. For devices with internal flash, a separate bootloader shall be used to implement secure boot.
3. For devices without internal flash, CPU / DSP vendor's secure boot mechanisms shall be used.
4. Secure boot shall be based on assymmetric cryptography. Integrity of the code shall be cheked **before** it runs on the CPUs/DSPs.
   
### Secure Debugging

### Tampering Detection

### Pure HW Protection Mechanisms


## Cloud

### Secure Communication

### Authentication & Session Tokens

### API Authorizations

### Remote Control & Remote Maintenance Security
Physical User Interaction w/ the device

### OTA Firmware Update

### Security in case of Compromised Server


## Secure Pairing Process & Factory Reset

