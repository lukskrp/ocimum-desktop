# Ocimum Desktop

Ocimum Desktop is the desktop of [TulsiOS](https://github.com/lukskrp/tulsipkgs): a fork of
[Cinnamon](https://github.com/linuxmint/cinnamon), named after *Ocimum*, the basil genus.

## Branches

| Branch | Contents |
|---|---|
| `master` | Mirror of upstream `linuxmint/cinnamon` `master` (development, currently 6.8) |
| `ocimum` | **The Ocimum Desktop release branch**: the Cinnamon release that TulsiOS's other Cinnamon components (muffin, cinnamon-desktop, cjs, …) match, plus the Ocimum commits on top |

`ocimum` is based on Cinnamon **6.8.0**, and tulsipkgs builds the rest of the Cinnamon
suite at the matching 6.8 releases (muffin 6.8.1, nemo 6.8.3, xapp 3.4.0, …).

## Ocimum changes

Kept small and isolated so rebasing onto new Cinnamon releases stays easy:

- Session names: "Ocimum Desktop" (session ids unchanged)
- System Info shows "Ocimum Desktop <version> (based on Cinnamon)"
- Basil-leaf logo (`ocimum-symbolic`, `ocimum`), used for the menu button
- Software Center and Assistant pinned to the panel by default; the terminal launcher is
  GNOME Terminal (upstream 6.8 pins Velocitty, which TulsiOS does not ship yet)

Theme, wallpaper and keyboard shortcuts are TulsiOS defaults, set by its NixOS modules,
not here.

## Rebasing onto a new Cinnamon release

```sh
git fetch https://github.com/linuxmint/cinnamon.git tag <version>
git rebase --onto FETCH_HEAD <old-base> ocimum
git push --force-with-lease origin ocimum
```

Then update the pinned revision in tulsipkgs (`pkgs/by-name/ci/cinnamon/package.nix`).

## License

GPL-2.0-or-later, like Cinnamon (see COPYING).
