# Home Assistant Omada Add-On

This add-on brings the Omada Controller directly into Home Assistant running on an 64 bit ARM or a x64 processor.

This fork varies to https://github.com/jkunczik/home-assistant-omada by removing Stable and referencing only the Latest version:

- Omada Latest

Omada Latest is mostly consistent with the already tested [docker-omada-controller](https://github.com/mbentley/docker-omada-controller), but might contain some Home-Assistant related inconsistencies or bugs.

## Installation

Installing third-party repositories:

1. Go to home assistant -> settings -> addons -> addon store
2. Click the hamburger menu (The three dots in the top right corner)
3. Click repositories
4. At the bottom there should be a space to paste the GitHub link: https://github.com/Pseudophryne/home-assistant-omada
5. You might have to refresh the page, but it should show up in the addon store under "Home Assistant Omada"

## Options

If you would like to use your own SSL certificate configured for Home Assistant with this Omada Add-On,
it can be enabled in the configuration options.
Set `Enable Home Assistant SSL` to `true`, and enter the full path for:

- `Certificate file`
- `Private key`

The default paths are compatible with the `Letsencrypt` Add-On.

## Update to a new version

To update the controller to a new version, the changes of Matt Bentleys docker-omada-controller are manually merged into `Omada Latest`. The following steps have to be done:
- 1. Make sure that there are no changes in the Dockerfile
- 2. If there are changes in install.sh, copy it over, while keeping the Home Assistant specific processing steps in the bottom of the file. Add `aarch64` to the supported mongodb architectures (`case "${ARCH}" in amd64|arm64|aarch64|"")`)
- 3. If there are changes in entrypoint.sh, replace the old contents with the new, keeping the Home Assistant specific steps in the top of the file. Also, change the `echo` to proper `bashio::log` statements as described in the file.
- 4. Build the addon locally by commenting out `image: dratrav/home-assistant-omada-beta` in `config.yaml`

## Contribution

This add-on is a fork of Matt Bentleys [docker-omada-cotroller](https://github.com/mbentley/docker-omada-controller) and jkunczik [home-assistant-omada](https://github.com/jkunczik/home-assistant-omada). Other than in the original docker omada controller, this add-on stores all persistent data in the /data directory, so that it is compatible with Home assistant. This Add-On would not be possible without the effort of other people. Pull requests for version
updates or new features are always more than welcome. Special thanks goes to DraTrav for pushing this Add-On forward!

<a href="https://github.com/jkunczik/home-assistant-omada/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=jkunczik/home-assistant-omada" />
</a>

Made with [contrib.rocks](https://contrib.rocks).
