---
layout: post
title: How to create a symlink
date: 2016-09-16 22:29:00
updated: 2024-06-14 11:50:59
excerpt: How to create a symbolic link (symlink).
categories: symlink symbolic link bash
---

Create a **symlink** (symbolic link) to alias another file or directory:

```sh
ln -s <source> <destination>
```

## Usage

Given the directory structure:

```
.
└── path
    └── to
        └── source
```

You can create a symlink like below:

```sh
ln -s path/to/source path/to/target
```

You'll now have the following:

```
.
└── path
    └── to
        ├── target -> path/to/source
        └── source
```

But what if the target file already exists?

```sh
ln -s path/to/source path/to/target
```

```
ln: path/to/target: File exists
```

You can force an override with the `-f` option:

```sh
ln -sf path/to/source path/to/target
```

Also, if you don't want the symlink to be relative, then make the path absolute:

```sh
ln -s "$(pwd)/path/to/source" path/to/target
```

Or use `realpath`:

```sh
ln -s "$(realpath path/to/source)" path/to/target
```

This ensures the symlink still points to the expected location even if it's moved.

Check out the manual page for more information:

```sh
man ln
```
