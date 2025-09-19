# Borealis - custom Aurora-DX image &nbsp; [![bluebuild build badge](https://github.com/alexfullmoon/borealis/actions/workflows/build.yml/badge.svg)](https://github.com/alexfullmoon/borealis/actions/workflows/build.yml)

Using `aurora-dx:stable`, customized for personal use and Thinkpad X1Y5 laptop.

## Installation

From suitable image (preferably freshly-installed aurora-dx):

```
rpm-ostree rebase ostree-unverified-registry:ghcr.io/alexfullmoon/borealis:stable

systemctl reboot

rpm-ostree rebase ostree-image-signed:docker://ghcr.io/alexfullmoon/borealis:stable

systemctl reboot
```

## Current changes from Aurora-DX

## TODO

- RPMs
  - Solaar
    - Also adds udev rules
  - Bitwarden
  - Sublime Text
  - SourceGit
  - Firefox
  - Crossover
- Flatpaks
  - LibreOffice
  - GearLever
  - Betterbird instead of Thunderbird
  - Obsidian
  - Steam
  - Discord
  - Zotero
- Chezmoi dotfiles sync
- System config
  - Enabled SMB1 for VM printer
  - Disabled avahi-daemon listening on ethernet (make it more universal?)
- Removed
  - Input Leap
  - InputRemapper (it conflicts with Solaar)
  - DejaDup

## TODO

- [ ] Add libfuse for continuing support of AppImage (whenever they drop it from Bluefin)
- [ ] Seafile, WindTerm, Ghostty
- [ ] Make chezmoi distinguish between KDE and Gnome
- [ ] Add KDE settings?
- [ ] See what's going on with avahi-daemon printer spam 
 
## Current issues (from Bluefin)

Notes after installation from ISO:

- Need to set all flatpaks, adding flatpak module resets all of standard ones.
- Grub config does not apply.
- Overall, rebasing from original ublue images works better.
- Consider moving to UBlue build template.

Ghostty RPM install conflicts with its own terminfo file from ncurses. Awaiting fixes.

Crossover apparently _really_ doesn't like being installed on readonly filesystem, any operation with existing bottles results in hang up. Importing archived bottles work, though. For creating new bottles install a copy into distrobox
