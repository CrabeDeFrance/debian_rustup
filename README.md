1. do rustup setup

```
./rustup.sh
```

2. then copy files

```
mkdir rustup/usr
cp -r ~/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/bin rustup/usr
cp -r ~/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/lib rustup/usr
cp -r ~/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/libexec rustup/usr

cargo install cbindgen
cp ~/.cargo/bin/cbindgen rustup/usr/bin
```

3. root permissions

```
chown -R root:root rustup
```
4. build package

```
dpkg-deb --build rustup
mv rustup.deb rustup-$(grep Version rustup/DEBIAN/control | cut -d ' ' -f 2).deb
```
