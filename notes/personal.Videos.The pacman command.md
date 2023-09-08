---
id: x02s8i6lsifil3h3qkrdara
title: The pacman command
desc: >-
  Title: Linux Crash Course - The Pacman Command
  URL: https://www.youtube.com/watch?v=HD7jJEh4ZaM
updated: 1689626325766
created: 1683505681650
---

- `pacman -Syy`

		- `S`: sync.

		- `y`: refresh the packets database.

		- `y`: force to refresh the local databases (even if it's up to date).

- When you're using pacman and you attempt to do any operation that requires synchronization (such as installing a package from a repository), it will used the servers described in the file `/etc/pacman.d/mirrorlist` (trying from the top to the bottom).

- `pacman -S <package>`: to install a package.

- `pacman -R <package>`: to uninstall a package.

		- `R`: remove

- `pacman -Ss <presumed package name>`: search for a package (specific name).

- `pacman -Qdt`: find orphan packages.

		- `Q`: query.

		- `d`: skips dependency checks.

		- `t`: limit the results to orphan packages.

- `pacman -Syu`

		- `u`: update.

	> Two weeks between upgrades is a good amount of time.

- It's a good idea regenerate your mirrorlist often (every month).
