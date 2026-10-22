# KiCad Library Installer for Windows

A small Windows tool to help install and update the Würth Elektronik KiCad libraries. I made it after receiving questions about the manual installation process; it uses a local Git installation to download or update the library and then configures your KiCad user settings.

> **Important — unofficial tool; use at your own risk.** This installer is a personal project. It is **not an official Würth Elektronik release** and has **not been officially reviewed, verified or approved by Würth Elektronik**. It modifies KiCad configuration files on your computer and downloads library content from GitHub. You are responsible for deciding whether to run it and for checking the result before using the libraries in a design. Back up any important settings and projects first.

## Requirements

- Windows with a KiCad **8, 9 or 10** user configuration. Other versions are not supported by this installer.
- [Git for Windows](https://git-scm.com/download/win), installed and available on your system `PATH`.
- Internet access to GitHub for the initial download and subsequent updates.

Start KiCad at least once and initialize its standard libraries before using the installer. **Close KiCad completely** before installing or updating the libraries.

## Installation

1. Download `WE-KiCad-Installer.exe` from this repository's release files.
2. Check that the file comes from the repository you intended to use. Only run software you trust and follow your organization's software-installation policy.
3. Start the EXE and select the KiCad configuration you want to update.
4. Read the responsibility notice, tick the acknowledgement if you agree, and click **Install / update libraries**.
5. Wait for the completion message. Restart KiCad and check that the symbol, footprint and 3D model paths work as expected.

The installer shows Git's current operation and, when Git reports it, a percentage for the current Git stage. **That percentage is not progress for the entire installation.** Git must be installed locally; the EXE does not install Git for you. If you install Git while the EXE is open, close and restart the EXE so it can see the updated `PATH`.

## What the installer changes

- It clones or updates the library in `%LOCALAPPDATA%\WurthElektronik\KiCad-Library`.
- It adds the library paths to the selected version's `kicad_common.json` and updates its user-level symbol and footprint library tables under `%APPDATA%\kicad\<version>`.
- For KiCad 10, it uses linked library tables; for KiCad 8/9, it adds individual library entries.
- Before overwriting an existing configuration file, it creates a timestamped `.bak` copy next to that file. Files that do not change are not backed up again.

The tool does **not** remove the library or reverse the KiCad configuration changes automatically. If an installation fails partway through, check the log and restore the relevant `.bak` files manually if necessary.

## Problems or suggestions?

Feedback is welcome, especially bug reports. Please include your Windows and KiCad versions, the relevant message from the installer's log, and what you expected to happen. **Remove usernames, private paths, credentials and other sensitive information** before posting logs publicly.

This project does not come with official Würth Elektronik support or a guarantee that the installer or library will be suitable for your particular design. Verify your KiCad configuration and library content yourself.
