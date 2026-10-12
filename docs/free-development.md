# Free edition development

This repository contains the public production app. Its available directors are the Purist and the Craftsman. Additional premium directors, channel strategy, YouTube analytics connection and imports, business outcomes, topic recommendations, and measured audience feedback belong in the separate private premium repository.

The free runtime always burns **Created by CoProd** into full-video rough cuts and final renders, including scripted Resolve outputs and manually delivered MP4/MOV masters. The overlay is independent of the plan, director and provider, with no setting to disable it. Premium is available at <https://coprod.app/>.

The checked-in overlay (`packages/media/assets/free-watermark.png`) is regenerated with `swift scripts/make-watermark.swift`. It works without system fonts or FFmpeg's optional `drawtext` filter. Its bytes and layout are part of the preview signature and watermark cache identity; upstream scene, caption and audio caches remain reusable. QA verifies the watermarked rough cut. Current rough cuts are copied into the FFmpeg final without a second overlay; older approved previews gain the watermark when re-rendered. The opaque backdrop covers the previous lettering when an older watermarked preview is finished again. Existing saved outputs are retained. Editable FCPXML/OTIO timelines remain source exports; finish them through the app to receive a watermarked master.

The CoProd rename changes display names, the app filename and the CLI (`bun run cpd`). Keep the existing bundle ID, `YTAIStudio` executable/module, Keychain service, library/cache paths, `WTS_*` configuration, `@wts/*` workspace names, Remotion composition IDs and OTIO `wts` metadata for compatibility. The public repository and publishing guard still target `isbkch/YouTube-AI-Studio`; do not change that destination as part of a display-name update.

Public history was rewritten on 2026-09-19 to remove those implementations from branches and release tags. Use a fresh clone; do not merge or push old public or premium history back into this repository. Older downloads, clones and GitHub pull-request references cannot be recalled by a Git history rewrite.

A second rewrite on 2026-10-05 removed the premium director from public branches and release tags while preserving unrelated changes. Re-clone after this rewrite; the publishing guard also rejects history containing the former director implementation.

Enable the tracked publishing guard after cloning:

```sh
git config core.hooksPath .githooks
```

The guard rejects premium branch names, other destinations, and commits containing the old repository root or the former director introduction (including merges with old history). It cannot determine whether newly written code is commercially premium; review that boundary before publishing.

Shared fixes should start in this checkout, then be deliberately ported into the private app. Because the public history now has different commit identities, select shared changes individually instead of merging the rewritten public history wholesale into an existing premium branch.

Existing production libraries remain readable. Extra tables left by earlier versions are preserved without exposing their former workflows, so opening the free edition does not delete a creator's saved data.

Unavailable directors in saved creator settings fall back to the Craftsman. Existing plans and their approval hashes remain untouched; re-generate an unsupported storyboard with an available director before building it in the free edition.
