# Notes for extracting files

I currently extract by hand. These notes try to formalize it for future automation.

In the examples below, the following placeholders are used:

- `<version>` - Full Firebird version (e.g. `5.0.4.1812-0`)
- `<architecture>` - CPU architecture (e.g. `x64`)
- `<short-version>` - Short Firebird version (e.g. `5.0.4`)

## Windows

TODO: Use commandline instead of Ark

1. Take `fbclient.dll`

## macOS

TODO: Find commandline for extracting the pkg itself

1. Extract `Firebird.pkg/Payload` from `Firebird-<version>-macos-<architecture>` using Ark
2. Use `gunzip -c Payload | cpio -i`
3. Take `Resources/lib/libfbclient.dylib`

## Linux

1. Use 
   ```
   tar -zxOf Firebird-<version>-linux-<architecture>.tar.gz --no-anchored buildroot.tar.gz | \
     tar -zxOf - ./opt/firebird/lib/libfbclient.so.<short-version> > libfbclient.so`
   ```
2. Take resulting `libfbclient.so`
