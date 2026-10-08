# WifiQR

Display a QR code for the current Wi-Fi network in your macOS terminal.
The shell script reads the network name and its Keychain password, then sends
a WPA Wi-Fi payload to `qrencode`.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).

[Installation](#installation) · [Usage](#usage) · [Report an issue](https://github.com/wispdevon/wifiqr/issues)

## Status and compatibility

This is a small macOS utility. The original README records testing on Big Sur;
current macOS releases have not been verified. The script assumes the Wi-Fi
interface is `en0` and uses `networksetup -getairportnetwork`.

- WPA is the only authentication type implemented.
- Linux and Windows branches print the detected platform; they do not generate a QR code.
- Reading a saved password may require Keychain authorization.
- The script does not escape reserved Wi-Fi QR payload characters; unusual SSIDs
  or passwords may produce a QR code that does not connect correctly.

## Installation

The current source invokes **`qrencode`**; it does not use a library named
`libqrcode` directly. Install the command using
[Homebrew](https://formulae.brew.sh/formula/qrencode):

```bash
brew install qrencode
git clone https://github.com/wispdevon/wifiqr.git
cd wifiqr
chmod +x wifiqr.sh
```

## Usage

```bash
./wifiqr.sh
```

Connect to the intended network first and approve any Keychain prompt. The QR
code appears as terminal text. Optional installation on your PATH is described
below; it requires write access to the destination:

```bash
sudo install -m 755 wifiqr.sh /usr/local/bin/wifiqr
wifiqr
```

## Privacy

The QR code includes the network password. Anyone who can see or capture it may
be able to join the network. Avoid public screenshots and terminal recordings.
The script reads credentials from macOS Keychain and passes the payload to
`qrencode` locally; it does not implement a remote upload service.

## Contributing

Useful improvements include modern macOS compatibility, Wi-Fi interface
detection, payload escaping, and explicit WPA/WEP/open-network handling.
Open an [issue](https://github.com/wispdevon/wifiqr/issues) or a focused pull
request with the macOS version and a test using dummy network credentials.
Linux support would need actual QR generation rather than a platform message.

## License

No license file is present. The original README credits
[libqrcode](https://github.com/ChuckM/libqrcode); the current script invokes
`qrencode`. No open-source reuse license is implied for this repository.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).
