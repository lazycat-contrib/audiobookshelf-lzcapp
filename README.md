# Audiobookshelf LazyCat community package

Upstream https://github.com/advplyr/audiobookshelf (GPL-3.0), 2.37.2. Package `community.lazycat.app.audiobookshelf`, min OS 1.5.0, amd64, mirror delivery, community (喵喵) store only.

Single container, no external database (Audiobookshelf ships its own SQLite). Configuration and metadata persist in two separate binds, matching upstream's split:

    /lzcapp/var/config:/config
    /lzcapp/var/metadata:/metadata

The image runs as root with `tini` as entrypoint and listens on port 80, so no `run_as` mapping or `setup_script` is needed. Media files themselves are not managed by this package — the library is expected to point at storage you control.

No `deploy_params.yml`: nothing is pre-seeded, and the first admin account is created in the browser on first visit. No `public_path`, so the library API stays behind the platform entry login.

Not device-tested: first account creation, library scan, playback, progress sync, mobile app connection, and persistence across restarts.
