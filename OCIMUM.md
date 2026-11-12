# Ocimum Desktop

Ocimum Desktop is the desktop of [TulsiOS](https://github.com/lukskrp/tulsipkgs): a hard fork
of [Cinnamon](https://github.com/linuxmint/cinnamon), named after *Ocimum*, the basil genus.
Cinnamon is the base; Ocimum takes its own direction from here and does not track
upstream releases.

## Branches

| Branch | Contents |
|---|---|
| `master` | Mirror of upstream `linuxmint/cinnamon` `master`, for reference |
| `ocimum` | **Ocimum Desktop.** Forked from Cinnamon 6.8.0 |

tulsipkgs builds `cinnamon` from `ocimum` and the rest of the suite at the 6.8 releases it
was forked from (muffin 6.8.1, nemo 6.8.3, xapp 3.4.0, …).

## Toolkit

Ocimum's GUI toolkit is GTK 3 through TulsiOS's forks, GTK3-O and
[OTK](https://github.com/lukskrp/OTK). One exception for now: the background daemon
inherited from Cinnamon 6.8 (per-monitor wallpapers) uses GTK 4. It will be ported to OTK
once OTK has the GTK 4 features it needs.

## Ocimum changes so far

- Session names: "Ocimum Desktop" (session ids unchanged)
- System Info shows "Ocimum Desktop <version> (based on Cinnamon)"
- Basil-leaf logo (`ocimum-symbolic`, `ocimum`), used for the menu button
- Software Center and Assistant pinned to the panel by default; the terminal launcher is
  GNOME Terminal (upstream 6.8 pins Velocitty, which TulsiOS does not ship yet)

Theme, wallpaper and keyboard shortcuts are TulsiOS defaults, set by its NixOS modules,
not here.

## Taking changes from Cinnamon

Upstream changes are picked deliberately, not merged wholesale:

```sh
git fetch https://github.com/linuxmint/cinnamon.git master
git cherry-pick <commit>…
```

After pushing to `ocimum`, update the pinned revision and hash in tulsipkgs
(`pkgs/by-name/ci/cinnamon/package.nix`).

## License

GPL-2.0-or-later, like Cinnamon (see COPYING).
