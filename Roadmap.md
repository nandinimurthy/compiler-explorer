# Compiler Explorer Road Map

CE was started in 2012 to serve my needs at [my company](https://drw.com) to show how
C++ constructs translated to assembly code. It started out as a `tmux` session with `vi` running in one
pane and `watch gcc -S foo.cc -o -` running in the other. Since then, it became a public website
serving the C++, Rust, Go, Haskell, Ispc, D, Swift and Pascal communities and performs around 20,000 compilations per day.

This document is an attempt to capture thoughts on the future direction of Compiler Explorer.

## Areas to improve

### Mobile client support

CE's UI doesn't work well with mobile clients. The editor doesn't support mobile clients, and the
layout doesn't lend itself well to small screens.

Ideas for improving mobile support include automatically folding up all the panes into a single tab upon
detection of a mobile client. This would require a bunch of fixes in the 
underlying [UI library](http://golden-layout.com) as this doesn't properly work with mobile and tabs.

Perhaps a read-only simplified view would work better: the main reason one brings up the CE website is to
look at tweeted links rather than author content.

### UI improvements

The UI has a number of things that need improving:

- [ ] Handling the loss of data if one has a work-in-progress CE window open and then clicks another CE link.

### Execution support

Another big ticket item is to allow executing of the user's code. This is fraught with security issues, and
brings up a number of UI and API considerations. Compiling code every time to execute with different params
seems wasteful, so caching seems good; but in a multi-instance setup a shared cache would be needed. Perhaps
a backend system that caches the executables (and makes them downloadable; at least for some compilers where
license allows), and stores the binaries in ephemeral, shared storage. This same backend system could also 
be used to store code, and could be part of a whole new way of sending and sharing code (if made permanent
storage).

### Support more compilers

Most of the open tickets are to do with adding new compilers, or fixing issues with existing compilers.
Continuing to add more compilers and make it easier for others to submit PRs to add new compilers is
very important. A [separate document](docs/AddingACompiler.md) explains how to add a compiler.

## Tensions

There's an inherent tension between the standalone, run-it-yourself version of CE and the scalable, AWS-backed
CE instance. Care must be taken to keep the standalone version usable.

## Priorities

Above all, the priority is to keep the main CE site up, stable and dependable.
That also means that URLs should live forever once they are created

## Non-goals

CE will remain ad-free, open-source and non-commercial. There's no plans at all to add "freemium" content,
despite the Patreon site where folks can help support the cost of running the servers.

## 2018 goals

With all this in mind, the tentative goals for 2018 are:
- [ ] Design an API that can handle remote code execution and download needs
- [ ] Implement remote execution UIs

These goals will be refined as time ticks on.
