# android-mesa-zink-spike

Standalone CI spike for investigating Mesa/Zink's Android build config, split
out of a private repo purely to run on public-repo (unlimited, free) Actions
minutes instead of burning that repo's private quota.

Currently investigating why `-Dandroid-stub=true` doesn't seem to prevent
Mesa's `libEGL.so`/`libgallium_dri.so` from linking against Android
platform-private libraries (`libcutils.so`, `libhardware.so`, `liblog.so`,
`libsync.so`, `libnativewindow.so`) that aren't safely `dlopen()`-able from a
normal app process.

No proprietary code lives here -- this only clones Mesa from its real
upstream (gitlab.freedesktop.org/mesa/mesa) and cross-compiles it for
Android/arm64.
