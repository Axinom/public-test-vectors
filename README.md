# Axinom test vectors

This document lists the test vectors that Axinom offers for customers, partners and the general public.

These test vectors aim to conform to the latest industry standards, among these the *DASH-IF Interoperability Points* and the *ISO/IEC CD 23000-19 "Common Media Application Format"*.

## Previous versions

* [v6](https://github.com/Axinom/dash-test-vectors/tree/conservative) - a conservative set of test vectors that utilized less modern features for wider compatibility (for the time).
* [v7 & v8](TestVectors-v7-v8.md) - a set of tests vectors that (for the time) intentionally utilized more advanced features - designed to push the boundaries of implementations and to encourage uptake of modern features.

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
* Clear Key license service URL: https://drm-clearkey-testvectors.axtest.net/AcquireLicense

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

# Audio content description

The audio tracks of the "v9" test vectors have descriptive language codes (e.g. `en-x-high` for high-pitched English audio).

# Content keys

The content keys for the v9 test vectors are listed below, individually for each test vector. You may also download CPIX documents with test vector content keys:

* [v9-MultiFormat.xml](ContentKeys/v9-MultiFormat.xml)

# v9-MultiFormat

This is a Multi-DRM video available as both "cbcs" and "cenc" encryption modes, in both HLS and DASH format, with PlayReady, Widevine and FairPlay DRM (where compatible). The HLS variant also contains the keys embedded in the clear (the encrypted content is playable even without DRM).

There are multiple video quality levels from 288p to 4K in 16:9 aspect ratio. There are four audio tracks. There are no text tracks.

Type | 4K 'cenc' | 4K 'cbcs' | 1080p 'cenc' | 1080p 'cbcs' | 4K clear | 1080p clear
-----|-----------|-----------|--------------|--------------|----------|------------
DASH | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cenc/Manifest.mpd) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cbcs/Manifest.mpd) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cenc/Manifest_1080p.mpd) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cbcs/Manifest_1080p.mpd) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Clear/Manifest.mpd) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Clear/Manifest_1080p.mpd)
HLS | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cenc/Manifest.m3u8) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cbcs/Manifest.m3u8) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cenc/Manifest_1080p.m3u8) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Encrypted_Cbcs/Manifest_1080p.m3u8) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Clear/Manifest.m3u8) | [Link](https://media.axprod.net/TestVectors/v9-MultiFormat/Clear/Manifest_1080p.m3u8)

[Download as archive (4.3 GB)](https://media.axprod.net/TestVectors/v9-MultiFormat.7z)

Key ID: `f8c80c25-690f-4736-8132-430e5c6994ce`
Key: `e8mcsd0GI80LUGUFaleh3Q==`

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiNjllNTQwODgtZTllMC00NTMwLThjMWEtMWViNmRjZDBkMTRlIiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsInZlcnNpb24iOjIsImxpY2Vuc2UiOnsiYWxsb3dfcGVyc2lzdGVuY2UiOnRydWV9LCJjb250ZW50X2tleXNfc291cmNlIjp7ImlubGluZSI6W3siaWQiOiJmOGM4MGMyNS02OTBmLTQ3MzYtODEzMi00MzBlNWM2OTk0Y2UiLCJlbmNyeXB0ZWRfa2V5IjoiaVhxNDlaODlzOGRDajBqbTJBN1h6UT09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifV19LCJjb250ZW50X2tleV91c2FnZV9wb2xpY2llcyI6W3sibmFtZSI6IlBvbGljeSBBIiwicGxheXJlYWR5Ijp7Im1pbl9kZXZpY2Vfc2VjdXJpdHlfbGV2ZWwiOjE1MCwicGxheV9lbmFibGVycyI6WyI3ODY2MjdEOC1DMkE2LTQ0QkUtOEY4OC0wOEFFMjU1QjAxQTciXX19XX19.k9OlwW0rUwuf5d5Eb0iO98AFR3qp7qKdFzSbg2PQj78`

# Axinom Encoding Test Vectors (October 2021)

These Multi-DRM videos are produced with Axinom Encoding and they are available with PlayReady, Widevine and FairPlay DRM (where compatible).
There are multiple video quality levels from 288p to 1080p in 16:9 aspect ratio. There are three audio tracks. There are three text tracks.

Type | H264 SingleKey | H264 MultiKey | H265 SingleKey | H265 MultiKey
-----|----------------------|---------------------|----------------------|--------------------
CMAF | [Link (mpd)](https://media.axprod.net/TestVectors/Cmaf/protected_1080p_h264_cbcs/manifest.mpd) <br> [Link (m3u8)](https://media.axprod.net/TestVectors/Cmaf/protected_1080p_h264_cbcs/manifest.m3u8) | [Link (mpd)](https://media.axprod.net/TestVectors/MultiKey/Cmaf_h264_1080p_cbcs/manifest.mpd) <br> [Link (m3u8)](https://media.axprod.net/TestVectors/MultiKey/Cmaf_h264_1080p_cbcs/manifest.m3u8) | [Link (mpd)](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_singlekey/manifest.mpd) <br> [Link (m3u8)](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_singlekey/manifest.m3u8) | [Link (mpd)](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_multikey/manifest.mpd) <br> [Link (m3u8)](https://media.axprod.net/TestVectors/H265/protected_cmaf_1080p_h265_multikey/manifest.m3u8)
DASH | [Link](https://media.axprod.net/TestVectors/Dash/protected_dash_1080p_h264_singlekey/manifest.mpd) | [Link](https://media.axprod.net/TestVectors/MultiKey/Dash_h264_1080p_cenc/manifest.mpd) | [Link](https://media.axprod.net/TestVectors/H265/protected_dash_1080p_h265_singlekey/manifest.mpd) | [Link](https://media.axprod.net/TestVectors/H265/protected_dash_1080p_h265_multikey/manifest.mpd)
HLS | [Link](https://media.axprod.net/TestVectors/Hls/protected_hls_1080p_h264_singlekey/manifest.m3u8) | [Link](https://media.axprod.net/TestVectors/MultiKey/Hls_h264_1080p_cenc/manifest.m3u8) | [Link](https://media.axprod.net/TestVectors/H265/protected_hls_1080p_h265_singlekey/manifest.m3u8) | [Link](https://media.axprod.net/TestVectors/H265/protected_hls_1080p_h265_multikey/manifest.m3u8)

### Content keys
The content keys for the Axinom Encoding Test Vectors (October 2021) are listed below, individually for each test vector
* CMAF
 * [H264-SingleKey](ContentKeys/Axinom-Encoding-Cmaf-H264-protected-SingleKey.xml)
 * [H264-MultiKey](ContentKeys/Axinom-Encoding-Cmaf-H264-protected-MultiKey.xml)
 * [H265-SingleKey](ContentKeys/Axinom-Encoding-Cmaf-H265protected-SingleKey.xml)
 * [H265-MultiKey](ContentKeys/Axinom-Encoding-Cmaf-H265-protected-MultiKey.xml)
* DASH & HLS
 * [H264-SingleKey](ContentKeys/Axinom-Encoding-Dash-Hls-H264-protected-SingleKey.xml)
 * [H264-MultiKey](ContentKeys/Axinom-Encoding-Dash-Hls-H264-protected-MultiKey.xml)
 * [H265-SingleKey](ContentKeys/Axinom-Encoding-Dash-Hls-H265-protected-SingleKey.xml)
 * [H265-MultiKey](ContentKeys/Axinom-Encoding-Dash-Hls-H265-protected-MultiKey.xml)

### X-AxDRM-Message headers
The message headers for the Axinom Encoding Test Vectors (October 2021) are listed below, individually for each test vector
* CMAF
 * [H264-SingleKey](X-AxDRM-Message-headers/Axinom-Encoding-Cmaf-H264-protected-SingleKey-X-AxDRM-Message.xml)
 * [H264-MultiKey](X-AxDRM-Message-headers/Axinom-Encoding-Cmaf-H264-protected-MultiKey-X-AxDRM-Message.xml)
 * [H265-SingleKey](X-AxDRM-Message-headers/Axinom-Encoding-Cmaf-H265-protected-SingleKey-X-AxDRM-Message.xml)
 * [H265-MultiKey](X-AxDRM-Message-headers/Axinom-Encoding-Cmaf-H265-protected-MultiKey-X-AxDRM-Message.xml)
* DASH & HLS
 * [H264-SingleKey](X-AxDRM-Message-headers/Axinom-Encoding-Dash-Hls-H264-protected-SingleKey-X-AxDRM-Message.xml)
 * [H264-MultiKey](X-AxDRM-Message-headers/Axinom-Encoding-Dash-Hls-H264-protected-MultiKey-X-AxDRM-Message.xml)
 * [H265-SingleKey](X-AxDRM-Message-headers/Axinom-Encoding-Dash-Hls-H265-protected-SingleKey-X-AxDRM-Message.xml)
 * [H265-MultiKey](X-AxDRM-Message-headers/Axinom-Encoding-Dash-Hls-H265-protected-MultiKey-X-AxDRM-Message.xml)

# Credits

Original content:

* "Tears of Steel" by [Blender Foundation](https://mango.blender.org)
* [Music by bensound.com](https://www.bensound.com)

# Disclaimer

Axinom does not guarantee the continued availability of the test vectors or the license server nor the accuracy of any descriptive metadata.
