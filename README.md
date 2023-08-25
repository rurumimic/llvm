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

### Packages

```bash
sudo pkg update -f
sudo pkg install git cmake ninja cscope
```

---

## llvm/llvm-project.git

```bash
cd $HOME
git clone https://github.com/llvm/llvm-project.git
```

### Setup

#### $HOME/.profile

```bash
cat <<EOF | tee -a $HOME/.profile > /dev/null

alias ll='ls -alGFh'
alias vi='vim'

export CSCOPE_DB="$HOME/llvm-project/cscope.out"

EOF
```

#### plugin.vim

```bash
cat /usr/local/share/vim/vim90/plugin/cscope_relative.vim

set cscope_relative
```

#### Cscope

- tutorial: [Vim/Cscope](https://cscope.sourceforge.net/cscope_vim_tutorial.html)
- [cscope_maps.vim](https://cscope.sourceforge.net/cscope_maps.vim)

```bash
cd llvm-project
cscope -b -q -R
```

- b: just build the database without GUI
- q: create a inverted index file
- R: parse all subdirectories

output:

```bash
cscope.in.out
cscope.out
cscope.po.out
```

#### Finding

- Find
  - `:cs find s <keyword>`: find this symbol
    - `:cs find 0 <keyword>`
    - `:cs f s <C-R><C-W>`: find the word under cursor
    - `<C + \>` + `s`: find the word under cursor
- Jump
  - `:[count]tn[ext][!]`: Jump to count next matching tag (default 1)
  - `:[count]tp[revious][!]`: Jump to count preivious matching tag (default 1)

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

