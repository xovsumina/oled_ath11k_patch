# oled_ath11k_patch

1. Log into Desktop mode
2. Obtain `sudo` access by running `passwd` and setting a password
3. Disable read-only via `sudo steamos-readonly disable`
4. Create an `updates` directory in the local OS build directory: `sudo mkdir /usr/lib/modules/$(uname -r)/updates`
5. Copy all 3 `.ko` files to this directory
6. Disable wifi
7. Run `sudo depmod -a` to refresh modules dependency list
8. Re-enable read-only via `sudo steamos-readonly enable`
9. Unload the current ath11k module via `sudo modprobe -r ath11k_pci` and `sudo modprobe -r ath11k`
10. Load the patched driver by running `sudo modprobe ath11k`, then `sudo modprobe ath11k_pci`
11. Confirm that you're using the patched version by running `modinfo ath11k` and looking for the `.../updates/ath11k.ko` path under `filename`
12. Re-enable wifi
13. Reboot the deck
