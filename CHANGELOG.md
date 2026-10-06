# Change Log

## [Unreleased]
- Performance: rewrote the import (pull) pipeline so it is much faster and far lighter on large projects.
  - Removed the O(files²) copy filter and the double full-tree MD5 hashing of the local and downloaded trees.
  - Only filter-included files are copied, and a file is written locally only when its contents actually changed.
  - File comparison/copying now runs with a bounded degree of parallelism, avoiding file-descriptor spikes.
  - Reduced the number of local/remote directory scans and made directory walking cheaper.
  - No change to the CRX Package Manager protocol, so this stays compatible with AEM on Java 11.
- Bug fix: import `@xmldom/xmldom` using its current package name so the extension bundles correctly.

## [1.0.4]
- Bug fix: fix behavior when a single .content.xml file is pushed

## [1.0.3]
- Bug fix: fix behavior executing from command palette

## [1.0.0]

- Initial release
