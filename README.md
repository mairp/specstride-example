# Specstride example: slugify

Try [Specstride](https://github.com/mairp/specstride-plugin) in five minutes. This repository is a tiny Node project with one
Spec Kit feature, [`specs/001-slugify`](specs/001-slugify/tasks.md), in three phases. Nothing is implemented yet: Specstride
does that, one reviewed and committed phase at a time.

![A Specstride run on this repository: three phases implemented, tested, reviewed and committed](assets/demo.gif)

_A real run on this repository, sped up (waits capped at 1.5 s, paths shortened). In phase 3 the two `[P]` tasks ran as a
parallel group; the merge check caught a test one worker wrote for a framework the project does not use, so the engine
redid both tasks in order before the reviewer saw the phase._

## Try it

You need Linux, Node 22+, git and Claude Code.

1. Install the plugin, in Claude Code:

   ```
   /plugin marketplace add mairp/specstride-plugin
   /plugin install specstride@specstride-marketplace
   ```

2. Clone this repository and open Claude Code in it:

   ```
   git clone https://github.com/mairp/specstride-example
   cd specstride-example
   claude
   ```

3. Say:

   > Run Specstride on the feature in this repo.

For each phase, the implementer works the tasks, the engine runs `npm test` itself, and a separate reviewer reads the change and
approves it or sends it back with its reasons. Each approved phase becomes its own commit:

```
git log --oneline
specstride: phase 3 approved — Short slugs and display titles
specstride: phase 2 approved — Accents, symbols and errors
specstride: phase 1 approved — Basic slugs
```

The run ends with a `DIGEST` line; `exit=0` means every phase was approved and committed.

## What is in the feature

| Phase                             | Tasks                                                           |
| --------------------------------- | --------------------------------------------------------------- |
| 1. Basic slugs                    | `slugify(text)` and its first tests                             |
| 2. Accents, symbols and errors    | accents removed, symbols dropped, a `TypeError` for non-strings |
| 3. Short slugs and display titles | `truncateSlug` and `titleFromSlug`, two independent `[P]` tasks |

The spec and plan beside the tasks are what the implementer and the reviewer read. Phase 3's `[P]` tasks run as a parallel group only when
[parallel units](https://github.com/mairp/specstride-plugin#parallel-units-opt-in) are turned on; otherwise they run in order.

## Start over

Approvals are kept outside the working tree, in `~/.specstride/workspaces/`. To run the example again from scratch, reset the
repository (`git reset --hard origin/main && git clean -fd`) and delete that workspace's directory.

## Licence

Apache-2.0.
