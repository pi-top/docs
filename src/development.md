# 👷 Development

This section seeks to offer advice for development work on pi-topOS.

### Changelog Formatting

    package-name (1.2.3) bullseye; urgency=medium

      * Fixed config file (#55)
        - Since version 1.0.1, the executable has moved to /usr/bin/command,
          but this was not reflected in the default config
      * Add support for Debian (#56)
        - Debian requires additional files to prevent invalid interface names.
      * Remove old tweaks

      -- pi-top <deb-maintainers@pi-top.com>  Mon, 27 Sep 2021 12:58:25 +0000
