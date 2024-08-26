# Linux kernel Devcontainer

A Devcontainer dedicated for Linux kernel development and debugging, including all the required distro packages and [virtme-ng](https://github.com/arighi/virtme-ng) for seamlessly running and debugging the kernel. All of these done with the ease of the VSCode user  interface. It is ideal for kernel newbies.


## Usage
```
# Clone project
git clone https://github.com/tur11ng/linux-kernel-devcontainer.git
cd linux-kernel-devcontainer

# Clone kernel
git clone https://github.com/torvalds/linux.git --depth=1
cd linux

# Default configure kernel
make defconfig # or Task : Default configure kernel

# Configure kernel
make defconfig # or Task : Configure kernel

# Setup C/C++ development
make LLVM=1 compile_commands.json # or Task : Prepare C/C++

# Setup Rust development
# Enable rust for linux, for more information see : https://docs.kernel.org/rust/quick-start.html#configuration
make LLVM=1 rust-analyzer # or Task : Prepare Rust

# Build kernel
make LLVM=1 -j$(nproc) # or Task : Build kernel

# Run kernel
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose # or Task : Run kernel

# Debug kernel
# Enable debug symbols. For more information see : https://www.kernel.org/doc/html/v4.14/dev-tools/gdb-kernel-debugging.html
# After you have enabled debug symbols, compile the kernel again like above and continue with the following commands
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose --debug
vng -r arch/x86/boot/bzImage --memory=1G --disable-microvm --verbose --gdb"
# or Run and Debug -> Debug kernel (it will build with the kernel with debug symbols, run the kernel in debug mode and attach the debugger)

# For more information on available Tasks, check out .vscode/tasks.json or Ctrl+Shift+P -> Tasks: Run Task.
```
