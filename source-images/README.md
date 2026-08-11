# Source images

Web working copies of the author photos, kept here so the masthead portrait
can be regenerated without hunting for a file. **These are not the masters** —
the full-resolution camera originals live outside this repo.

**Hugo does not publish this directory.** Only `static/` is copied into the
built site, so nothing here is served to visitors.

| file | size | notes |
| --- | --- | --- |
| `2025_author_icon.png` | 1024×1024 | circular crop, transparent corners |
| `2025_author_pic.jpg` | 1600×2400 | full portrait |

Downscaled from 3584px and 4480px respectively, which together came to 23MB.
Git stores binaries whole and history is permanent, so the originals were
kept out deliberately; go back to the real masters for print or any crop
these can't support.

## Regenerating the masthead portrait

`static/images/author.png` is 200×200, displayed at 80px:

```sh
sips -Z 200 source-images/2025_author_icon.png --out static/images/author.png
```

Set `params.authorImage` in `config.toml` to point somewhere else, or delete
that line to drop the portrait from the masthead entirely.
