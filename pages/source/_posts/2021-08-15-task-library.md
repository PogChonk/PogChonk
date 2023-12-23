---
layout: post
title: Task Library
category: Studio
author: Thodor12
links: [
    "https://devforum.roblox.com/t/task-library-now-available/1387845",
    "https://developer.roblox.com/en-us/api-reference/lua-docs/task"
]
tags: ["Thodor12", "Studio"]
---

Along with the update of the [Task Library](#link1) (see also [task library documentation](#link2)), we got a new set of functions for task scheduling, along with a new and improved `wait()` function, namely `task.wait()`.

This function is the new equivalent of doing `RunService.Heartbeat:Wait()` which was always considered a better option.

Along with the new Find and Replace window Roblox recently introduced it's now very easy to convert to this new function by use of a regex operation:
- Fill in in the find bar: `(?<![\S\.])wait\(`
- Enable regex searching (third icon next to find bar, the dot with the star)
- Fill in the replace bar: `task.wait(`

What this does it looks for all occurences of `wait(` with a couple of additional checks
- It does not catch cases that are preceded by any other non whitespace character (means it won't alter things like variables or functions which are trailing with `wait(`
- It does not catch cases that are preceded by a dot (this means it won't accidently overwrite any occurences of existing `task.wait(`

**Note**: This same method works for all task library functions, for example if you wanted to change the occurences of `spawn` you would do: `(?<![\S\.])spawn\(` and `task.spawn(`.