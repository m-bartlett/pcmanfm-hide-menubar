<sub>[patch](patch) file copied from
https://gist.github.com/M4he/3a8171a7f39d9ba9a0cf6bb387b08061</sub>

| **before** | **after** |
|---|---|
| ![before](https://user-images.githubusercontent.com/85039141/136505135-a7e7f949-c6c2-4627-b5ef-0bf84411b6e4.png) | ![after](https://user-images.githubusercontent.com/85039141/136505152-6992f8ab-0cde-4564-bbff-535d9c698079.png) |

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
