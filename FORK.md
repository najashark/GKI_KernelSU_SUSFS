# najashark fork — notes

Personal fork of [`zzh20188/GKI_KernelSU_SUSFS`](https://github.com/zzh20188/GKI_KernelSU_SUSFS)
(originally forked from `WildKernels/GKI_KernelSU_SUSFS`).

## Additions in this fork

- **`vpnhide` branch** — adds a `use_vpnhide` build option that integrates the
  [VPNHide Next](https://github.com/soranerai/vpnhide_next) in-tree backend
  (`soranerai/vpnhide_next_backend`, `CONFIG_VPNHIDE=y` via its official
  `kpatch/scripts/apply.sh`). Can be combined with the upstream `use_nomount` option
  (VPNHide Next's daemon can use NoMount for filesystem path hiding).

## How to run a build

Actions → **Android 内核构建-自定义** (custom kernel build) → *Run workflow*, branch `vpnhide`.
Example inputs for a Pixel 9 series (zumapro) on firmware CP3A.260905.009:

| input | value |
|---|---|
| kernel_version | `6.1` |
| os_patch_level | `2026-03` → kernel **6.1.162** (matches the stock `6.1.162-android14-11` kernel) |
| use_nomount | ✅ |
| use_vpnhide | ✅ |
| artifact_upload_mode | `上传全部` (AnyKernel3 + boot images + manager) |

## After flashing the kernel (userspace companions)

- **VPNHide Next**: install `vpnhide-bridge.zip` + `vpnhide.apk` from
  <https://github.com/soranerai/vpnhide_next/releases> — the bridge must match the app version.
  Enable the app in LSPosed with **System Framework** in scope.
- **NoMount** (when using the NoMount metamodule): <https://github.com/maxsteeel/nomount/releases>
- SUSFS userspace module: <https://github.com/sidex15/susfs4ksu-module>
