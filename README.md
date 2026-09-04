# StemDeck for LazyCat

This repository packages [StemDeck](https://github.com/stemdeckapp/stemdeck) as a LazyCat LPK v2 application.

StemDeck is a modern stem extraction platform for musicians, producers, and hobbyists. It isolates vocals, drums, bass, piano, guitar, and other stems for practice, transcription, remixing, and creative audio workflows through a modern interactive interface.

## Automatic publishing

The scheduled GitHub workflow:

1. discovers stable semantic-version tags from `ghcr.io/stemdeckapp/stemdeck`;
2. verifies the `linux/amd64` image through `ghcr.nju.edu.cn` with digest matching;
3. updates the package and Manifest when a newer version is available;
4. builds a versioned GitHub Release asset; and
5. publishes that verified asset only to the MiaoMiao private store.

The workflow requires the following GitHub Actions secrets:

- `APPSTORE_URL`
- `APPSTORE_TOKEN`
- `APP_ID` (optional)
- `PRIVATE_STORE_GROUP_CODES` (optional)

Organization secrets must explicitly authorize this repository. A repository secret with the same name overrides the organization secret.

## Local build

```bash
lzc-cli project release -o dist/stemdeck.lpk
lzc-cli lpk info dist/stemdeck.lpk
```

## Data

- Extracted stems, downloaded audio, and settings: `/lzcapp/var/jobs`
- Demucs/Torch cache: `/lzcapp/cache/stemdeck`

## License and attribution

StemDeck and the included icon are provided by the upstream project under the [Apache License 2.0](https://github.com/stemdeckapp/stemdeck/blob/main/LICENSE). This packaging repository does not modify the upstream application image.
