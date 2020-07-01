# ir-gen
Generate ir-keytable config for unsupported IR remotes.

Requires `ir-ctl` to be installed (part of `v4l-utils`).

## Usage
Mark this script as executable and run as root from terminal:
```
./ir-gen
```
Hold your remote within 5 cm (2 inches) from IR receiver and press any key. The command should output an `ir-keytable` config (rc_keymap) in ".toml" format. Either copy and save output into file or run below command to save output into file directly (replace "example" with any name you want):
```
./ir-gen > /etc/rc_keymaps/example.toml
```

### Test
After keymap file is generated run below command to test if you get output from your remote:
```
ir-keytable -c -w example.toml -t
```
All that is left is to assign keyboard key names to different scancodes you get when pressing buttons during the test. To do this edit your "example.toml" file in any text editor. All linux key names can be found [here](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/include/uapi/linux/input-event-codes.h#n64).

To have the generated config auto loaded at boot, add below line to `/etc/rc_maps.cfg` file:
```
* * example.toml
```

## Donation
If you like my work please support it by buying me a cup of coffee :-)

[![PayPal](https://github.com/Rafostar/gnome-shell-extension-cast-to-tv/wiki/images/paypal.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=TFVDFD88KQ322)
