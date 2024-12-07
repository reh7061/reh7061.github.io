---
layout: post
title: "CTF Challenge: Buffer Overflow"
date: 2024-11-10
categories: ctf
---

# CTF Challenge: Buffer Overflow

## Overview
In this challenge, we were provided with a vulnerable binary that contained a classic buffer overflow exploit. The goal was to obtain a shell on the remote server.

## Tools Used
- **GDB**: For debugging the vulnerable binary.
- **Python**: To craft the exploit payload.

## Step-by-Step Solution
### Step 1: Analyzing the Binary
- Opened the binary in **GDB**.
- Found the vulnerable function `vuln()` that lacked proper boundary checks for user input.

### Step 2: Crafting the Payload
- Calculated the offset to the return address using a cyclic pattern.
- Overwrote the return address to redirect execution to the shellcode.

```python
# Crafting payload using Python
offset = 72
payload = b"A" * offset
payload += b"\xef\xbe\xad\xde"  # Address to redirect to shellcode
print(payload)
```
