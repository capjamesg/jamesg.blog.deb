# Turn your blog into a .deb file 

A `.deb` file is a bundled file that you can use to distribute software on Linux machines.

This repository provides a shell that you can use to add only a `man` page to your system's manual.

> [!WARNING]  
> This project was made for fun, to learn about the .deb packaging system.
> You should never install packages whose source you do not trust.
> I do not recommend using `.deb` as a way to share your blog to readers (the web is the best way to share what you write online), but this repository may help you learn a thing or two about the structure of a `.deb` file.

## Getting started

To get started, clone this repository:

```bash
git clone https://capjamesg/jamesg.blog.deb
cd jamesg.blog.deb/jamesg.blog
```

Then:

1. Open the `DEBIAN/source` file and replace the values with values that are meaningful to you (i.e. your name, email).
2. Open the `DEBIAN/changelog` file and add a changelog entry that makes sense to you.
3. Rename `usr/share/man/man1/jamesg.blog.1` to `usr/share/man/man1/<your-command>.1`. The `.1` suffix is required.

Once you have set up your package, run the following commands to build your package:

```bash
mkdir my-package
mv DEBIAN my-package/
echo " " > my-package/my-package # you need to have a blank file with the same name as your binary
dpkg-deb --build --root-owner-group my-package/
```

To install your package, run:

```bash
sudo dpkg -i my-package.deb
```

Your manual page will be available at:

```bash
man my-package
```

## License

This project is licensed under an MIT license. Any blog posts in the `usr/share/man/man1/jamesg.blog.1` file are All rights reserved.
