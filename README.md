<sub>[patch](patch) file copied from
https://gist.github.com/M4he/3a8171a7f39d9ba9a0cf6bb387b08061</sub>

# Arch install
```sh
makepkg -Arcis
```

# Manual Install from Upstream
```sh
mkdir -p upstream
curl -L https://github.com/lxde/pcmanfm/archive/refs/tags/1.3.2.tar.gz | tar xvfz - --strip-components=1 -C upstream
cp patch upstream/
cd upstream
git apply patch
./autogen.sh
./configure --prefix=/usr --sysconfdir=/etc
make && make install
```