# ONNX Runtime source mirror

Source releases of [ONNX Runtime](https://onnxruntime.ai) by Microsoft, under the MIT license, kept while github.com/microsoft/onnxruntime is unavailable. That repository has returned 404 since 17 November 2026. TypeWhisper builds the speech recognition add-on of its Linux app from these sources.

Each release has a tarball that `git archive` made from the upstream release commit. Git object IDs are hashes of the content, so the commit and tree IDs below name the exact upstream source. Software Heritage archived the upstream repository up to 14 November 2026 under the same IDs.

| Version | Commit | Tree | Tarball | SHA-256 |
| --- | --- | --- | --- | --- |
| 1.28.2 | `33ca9628233dc8f002435e868d4c2e9f82766ca1` | `7841f821d01a42a4ae981810242278258898e61f` | [onnxruntime-1.28.2.tar.gz](https://github.com/TypeWhisper/onnxruntime/releases/download/v1.28.2/onnxruntime-1.28.2.tar.gz) | `060f0b3d8026d46a4c78d10ef99934e0ea2830f43e401486e9617e9a65b25fac` |

Software Heritage: [swh:1:rev:33ca9628233dc8f002435e868d4c2e9f82766ca1](https://archive.softwareheritage.org/swh:1:rev:33ca9628233dc8f002435e868d4c2e9f82766ca1)

## Checking a tarball

The commit came from [intel/onnxruntime](https://github.com/intel/onnxruntime), where it has the same IDs; ROCm/onnxruntime and NVIDIA/onnxruntime have it too. To compare the tarball with it:

```sh
git init check && cd check
git fetch --depth 1 https://github.com/intel/onnxruntime.git 33ca9628233dc8f002435e868d4c2e9f82766ca1
git rev-parse 'FETCH_HEAD^{tree}'   # 7841f821d01a42a4ae981810242278258898e61f
git archive --format=tar --prefix=onnxruntime-1.28.2/ FETCH_HEAD | sha256sum
gzip -dc ../onnxruntime-1.28.2.tar.gz | sha256sum
```

The last two commands print the same hash.

Like GitHub's own archives, the tarball leaves out the Git submodules (`cmake/external/onnx`, `libprotobuf-mutator` and `emsdk`). The ONNX Runtime build fetches what it needs through CMake.

## License

ONNX Runtime is copyright Microsoft Corporation and licensed under the MIT license; see [LICENSE](LICENSE) and [ThirdPartyNotices.txt](ThirdPartyNotices.txt) from the upstream source. This mirror is not affiliated with Microsoft.
