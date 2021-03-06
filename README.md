# grmon

Command line monitoring for goroutines

<p align="center"><img src="https://bradley.codes/static/img/grmon.gif" alt="grmon"/></p>

## Install

```bash
go get -u github.com/bcicen/grmon/cmd/grmon
```

## Usage

Simply import and call `grmon.Start()` somewhere in your code:

```go
import "github.com/bcicen/grmon"
...
grmon.Start()
```

alternatively, you may just use the handler registered on import:

```go
import (
  _ "github.com/bcicen/grmon"
  "net/http"
)
...
http.ListenAndServe(":1234", nil)
```

now `grmon` can connect to the running program:
```bash
grmon
```

By default, `grmon` will automatically refresh every 5s. Pause automatic refresh(`p`) to enable the cursor and expand the full trace for a selected goroutine(`<enter>`).

### Keybindings

Key | Action
--- | ---
r | manually refresh
p | pause/unpause automatic updates
s | toggle sort column and refresh
f | filter by keyword
\<up\>,\<down\>,j,k | move cursor position
\<enter\>,o | expand trace under cursor
t | open trace in full screen mode
q | exit grmon

### Options

Option | Description | Default
--- | --- | ---
-endpoint	| URL endpoint for grmon | /debug/grmon
-host | listening grmon host | localhost:1234
-i | time in seconds between refresh, 0 to disable | 5


## Roadmap

* Hierarchal/tree display
