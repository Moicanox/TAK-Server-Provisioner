# TAK Server Provisioner

**TAK Server Provisioner** is an independently developed plugin for **ATAK-CIV** that imports certificates and configures a TAK Server connection from a provisioning ZIP package.

## Compatibility

| Component           | Supported version |
| ------------------- | ----------------- |
| Plugin              | 1.0               |
| ATAK-CIV            | 5.7.0             |
| Minimum Android API | 23                |

The APK published in the [Releases](https://github.com/Moicanox/TAK-Server-Provisioner/releases/latest) section is signed through the **TAK.gov Third Party Pipeline**.

> [!IMPORTANT]
> ATAK plugins are version-specific. This release is intended for **ATAK-CIV 5.7.0** and should not be installed on other ATAK versions.

## Features

* Imports provisioning ZIP packages from the Android file system.
* Supports unencrypted and password-protected ZIP archives.
* Supports standard ZIP encryption and AES encryption.
* Reads server configuration from `manifest.json`.
* Detects PKCS#12 and PFX truststores and client certificates.
* Supports multiple client certificates.
* Provides a manual configuration form when information is missing.
* Configures the TAK Server connection directly in ATAK.
* Keeps the ZIP password only for the active plugin session.
* Deletes the provisioning ZIP from the device after a successful import.

## Download

Download the latest TAK.gov-signed APK from the project releases page:

[Download the latest release](https://github.com/Moicanox/TAK-Server-Provisioner/releases/latest)

> [!WARNING]
> When using an ATAK release build, install only the APK signed through the **TAK.gov Third Party Pipeline**.

## Installation

1. Download the signed APK from the [Releases](https://github.com/Moicanox/TAK-Server-Provisioner/releases/latest) section.
2. Copy the APK to the Android device.
3. Install the APK.
4. Open **ATAK-CIV 5.7.0**.
5. Enable **TAK Server Provisioner** if requested by the ATAK Plugin Manager.

## Usage

1. Copy the provisioning ZIP package to the Android device, normally into the `Download` directory.
2. Open **TAK Server Provisioner** from the ATAK toolbar.
3. Select the provisioning ZIP package.
4. Enter the ZIP password, if required.
5. Select the client certificate.
6. Complete any missing configuration fields.
7. Press **APPLY**.
8. Verify the connection under **Manage Server Connections**.

> [!NOTE]
> After a successful import, the plugin deletes the source ZIP package from the device for security reasons.

## Provisioning ZIP Package

The provisioning ZIP filename is not restricted.

For example, both of the following filenames are valid:

```text
server-certificates.zip
test123456.zip
```
<img width="886" height="133" alt="root" src="https://github.com/user-attachments/assets/ba71c1d6-2343-4ffc-b08a-2071270836ac" />

### Recommended Structure

```text
provisioning.zip
├── manifest.json
└── certs/
    ├── trust/
    │   └── truststore.p12
    └── clients/
        ├── client-01.p12
        └── client-02.p12
```

<img width="990" height="738" alt="json" src="https://github.com/user-attachments/assets/4f5c00f5-56b3-470f-b9d0-b16a6e64befb" />

A demonstration provisioning package is available in the [Releases](https://github.com/Moicanox/TAK-Server-Provisioner/releases/latest) section.

> [!CAUTION]
> The demonstration package contains sample data only. It must not be used as a production credential package.

## Security

* ZIP passwords are kept only for the active plugin session and are not stored permanently.
* Production certificates and passwords must never be published on GitHub.
* The provisioning ZIP package is deleted only after the configuration has completed successfully.
* If Android prevents the ZIP package from being deleted, the plugin displays a security warning.
* Keep a secure backup of the original provisioning package outside the ATAK device.

## Disclaimer

This is an independent project and is not affiliated with, sponsored by, or endorsed by:

* the TAK Product Center;
* TAK.gov;
* the United States Government;
* any commercial organization.

## License

TAK Server Provisioner is distributed as proprietary freeware.

The compiled APK may be downloaded and used free of charge under the terms
contained in the [LICENSE](LICENSE) file.

The source code is not included and is not licensed for distribution,
modification or reuse.

Please distribute only links to the official GitHub Releases page. Rehosting
or redistributing the APK is not permitted.
