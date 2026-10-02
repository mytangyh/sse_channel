# Flutter 3.27.4 compatibility

Branch: `compat/flutter-3.27.4`. Upstream Git baseline: `90ec12606e33e067dba1e4f18bd6869d419dbf7c` from jamiewest/sse_channel, version 0.2.2. FVM pins Flutter 3.27.4 / Dart 3.6.2. Package exports and license remain upstream's.

The Git baseline does not contain its exported src/sse_channel.dart or src/util.dart. These two lib files and the transformer test were recovered from the same released package archive at https://pub.dev/api/archives/sse_channel-0.2.2.tar.gz. Archive SHA256: `ad85fda353fae12533fd762dbd3ff275e710f216644e39459bf11a138124acad`. The published implementation's incorrect ../../src/util.dart import is corrected to util.dart.

Other patches set actual compatible SDK, async, stream_channel and sse constraints and apply the Dart 3.6 formatter. Current resolution uses sse 4.1.8. No placeholder implementation or protocol rewrite was introduced.

2026-10-02: all 13 upstream tests passed, including local HTTP SSE exchange, reconnect and Last-Event-ID behavior. Format checks pass for eight files; strict analysis reports no issues. Run `fvm dart test --reporter expanded` from this root. Full logs are in the GenUI compatibility checkout.

The compatibility branch is maintained in `mytangyh/sse_channel`. The temporary override has been removed; there are no locked path sources, and Dart 3.6.2 pub get --enforce-lockfile plus the 13-test profile pass. GenUI's delivery manifest pins the exact compatibility commit.

An exported Git baseline with the current uncommitted patches also passes the full profile in a temporary directory and fresh Pub cache. The root lockfile's hosted URLs were subsequently normalized to pub.dev without changing versions or archive hashes, and strict resolution at pub.dev passes. Verification scripts select pub.dev for their process and restore the previous setting. This evidence does not represent a final remote fork clone.
