# dwm with my personal modifications

This repo contains [dwm](https://dwm.suckless.org/) with my preferred
modifications applied. The set of patches has evolved over the years (more
than a decade now). I don't expect this setup to be useful to others and
there's nothing particularly special about it, but it's shared all the same.
Right now modifications include:

* Add `config.h` with my preferred setup. Revert to colours used in an earlier
  dwm release, and use the Windows key as the modifier.
* Add support for re-execing the dwm binary (useful for when recompiling).
  Uses `getauxval(AT_EXECFN)` to get the binary location.
* Compile dwm with `-O2 -flto`. Not going to have any meaningful performance
  difference, but there doesn't seem a good reason not to.
* Apply the [pertag](https://dwm.suckless.org/patches/pertag/) patch so that
  layout etc. can be modified on a per tag basis.
* Apply the [centeredmaster](https://dwm.suckless.org/patches/centeredmaster/)
  patch to provide a new layout with the master area centered on the screen. I
  don't add the centeredfloatingmaster layout from that patch. Mapped to
  `Mod+c`.
* Apply the [movestack](https://dwm.suckless.org/patches/movestack/) patch to
  allow windows to be moved using `Mod+shift+j` and `Mod+shift+k`.
* Apply the [zoomswap](https://dwm.suckless.org/patches/zoomswap/) patch so
  that the current window and previous master are swapped upon zooming
  (`Mod+Enter`).
* Apply the [bottomstack](https://dwm.suckless.org/patches/bottomstack/) patch
  to provide a new layout where the master area is on the top of the screen
  and the stack is below. I remove the `bstackhoriz` layout, as I don't use
  it. `bstack` is mapped to `Mod+b` (and status bar toggling is remapped to
  `Mod+Shift+b`).
* Apply the [cyclelayouts](https://dwm.suckless.org/patches/cyclelayouts/)
  patch to enable cycling through the available layouts. This is mapped to
  `Mod+,` and `Mod+.`.
* Patch dwm so the clock in the status bar is updated each second, without
  relying on an external script calling `xsetroot`. This patch uses `select`
  with a `timerfd` to do this, and removes support for updating the status
  boar using `xsetroot`.

## Historical notes

Until recently (Dec 2019) I used dwm with the
[flextile](https://dwm.suckless.org/patches/flextile/) and
[systray](https://dwm.suckless.org/patches/systray/) patches, and a few extra
custom modifications. Although flextile provides a huge amount of flexibility
vs fixed layouts, I found I never used it and couldn't come up with easy to
remember bindings. Using the Windows key as the modifier rather than AltL is
also a recent change, that for now is a trial.
