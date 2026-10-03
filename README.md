# MiSTer BGM Library

A shared music library for MiSTer FPGA, installed and updated through MiSTer Downloader or Update All. This database installs music files. Install the BGM player separately to hear them in the MiSTer menu.

## Install the music library

1. Download [the library's Downloader ZIP](https://raw.githubusercontent.com/fenderf4i/MiSTer-BGM-Library/db/downloader_fenderf4i_MiSTer-BGM-Library.zip).
2. Extract `downloader_fenderf4i_MiSTer-BGM-Library.ini` and copy it to the root of your MiSTer SD card, next to `downloader.ini` (normally `/media/fat/`).
3. Run Downloader, `update`, or Update All from the MiSTer Scripts menu.

Alternatively, add this section to your existing `downloader.ini`:

```ini
[fenderf4i/MiSTer-BGM-Library]
db_url = https://raw.githubusercontent.com/fenderf4i/MiSTer-BGM-Library/db/db.json.zip
```

Use either the drop-in file or the manual section; you only need to register the library once. Future runs download library updates.

## Install and use the BGM player

BGM is maintained in [MiSTer Extensions (mrext)](https://github.com/wizzomafizzo/mrext). See its [current BGM instructions](https://github.com/wizzomafizzo/mrext/blob/main/docs/bgm.md).

- With Update All: open its settings by pressing Up during the startup countdown, enable **MiSTer Extensions (wizzo)** under **Other Tools & Scripts**, save, and run the update.
- With Downloader: add the following section to `downloader.ini` and run Downloader. This installs the combined MiSTer Extensions collection:

```ini
[mrext/all]
db_url = https://raw.githubusercontent.com/wizzomafizzo/mrext/main/releases/all.json
```

After both the player and music have been installed:

1. Run `bgm` from the MiSTer Scripts menu to perform its initial setup.
2. Select the **MiSTer-BGM-Library** playlist in its control screen. If the first run only performs setup, run `bgm` again.
3. Enable random playback or single-track looping as desired.

BGM can play music in the menu, stop when a core launches, and resume when you return to the menu. Its first run sets up automatic startup. This library does not replace your `bgm.ini`, other playlists, or startup configuration.

## Included test track

| Track | Creator | License | Installed path |
| --- | --- | --- | --- |
| Happy Adventure (Loop) | TinyWorlds | CC0 1.0 | `music/MiSTer-BGM-Library/Happy Adventure.mp3` |

[Original track and creator's license declaration](https://opengameart.org/content/happy-adventure-loop) · [CC0 public-domain dedication](https://creativecommons.org/publicdomain/zero/1.0/)

The test track may be copied and redistributed under CC0 without required attribution. Creator credit is retained here for provenance. The original MP3 is preserved without conversion. It is suitable for testing installation and playback; a small gap may be audible when looping.

## Add music to the library

1. Add supported audio files under `music/MiSTer-BGM-Library/` on the `main` branch. BGM supports `.mp3`, `.ogg`, `.wav`, `.mid`, `.vgm`, `.vgz`, and `.vgm.gz`.
2. For a separate selectable playlist, create a uniquely named folder directly under `music/`.
3. Record each track's creator, source URL, and redistribution license in this README. Only add tracks you have permission to distribute publicly.
4. Commit or merge the change into `main`. The **Build Custom Database** GitHub Action generates and tests the database, then publishes it on the `db` branch.
5. Wait for the Action to finish successfully before asking users to run Downloader again.

GitHub's **Add file > Upload files** can be used by repository maintainers. Other contributors can submit a pull request. Avoid replacing another collection's paths. A leading underscore in a BGM filename marks a boot sound, so ordinary music filenames should not start with `_`.

For externally hosted tracks, list their destination paths, direct URLs, byte sizes, and MD5 hashes in `external_files.csv`. Use stable direct-download URLs. Files committed to this repository are downloaded directly from GitHub.

## Troubleshooting

- **Database download fails:** check the repository's Actions tab and make sure the latest build succeeded; verify the URL above is copied exactly.
- **Tracks downloaded but no music plays:** install and run BGM, select the library playlist, enable playback, and check volume. Downloader installs files; it does not start the player.
- **Playlist missing:** check that tracks are present in `/media/fat/music/MiSTer-BGM-Library/`, then restart BGM.
- **Update verification:** run Downloader a second time after a successful installation; unchanged tracks should not need downloading again.

Database: [db.json.zip](https://raw.githubusercontent.com/fenderf4i/MiSTer-BGM-Library/db/db.json.zip) · [Build status](https://github.com/fenderf4i/MiSTer-BGM-Library/actions)

Built using [theypsilon's Custom Database Template](https://github.com/theypsilon/DB-Template_MiSTer). The template's software license is retained in `LICENSE`; music uses the license listed for each track above.
