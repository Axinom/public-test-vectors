# Axinom test vectors

This document lists the test vectors that Axinom offers for customers, partners and the general public.

These test vectors aim to conform to the latest industry standards, among these the *DASH-IF Interoperability Points* and the *ISO/IEC CD 23000-19 "Common Media Application Format"*.

## Previous versions

* [v6](https://github.com/Axinom/dash-test-vectors/tree/conservative) - a conservative set of test vectors that utilized less modern features for wider compatibility (for the time).
* [v7 & v8](TestVectors-v7-v8.md) - a set of tests vectors that (for the time) intentionally utilized more advanced features - designed to push the boundaries of implementations and to encourage uptake of modern features.
* [v9](TestVectors-v9.md) - the last set of test vectors packaged by Axinom in-house packager "Makemedia".

# Quick playback in common players

Most modern players include a demo application that enables you to easily play these test vectors:

* [dash.js](https://github.com/Dash-Industry-Forum/dash.js/) includes these test vectors on the [demo page](https://reference.dashif.org/dash.js/nightly/samples/dash-if-reference-player/index.html).
* [Shaka Player](https://github.com/google/shaka-player) includes these test vectors on the [demo page](https://shaka-player-demo.appspot.com/).
* The [ExoPlayer](https://github.com/google/ExoPlayer) demo app can load the [Axinom playlist](https://raw.githubusercontent.com/Axinom/dash-test-vectors/master/axinom.exolist.json) (click this link on an Android device with ExoPlayer demo app installed; [more info](https://google.github.io/ExoPlayer/demo-application.html))

# Usage of Axinom DRM

The test vectors aim to utilize all the major DRM technologies - Widevine, FairPlay and PlayReady -, as applicable. The [W3C Clear Key mechanism](https://www.w3.org/TR/encrypted-media/#clear-key) is also supported for key delivery.

* FairPlay license service URL: https://drm-fairplay-licensing.axtest.net/AcquireLicense
* PlayReady license service URL: https://drm-playready-licensing.axtest.net/AcquireLicense
* Widevine license service URL: https://drm-widevine-licensing.axtest.net/AcquireLicense
* Clear Key license service URL: https://clearkey.axtest.net/AcquireLicense

The license server will provide nonpersistent licenses for the relevant keys upon each license request. To receive a PlayReady or Widevine license, you must add the HTTP header `X-AxDRM-Message` to the license request, with the value being a constant unique to each test vector. This HTTP header is not required in order to receive Clear Key licenses.

Example of license request:

    POST https://drm-widevine-licensing.axtest.net/AcquireLicense HTTP/1.1
    Host: drm-widevine-licensing.axtest.net
    X-AxDRM-Message: eyJ0eX...

# PlayReady compatibility

For widest support, the rights management header version is typically 4.0.0.0, which is compatible with client applications implementing PlayReady version 2.0 or newer. Where required, later versions of the header are utilized (e.g. v4.3.0.0 for PlayReady 'cbcs' content).

# W3C Clear Key compatibility

Clear Key variants of encrypted test vectors are provided using separate manifests that do not signal any other DRM system. This is because DASH-IF Interoperability Points forbid the mixed use of DRM systems and the Clear Key mechanism.

# Customization of DRM behavior

To customize the DRM parameters (e.g. license persistence/expiration or HDCP configuration) you must create your own license tokens instead of using the pre-generated ones provided below. Please refer to the [Axinom DRM Quick Start](https://github.com/Axinom/drm-quick-start) repository for more information on how to achieve this.

# v10

These Multi-DRM test vectors are produced with Axinom Encoding and, compared to v9 vectors, H265 and MPEG-2 TS streams were added. All streams are available with PlayReady, Widevine and FairPlay DRM (where compatible), and have three variants: single-key, multi-key and clear. Each stream contains multiple video quality levels from 288p to 1080p in 16:9 aspect ratio, has three audio tracks and three text tracks.

Type | H264 SingleKey | H264 MultiKey | H264 Clear | H265 SingleKey | H265 MultiKey | H265 Clear
-----|----------------|---------------|------------|----------------|---------------|------------
CMAF | [.mpd](https://media.axprod.net/TestVectors/Cmaf/protected_1080p_h264_cbcs/manifest.mpd) <br> [.m3u8](https://media.axprod.net/TestVectors/Cmaf/protected_1080p_h264_cbcs/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Cmaf-H264-protected-SingleKey.txt) | [.mpd](https://media.axprod.net/TestVectors/MultiKey/Cmaf_h264_1080p_cbcs/manifest.mpd) <br> [.m3u8](https://media.axprod.net/TestVectors/MultiKey/Cmaf_h264_1080p_cbcs/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Cmaf-H264-protected-MultiKey.txt) | [.mpd](https://media.axprod.net/TestVectors/Cmaf/clear_1080p_h264/manifest.mpd) <br> [.m3u8](https://media.axprod.net/TestVectors/Cmaf/clear_1080p_h264/manifest.m3u8) | [.mpd](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_singlekey/manifest.mpd) <br> [.m3u8](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_singlekey/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Cmaf-H265-protected-SingleKey.txt) | [.mpd](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_multikey/manifest.mpd) <br> [.m3u8](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_multikey/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Cmaf-H265-protected-MultiKey.txt) | [.mpd](https://media.axprod.net/TestVectors/H265/clear_cmaf_1080p_h265/manifest.mpd) <br> [.m3u8](https://media.axprod.net/TestVectors/H265/clear_cmaf_1080p_h265/manifest.m3u8)
DASH | [.mpd](https://media.axprod.net/TestVectors/Dash/protected_dash_1080p_h264_singlekey/manifest.mpd) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H264-protected-SingleKey.txt) | [.mpd](https://media.axprod.net/TestVectors/MultiKey/Dash_h264_1080p_cenc/manifest.mpd) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H264-protected-MultiKey.txt) | [.mpd](https://media.axprod.net/TestVectors/Dash/not_protected_dash_1080p_h264/manifest.mpd) | [.mpd](https://media.axprod.net/TestVectors/H265/protected_dash_1080p_h265_singlekey/manifest.mpd) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H265-protected-SingleKey.txt) | [.mpd](https://media.axprod.net/TestVectors/H265/protected_dash_1080p_h265_multikey/manifest.mpd) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H265-protected-MultiKey.txt) | [.mpd](https://media.axprod.net/TestVectors/H265/clear_dash_1080p_h265/manifest.mpd)
HLS | [.m3u8](https://media.axprod.net/TestVectors/Hls/protected_hls_1080p_h264_singlekey/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H264-protected-SingleKey.txt) | [.m3u8](https://media.axprod.net/TestVectors/MultiKey/Hls_h264_1080p_cenc/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H264-protected-MultiKey.txt) | [.m3u8](https://media.axprod.net/TestVectors/Hls/not_protected_hls_1080p_h264/manifest.m3u8) | [.m3u8](https://media.axprod.net/TestVectors/H265/protected_hls_1080p_h265_singlekey/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H265-protected-SingleKey.txt) | [.m3u8](https://media.axprod.net/TestVectors/H265/protected_hls_1080p_h265_multikey/manifest.m3u8) <br> [Token & Key](ContentKeys/Axinom-Encoding-Dash-Hls-H265-protected-MultiKey.txt) | [.m3u8](https://media.axprod.net/TestVectors/H265/clear_hls_1080p_h265/manifest.m3u8)

[Download CMAF as archive (4 GB)](https://media.axprod.net/TestVectors/v10_Cmaf.7z) | [Download DASH as archive (4 GB)](https://media.axprod.net/TestVectors/v10_Dash.7z) | [Download HLS as archive (4 GB)](https://media.axprod.net/TestVectors/v10_Hls.7z)

# Credits

Original content:

* "Tears of Steel" by [Blender Foundation](https://mango.blender.org)

# Disclaimer

Axinom does not guarantee the continued availability of the test vectors or the license server nor the accuracy of any descriptive metadata.
