# Lumen Translate releases

Builds and releases of **Lumen Translate**, an iPhone app that translates with large language
models (Claude, OpenAI, DeepSeek, any OpenAI-compatible service or a model on your network) and can
replace Apple Translate as the default translation app on iOS 18.4 and later.

The source is private. The `Build` workflow checks it out with a read-only deploy key and:

- runs the translation core's tests, builds the app and its Translate extension for the iOS
  Simulator, checks the bundle and runs the UI tests, with screenshots in the `ui-test-evidence`
  artifact;
- builds an ad-hoc signed IPA (`LumenTranslate-ipa` artifact), and publishes it as a release when
  a tag is given.

```sh
gh workflow run build.yml -R Elsen823/lumen-translate-releases -f ref=main
gh workflow run build.yml -R Elsen823/lumen-translate-releases -f ref=main -f release=v0.1.0
```

## Installing

Download the IPA from a release and install it with SideStore or AltStore. A sideloaded build
works as a translator inside the app, but free signing can't grant the Translation capability,
so iOS won't list it under Settings → Apps → Default Apps → Translation. For that, build the
source with a paid Apple Developer team.
