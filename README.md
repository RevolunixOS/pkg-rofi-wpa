# rofi-wpa

Rofi front end for a `wpa_supplicant`-managed Wi-Fi connection, with an
additional submenu for bringing WireGuard interfaces up or down.

> [!CAUTION]
> The script writes Wi-Fi configuration to `/etc/wpa_supplicant.conf`, removes
> network entries, and runs `wg-quick` through `sudo`. Review it and keep a
> recovery path before using it on a remote or production machine.

## Build and install

```bash
nix build github:RevolunixOS/pkg-rofi-wpa
nix profile install github:RevolunixOS/pkg-rofi-wpa
```

Open the menu with:

```bash
rofi-wpa
```

Reload the saved configuration into the runtime path with:

```bash
rofi-wpa -l
```

## Requirements

- `wpa_supplicant` controlled through `wpa_cli`;
- `iw`, `ip`, and standard shell utilities;
- optional WireGuard configurations in `/etc/wireguard/*.conf`;
- `wg-quick` and suitable sudo rules for WireGuard actions;
- a patched Nerd Font for menu icons.

The Nix wrapper currently provides only Rofi. Network and WireGuard tools must
be supplied by the host. The script assumes a writable global
`/etc/wpa_supplicant.conf` and is not designed for NetworkManager-managed
systems.

## License

See [`LICENSE`](LICENSE).
