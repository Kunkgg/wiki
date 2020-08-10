# Anki

## How to setup anki-sync-server in local?

1. For Anki 2.1.
Create a new directory in the add-ons folder
(name it something like `ankisyncd`),
create a file named `__init__.py` containing the
code below and put it in the ankisyncd directory.

```python
import anki.sync, anki.hooks, aqt

addr = "http://127.0.0.1:27701/" # put your server address here
anki.sync.SYNC_BASE = "%s" + addr
def resetHostNum():
    aqt.mw.pm.profile['hostNum'] = None
anki.hooks.addHook("profileLoaded", resetHostNum)
```

2. Run sync server by docker,
use follow script ($HOME/.script/setup\_AnkiSync)

```sh
#!/usr/bin/bash

export ANKI_SYNC_DATA_DIR="${HOME}/Datas/Anki2"
export HOST_PORT=27701

[[ -d "${ANKI_SYNC_DATA_DIR}" ]] && mkdir -p "${ANKI_SYNC_DATA_DIR}"

docker run -itd \
   --mount type=bind,source="$ANKI_SYNC_DATA_DIR",target=/app/data \
   -p "$HOST_PORT":27701 \
   --name anki-container \
   --restart always \
   kuklinistvan/anki-sync-server:latest

docker container ps
```
