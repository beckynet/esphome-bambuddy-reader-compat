# ESPHome compatibility

This maintained copy is prepared to support ESPHome 2026.7.4 and 2026.10.x; release validation is still pending.

The 2026.10 adapter is selected with `ESPHOME_VERSION_CODE`. It updates the PN532 transport overrides to use `std::span` and `PN532Frame`, reads MIFARE blocks into `MifareReadData`, and owns the custom tag trigger and binary sensor lists. The 2026.7.4 path retains the original `std::vector` transport and block interfaces.

The scan, authentication, key derivation, block ordering, decoding, and sensor publication logic are unchanged. The fixed-size 2026.10 buffers hold the same PN532 response payload and 16-byte MIFARE blocks as the former vectors.

## Validation still required before release

Compile the user's configuration against both ESPHome 2026.7.4 and the latest 2026.10.x patch, then verify a known Bambu spool scan on the user's PN532 hardware. In particular, verify the tag UID, derived-key authentication, and decoded filament fields. A successful compile alone does not prove the NFC reader's wire behavior.

Use the compatibility fork in `spool-reader/hw-nfc.yaml` after publishing this repository as `beckynet/esphome-bambuddy-reader-compat`.
