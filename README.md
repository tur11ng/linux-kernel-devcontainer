# Linux kernel Devcontainer

```
git clone https://github.com/tur11ng/linux-kernel-devcontainer.git
cd linux-kernel-devcontainer

git clone https://github.com/torvalds/linux.git --depth=1
cd linux

make defconfig
make LLVM=1 compile_commands.json
make LLVM=1 -j$(nproc)

# For debugging configurations see : https://github.com/Rhydon1337/linux-kernel-debugging
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose --debug
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose --gdb # or simply launch the "Linux kernel debug" profile from the vscode debugger
```
