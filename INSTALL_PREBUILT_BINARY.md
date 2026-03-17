# How to install wfweb without building yourself

wfweb provides prebuilt packages for the following platforms, available on the [GitHub Releases](https://github.com/adecarolis/wfweb/releases) page:

| Package | Platform |
|---|---|
| `wfweb_<version>_amd64.deb` | Ubuntu / Debian x86_64 |
| `wfweb_<version>_arm64.deb` | Raspberry Pi / Linux ARM64 |
| `wfweb-windows-x86_64.zip` | Windows x86_64 |

If your platform is not listed, see [BUILDING.md](BUILDING.md) for build-from-source instructions.

---

## Ubuntu / Debian (x86_64)

Download the latest `wfweb_<version>_amd64.deb` from the [releases page](https://github.com/adecarolis/wfweb/releases), then install it:

~~~
sudo apt install ./wfweb_<version>_amd64.deb
~~~

`apt` will automatically install all required runtime dependencies.

---

## Raspberry Pi / Linux ARM64

Download the latest `wfweb_<version>_arm64.deb` from the [releases page](https://github.com/adecarolis/wfweb/releases), then install it:

~~~
sudo apt install ./wfweb_<version>_arm64.deb
~~~

`apt` will automatically install all required runtime dependencies.

---

## Windows

Download the latest `wfweb-windows-x86_64.zip` from the [releases page](https://github.com/adecarolis/wfweb/releases), extract it, and run `wfweb.exe` from the extracted directory. The ZIP is self-contained with all required DLLs.

---

## After installing

Before running wfweb for the first time, create a configuration file for your radio. See the [Quick start](README.md#quick-start-headless-ic-7300-via-usb) section in the README for details.

Then start wfweb manually:

~~~
wfweb
~~~

Open your browser at `https://<hostname>:8080` and accept the self-signed certificate warning on first visit.

### Autostart with systemd

To start wfweb automatically at boot:

~~~
systemctl enable --now wfweb@$USER
~~~

To check status or view logs:

~~~
systemctl status wfweb@$USER
journalctl -u wfweb@$USER -f
~~~

### Serial port access

For USB-connected radios, add your user to the `dialout` group:

~~~
sudo usermod -aG dialout $USER
~~~

Log out and back in for this to take effect.
