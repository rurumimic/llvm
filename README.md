# LLVM

- [llvm.org](https://llvm.org/)
  - [releases](https://releases.llvm.org/)
  - [docs](https://llvm.org/docs/)
- [github.com/llvm](https://github.com/llvm)
  - [llvm-project](https://github.com/llvm/llvm-project)

---

## FreeBSD 13

Start FreeBSD:

```bash
vagrant up
vagrant ssh
```

### Built-in LLVM/Clang

```bash
clang --version

FreeBSD clang version 13.0.0 (git@github.com:llvm/llvm-project.git llvmorg-13.0.0-0-gd7b669b3a303)
Target: x86_64-unknown-freebsd13.1
Thread model: posix
InstalledDir: /usr/bin
```

### Install Packages

```bash
sudo pkg update -f
sudo pkg install git
sudo pkg install cmake
sudo pkg install ninja
```

Already provisioned with vagrant.

---

## llvm/llvm-project.git

```bash
git clone https://github.com/llvm/llvm-project.git
```

### Cscope

- tutorial: [Vim/Cscope](https://cscope.sourceforge.net/cscope_vim_tutorial.html)
- [cscope_maps.vim](https://cscope.sourceforge.net/cscope_maps.vim)

```bash
cd llvm-project
cscope -b -q -R
```

- b: just build the database without GUI
- q: create a inverted index file
- R: parse all subdirectories

```bash
cscope.in.out
cscope.out
cscope.po.out
```

---

## Source Code

- [src/helloworld](src/helloworld/README.md)
  - [src/helloworld/hello.c](src/helloworld/hello.c)
- [src/sum](src/sum/README.md): opt, llc, llvm-mc, lli, llvm-link, llvm-as, llvm-dis
- [src/frontend](src/frontend/README.md)

---

## Ref

### vimrc

- [vimrc](https://github.com/amix/vimrc) by amix

