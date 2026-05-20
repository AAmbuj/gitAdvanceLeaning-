# Hello World C++ With Bazel

This repository contains a minimal C++ project structured for Bazel with Bzlmod enabled through `MODULE.bazel`.

## Project Structure

```text
.
├── BUILD.bazel
├── MODULE.bazel
├── README.md
└── src
	├── BUILD.bazel
	└── main.cc
```

## Requirements

- Bazel with Bzlmod support enabled by default
- A working C++ toolchain such as `g++` or `clang`

## Build

```bash
bazel build //:hello_world
```

## Run

```bash
bazel run //:hello_world
```

## Git Problem

The branch `amsh_first_commit` currently contains three separate commits:

- `first Commit`
- `second Commit`
- `third commit`

This works, but it makes the pull request history noisier than necessary when the changes belong to one logical update.

## Git Solution

Use interactive rebase to squash the last three commits into one:

```bash
git rebase -i HEAD~3
```

When the editor opens, keep the first commit as `pick` and change the next two to `squash`:

```text
pick bfbb69e first Commit
squash 586a3ce second Commit
squash cecb184 third commit
```

Save and close the editor, write the final combined commit message, then update the remote branch:

```bash
git push --force-with-lease origin amsh_first_commit
```

## Notes

- `MODULE.bazel` defines the Bazel module metadata and adds `rules_cc` for C++ rules.
- The root `BUILD.bazel` exposes a convenient top-level `hello_world` target.
- `src/BUILD.bazel` defines the actual `cc_binary` target.
