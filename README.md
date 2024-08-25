# Linux kernel Devcontainer

A Devcontainer dedicated for Linux kernel development and debugging, including all the required distro packages and [virtme-ng](https://github.com/arighi/virtme-ng) for seamlessly running and debugging the kernel. All of these bundled from the ease of the VSCode user  interface. It is ideal for kernel newbies.


## Usage
```
# Clone the project
git clone https://github.com/tur11ng/linux-kernel-devcontainer.git
cd linux-kernel-devcontainer

# Clone linux kernel
git clone https://github.com/torvalds/linux.git --depth=1
cd linux

# Basic configuration of linux kernel
make defconfig
make LLVM=1 compile_commands.json

# Compilation of linux kernel
make LLVM=1 -j$(nproc)

# Debugging
# For more information on debugging configurations see : https://www.kernel.org/doc/html/v4.14/dev-tools/gdb-kernel-debugging.html
# After you enabled debug symbols, compile the kernel again like above and continue with the following commands
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose --debug
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose --gdb # or simply launch the "Linux kernel" debug profile from the VSCode debugger
```
