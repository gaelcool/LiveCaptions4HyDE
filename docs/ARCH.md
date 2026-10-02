# Arch Linux and HyDE

Live Captions works with PipeWire through its PulseAudio compatibility server.
For desktop-audio captioning, start PipeWire, WirePlumber, and `pipewire-pulse`
in the user session before launching the application.

The application deliberately uses GTK's standard color variables instead of
hard-coded window colors. This lets HyDE's GTK theme determine the caption
window's palette.

## Packaging notes

An Arch package should depend on the runtime libraries used by the Meson build:

```
libadwaita libpulse onnxruntime
```

It should also install the desktop file, AppStream metadata, icons, and GSettings
schema via Meson's normal install step. `pipewire-pulse` is a runtime requirement
for desktop-audio capture on PipeWire systems; it is normally provided by a HyDE
installation rather than linked directly by the package.

The compiler diagnostics in the original AUR build log are warnings. The log ends
with a successful link and two passing validation checks, so they do not by
themselves indicate orphaned or missing build dependencies.
