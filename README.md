# ask-cdx

This repository owns the packaged `ask-cdx` source consumed by the OpenWrt
integration tree.

The actual kernel module source lives under `cdx-5.03.1/` so the OpenWrt
package can fetch a pinned git revision, unpack it into `build_dir`, and build
it through the standard package workflow.

`openwrt/package/kernel/ask-cdx/` remains responsible for:
- package metadata and dependency declarations
- OpenWrt init/service integration under `files/`
- any future OpenWrt-local patch queue, if one is added intentionally

For reproducible packaging, OpenWrt should always pin an exact commit or tag
from this repository through `PKG_SOURCE_VERSION` and verify the archive with
`PKG_MIRROR_HASH`. Tags should mark packaging-relevant source states; commits
must stay immutable once referenced by a released OpenWrt package.
