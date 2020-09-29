# Axinom DASH test vectors

This document lists the test vectors that Axinom offers for customers, partners and the general public.

These test vectors make use of modern DASH features and conform to the latest industry standards, among these the *DASH-IF Interoperability Points* and the upcoming *ISO/IEC CD 23000-19 "Common Media Application Format"* (or its latest draft).

As such, the scope of features utilized intentionally exceeds that seen with more traditional conservative test vectors - the below data is designed to push the boundaries of implementations and to encourage uptake of modern features. Please use the [conservative branch](https://github.com/Axinom/dash-test-vectors/tree/conservative) for a more widely-compatible (but less modern) version of the content.

# Quick playback in common players

Most modern players include a demo application that enables you to easily play these test vectors:

* [dash.js](https://github.com/Dash-Industry-Forum/dash.js/) includes these test vectors on the [demo page](https://reference.dashif.org/dash.js/nightly/samples/dash-if-reference-player/index.html).
* [Shaka Player](https://github.com/google/shaka-player) includes these test vectors on the [demo page](https://shaka-player-demo.appspot.com/).
* The [ExoPlayer](https://github.com/google/ExoPlayer) demo app can load the [Axinom playlist](https://raw.githubusercontent.com/Axinom/dash-test-vectors/master/axinom.exolist.json) (click this link on an Android device with ExoPlayer demo app installed; [more info](https://google.github.io/ExoPlayer/demo-application.html))

# Usage of Axinom DRM

All test vectors can be played back using both the PlayReady and Widevine DRM technologies for decryption. The [W3C Clear Key mechanism](https://www.w3.org/TR/encrypted-media/#clear-key) is also supported for key delivery.

PlayReady license server URL: https://drm-playready-licensing.axtest.net/AcquireLicense

Widevine license server URL: https://drm-widevine-licensing.axtest.net/AcquireLicense

Clear Key license server URL: https://drm-clearkey-testvectors.axtest.net/AcquireLicense

The license server will provide nonpersistent licenses for the relevant keys upon each license request. To receive a PlayReady or Widevine license, you must add the HTTP header `X-AxDRM-Message` to the license request, with the value being a constant unique to each test vector. This HTTP header is not required in order to receive Clear Key licenses.

Example of license request:

    POST https://drm-widevine-licensing.axtest.net/AcquireLicense HTTP/1.1
    Host: drm-widevine-licensing.axtest.net
    X-AxDRM-Message: eyJ0eX...

# PlayReady compatibility

The rights management header version is 4.0.0.0, which is compatible with client applications implementing PlayReady version 2.0 or newer.

# W3C Clear Key compatibility

Clear Key variants of encrypted test vectors are provided using separate manifests that do not signal any other DRM system. This is because DASH-IF Interoperability Points forbid the mixed use of DRM systems and the Clear Key mechanism.

# Customization of DRM behavior

To customize the DRM parameters (e.g. license persistence/expiration or HDCP configuration) you must create your own license tokens instead of using the pre-generated ones provided below. Please refer to the [Axinom DRM Quick Start](https://github.com/Axinom/drm-quick-start) repository for more information on how to achieve this.

# Audio content description

The audio tracks of the "v7" test vectors contain the same content but at a different pitch.

* "en" language is the original audio.
* "en-AU" language is the same content at a higher pitch.
* "et-ET" language is the same content at a lower pitch.

The audio tracks of the "v8" and "v9" test vectors have more descriptive language codes (e.g. `en-x-high` for high-pitched English audio).

# Content keys

The content keys for the v7 and v9 test vectors are listed below, individually for each test vector. You may also download CPIX documents with test vector content keys:

* [ContentKeys-v7.xml](ContentKeys/ContentKeys-v7.xml).
* [v9-MultiFormat.xml](ContentKeys/v9-MultiFormat.xml).

For v8 test vectors, the content keys are not listed in this document for brevity. They can be found in the following CPIX documents:

* [Axinom-v8-MultiContent-Period01.xml](ContentKeys/Axinom-v8-MultiContent-Period01.xml)
* [Axinom-v8-MultiContent-Period02.xml](ContentKeys/Axinom-v8-MultiContent-Period02.xml)
* [Axinom-v8-MultiContent-Period03.xml](ContentKeys/Axinom-v8-MultiContent-Period03.xml)
* [Axinom-v8-MultiContent-Period04.xml](ContentKeys/Axinom-v8-MultiContent-Period04.xml)
* [Axinom-v8-MultiContent-Period05.xml](ContentKeys/Axinom-v8-MultiContent-Period05.xml)
* [Axinom-v8-MultiContent-Period06.xml](ContentKeys/Axinom-v8-MultiContent-Period06.xml)
* [Axinom-v8-MultiContent-Period07.xml](ContentKeys/Axinom-v8-MultiContent-Period07.xml)
* [Axinom-v8-MultiContent-Period08.xml](ContentKeys/Axinom-v8-MultiContent-Period08.xml)
* [Axinom-v8-MultiContent-Period09.xml](ContentKeys/Axinom-v8-MultiContent-Period09.xml)
* [Axinom-v8-MultiContent-Period10.xml](ContentKeys/Axinom-v8-MultiContent-Period10.xml)

# v7-MultiDRM-SingleKey

Single-period presentation using DASH live profile. All video and audio representations are encrypted using the same key. Text representations are not encrypted.

Different variants of the test vector are provided in the form of different manifests that reference the same media segments. The manifests contain the license server URL for Clear Key but not for PlayReady or Widevine.

PlayReady and Widevine | W3C Clear Key
:----------------------|:---------------
[4K variant](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest.mpd) | [4K variant](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_ClearKey.mpd)
[1080p variant](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_1080p.mpd) | [1080p variant](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_1080p_ClearKey.mpd)
[Audio-only variant](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_AudioOnly.mpd) | [Audio-only variant](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_AudioOnly_ClearKey.mpd)

[Download as archive](https://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey-Update1.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
Video          | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
Text           | 5x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. All DRM system initialization and signaling data is in the manifest - the segments themselves only contain encryption-related data in a DRM-agnostic manner.

Adaptation set | Key ID                               | Content key
:--------------|:-------------------------------------|:------------------------
Video (all)    | 9eb4050d-e44b-4802-932e-27d75083e266 | FmY0xnWCPCNaSpRG+tUuTQ==
Audio (all)    | 9eb4050d-e44b-4802-932e-27d75083e266 | FmY0xnWCPCNaSpRG+tUuTQ==
Text (all)     | -                                    | -

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsInZlcnNpb24iOjIsImxpY2Vuc2UiOnsiYWxsb3dfcGVyc2lzdGVuY2UiOnRydWV9LCJjb250ZW50X2tleXNfc291cmNlIjp7ImlubGluZSI6W3siaWQiOiI5ZWI0MDUwZC1lNDRiLTQ4MDItOTMyZS0yN2Q3NTA4M2UyNjYiLCJlbmNyeXB0ZWRfa2V5IjoibEszT2pITFlXMjRjcjJrdFI3NGZudz09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifV19LCJjb250ZW50X2tleV91c2FnZV9wb2xpY2llcyI6W3sibmFtZSI6IlBvbGljeSBBIiwicGxheXJlYWR5Ijp7Im1pbl9kZXZpY2Vfc2VjdXJpdHlfbGV2ZWwiOjE1MCwicGxheV9lbmFibGVycyI6WyI3ODY2MjdEOC1DMkE2LTQ0QkUtOEY4OC0wOEFFMjU1QjAxQTciXX19XX19.W2FbPDSDaq-LeeLfOnbpTMa-zCmXh8RLChEVDYvdcVw`

# v7-MultiDRM-MultiKey

Single-period presentation using DASH live profile. Video and audio representations are encrypted using multiple keys. Text representations are not encrypted.

Different variants of the test vector are provided in the form of different manifests that reference the same media segments. The manifests contain the license server URL for Clear Key but not for PlayReady or Widevine.

PlayReady and Widevine | W3C Clear Key
:----------------------|:---------------
[4K variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest.mpd) | [4K variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_ClearKey.mpd)
[1080p variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_1080p.mpd) | [1080p variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_1080p_ClearKey.mpd)
[Audio-only variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_AudioOnly.mpd) | [Audio-only variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_AudioOnly_ClearKey.mpd)

[Download as archive](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-Update1.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
Video          | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
Text           | 5x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. All DRM system initialization and signaling data is in the manifest - the segments themselves only contain encryption-related data in a DRM-agnostic manner.

Adaptation set        | Key ID                               | Content key
:---------------------|:-------------------------------------|:------------------------
Video (288p...480p)   | 80399bf5-8a21-4014-8053-e27e748e98c0 | 3aHppzZ2g3Y3wK1uNnUXmg==
Video (720p...1080p)  | 90953e09-6cb2-49a3-a260-7a5fefead499 | zsmKW7Mq9Unz5R7oUGeF8w==
Video (1440p...2160p) | 0e4da92b-d0e8-4a66-8c3f-c25a97eb6532 | UmYYfGb7znuoFAQM79ayHw==
Audio (en)            | 585f233f-3072-46f1-9fa4-6dc22c66a014 | jayKpC3tmPq4YKXkapa8FA==
Audio (en-AU)         | 4222bd78-bc45-41bf-b63e-6f814dc391df | GAMi9v92b9ca5yBwaptN+Q==
Audio (et-ET)         | -                                    | -
Text (all)            | -                                    | -

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsInZlcnNpb24iOjIsImxpY2Vuc2UiOnsiYWxsb3dfcGVyc2lzdGVuY2UiOnRydWV9LCJjb250ZW50X2tleXNfc291cmNlIjp7ImlubGluZSI6W3siaWQiOiI4MDM5OWJmNS04YTIxLTQwMTQtODA1My1lMjdlNzQ4ZTk4YzAiLCJlbmNyeXB0ZWRfa2V5IjoibGlOSnFWYVlrTmgrTUtjeEpGazdJZz09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImlkIjoiOTA5NTNlMDktNmNiMi00OWEzLWEyNjAtN2E1ZmVmZWFkNDk5IiwiZW5jcnlwdGVkX2tleSI6ImtZdEhIdnJyZkNNZVZkSjZMa2Jrbmc9PSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJpZCI6IjBlNGRhOTJiLWQwZTgtNGE2Ni04YzNmLWMyNWE5N2ViNjUzMiIsImVuY3J5cHRlZF9rZXkiOiI3dzdOWkhITE1nSjRtUUtFSzVMVE1RPT0iLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiaWQiOiI1ODVmMjMzZi0zMDcyLTQ2ZjEtOWZhNC02ZGMyMmM2NmEwMTQiLCJlbmNyeXB0ZWRfa2V5IjoiQWM0VVVtWXRCSjVuUFE5TjE1cmMzZz09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImlkIjoiNDIyMmJkNzgtYmM0NS00MWJmLWI2M2UtNmY4MTRkYzM5MWRmIiwiZW5jcnlwdGVkX2tleSI6Ik82Rk8wZnFTV29wcDdiamMvRDRsTUE9PSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn1dfSwiY29udGVudF9rZXlfdXNhZ2VfcG9saWNpZXMiOlt7Im5hbWUiOiJQb2xpY3kgQSIsInBsYXlyZWFkeSI6eyJtaW5fZGV2aWNlX3NlY3VyaXR5X2xldmVsIjoxNTAsInBsYXlfZW5hYmxlcnMiOlsiNzg2NjI3RDgtQzJBNi00NEJFLThGODgtMDhBRTI1NUIwMUE3Il19fV19fQ.nMT-_Xor0ROh9sSAbDGu5nsMjrsCJ1W7FZGcr2xpqBY`

# v7-MultiDRM-MultiKey-MultiPeriod

Multi-period presentation using DASH live profile. Video and audio representations are encrypted using multiple keys, some of which change between periods. Text representations are not encrypted.

The two periods contain the same content encrypted with different keys.

Different variants of the test vector are provided in the form of different manifests that reference the same media segments. The manifests contain the license server URL for Clear Key but not for PlayReady or Widevine.

PlayReady and Widevine | W3C Clear Key
:----------------------|:---------------
[4K variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest.mpd) | [4K variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_ClearKey.mpd)
[1080p variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_1080p.mpd) | [1080p variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_1080p_ClearKey.mpd)
[Audio-only variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_AudioOnly.mpd) | [Audio-only variant](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_AudioOnly_ClearKey.mpd)

[Download as archive](https://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod-Update1.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
Video          | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
Text           | 5x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. All DRM system initialization and signaling data is in the manifest - the segments themselves only contain encryption-related data in a DRM-agnostic manner.

## Period 1

Adaptation set        | Key ID                               | Content key
:---------------------|:-------------------------------------|:------------------------
Video (288p...480p)   | 0872786e-f9e7-465f-a3a2-4e5b0ef8fa45 | wyYRebq2Hu7JedLUBpURzw==
Video (720p...1080p)  | c14f0709-f2b9-4427-916b-61b52586506a | 7fsXeXJHs8enQ0SEfkhTBQ==
Video (1440p...2160p) | 8b029e51-d56a-44bd-910f-d4b5fd90fba2 | yInMol6zCzsSjrg06k2k+g==
Audio (en)            | 2d6e9387-60ca-4145-aec2-c40837b4b026 | QtC/8bYPe+SfF9YDSE0MuQ==
Audio (en-AU)         | de02f07f-a098-4ee0-b556-907c0d17fbbc | GQnGyyKBez4x8aNTD6cNzw==
Audio (et-ET)         | -                                    | -
Text (all)            | -                                    | -

## Period 2

Adaptation set        | Key ID                               | Content key
:---------------------|:-------------------------------------|:------------------------
Video (288p...480p)   | 0872786e-f9e7-465f-a3a2-4e5b0ef8fa45 | wyYRebq2Hu7JedLUBpURzw==
Video (720p...1080p)  | 914e69f4-0ab3-4534-9e9f-9853615e26f6 | 0DBllUYESc5WdSJMebqlBA==
Video (1440p...2160p) | da4445c2-db5e-48ef-b096-3ef347b16c7f | 0aUpR1ASGSQ1UGxWxY7ozA==
Audio (en)            | 29f05e8f-a1ae-46e4-80e9-22dcd44cd7a1 | BxGxfISpDLtBCXJkyQG3Mg==
Audio (en-AU)         | -                                    | -
Audio (et-ET)         | 69fe7077-dadd-4b55-96cd-c3edb3991853 | 7TqCUJKmSlCbdIeJ0xbAgQ==
Text (all)            | -                                    | -

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsInZlcnNpb24iOjIsImxpY2Vuc2UiOnsiYWxsb3dfcGVyc2lzdGVuY2UiOnRydWV9LCJjb250ZW50X2tleXNfc291cmNlIjp7ImlubGluZSI6W3siaWQiOiIwODcyNzg2ZS1mOWU3LTQ2NWYtYTNhMi00ZTViMGVmOGZhNDUiLCJlbmNyeXB0ZWRfa2V5IjoiUHc2K2VFWU5jdmpZYmZzaDNYM2ZtZz09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImlkIjoiYzE0ZjA3MDktZjJiOS00NDI3LTkxNmItNjFiNTI1ODY1MDZhIiwiZW5jcnlwdGVkX2tleSI6Ii8xK2ZOaWgzOG1xUnY0eWNZem50L3c9PSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJpZCI6IjhiMDI5ZTUxLWQ1NmEtNDRiZC05MTBmLWQ0YjVmZDkwZmJhMiIsImVuY3J5cHRlZF9rZXkiOiJrcTBKdVpFanBGTjhzYVRtdDU2ME9nPT0iLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiaWQiOiIyZDZlOTM4Ny02MGNhLTQxNDUtYWVjMi1jNDA4MzdiNGIwMjYiLCJlbmNyeXB0ZWRfa2V5IjoiVGNSUWVCV3hFb0hPS0hyYWQ0U2VWUT09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImlkIjoiZGUwMmYwN2YtYTA5OC00ZWUwLWI1NTYtOTA3YzBkMTdmYmJjIiwiZW5jcnlwdGVkX2tleSI6InBvZW5jUzdHZ21lR0Zlb0o2UEVBVFE9PSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJpZCI6IjkxNGU2OWY0LTBhYjMtNDUzNC05ZTlmLTk4NTM2MTVlMjZmNiIsImVuY3J5cHRlZF9rZXkiOiJlaUkvTXNsbHJRNHdDbFJUL0xObUNBPT0iLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiaWQiOiJkYTQ0NDVjMi1kYjVlLTQ4ZWYtYjA5Ni0zZWYzNDdiMTZjN2YiLCJlbmNyeXB0ZWRfa2V5IjoiMncremR2cXJwRFYzeFIwYkp5NHVndz09IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImlkIjoiMjlmMDVlOGYtYTFhZS00NmU0LTgwZTktMjJkY2Q0NGNkN2ExIiwiZW5jcnlwdGVkX2tleSI6Ii94bFNIcHh3cXUzZ28vZ2xwbVNnYVE9PSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJpZCI6IjY5ZmU3MDc3LWRhZGQtNGI1NS05NmNkLWMzZWRiMzk5MTg1MyIsImVuY3J5cHRlZF9rZXkiOiJ6dTZpdXpOMnBzaTBaU3hRaUFUa1JRPT0iLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9XX0sImNvbnRlbnRfa2V5X3VzYWdlX3BvbGljaWVzIjpbeyJuYW1lIjoiUG9saWN5IEEiLCJwbGF5cmVhZHkiOnsibWluX2RldmljZV9zZWN1cml0eV9sZXZlbCI6MTUwLCJwbGF5X2VuYWJsZXJzIjpbIjc4NjYyN0Q4LUMyQTYtNDRCRS04Rjg4LTA4QUUyNTVCMDFBNyJdfX1dfX0.R7aHvOHPBV-f2VfjeQC0AOi9axZI_xGIlpB-OScAzy4`

# v7-Clear

This is a clear (no encryption) variant of the above, to provide some comparison capability for diagnostics and debugging. The media samples inside are (binary) equal to the encrypted variants.

[Single-period 4K variant](https://media.axprod.net/TestVectors/v7-Clear/Manifest.mpd)

[Single-period 1080p variant](https://media.axprod.net/TestVectors/v7-Clear/Manifest_1080p.mpd)

[Single-period audio-only variant](https://media.axprod.net/TestVectors/v7-Clear/Manifest_AudioOnly.mpd)

[Multi-period 4K variant](https://media.axprod.net/TestVectors/v7-Clear/Manifest_MultiPeriod.mpd)

[Multi-period 1080p variant](https://media.axprod.net/TestVectors/v7-Clear/Manifest_MultiPeriod_1080p.mpd)

[Multi-period audio-only variant](https://media.axprod.net/TestVectors/v7-Clear/Manifest_MultiPeriod_AudioOnly.mpd)

[Download as archive](https://media.axprod.net/TestVectors/v7-Clear.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
Video          | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
Text           | 5x IMSC 1.0 Text Profile

# v8-MultiContent

This is a multi-period presentation using DASH live profile. The content in each period is markedly different from preceding and following periods, with changes occurring in the available set of audio and text languages, content keys, quality levels and video aspect ratio.

This test vector is intended to simulate a recorded live stream that delivers different types of content in sequence (e.g. movies with different aspect ratios and language availability, interspersed with advertisements).

Each period is encrypted with up to 4 different keys: an audio key, an SD video key, an HD video key and an UHD video key. PlayReady and Widevine DRM signaling is present. A clear variant with no encryption is also available.

Encrypted | Clear
:---------------|--------------
[Manifest](https://media.axprod.net/TestVectors/v8-MultiContent/Encrypted/Manifest.mpd) | [Manifest](https://media.axprod.net/TestVectors/v8-MultiContent/Clear/Manifest.mpd)
[Download as archive](https://media.axprod.net/TestVectors/v8-MultiContent-Encrypted.7z) | [Download as archive](https://media.axprod.net/TestVectors/v8-MultiContent-Clear.7z)

For diagnostic purposes, you can also play each period individually by constructing relative URLs matching the pattern [Period01/Manifest.mpd](https://media.axprod.net/TestVectors/v8-MultiContent/Encrypted/Period01/Manifest.mpd).

In each period, tracks matching the below parameters are present:

Track          | Parameters
:--------------|:----------
Video          | 1..7 x H.264 High Profile, 288p...2160p @ max 6 Mbps
Video          | 1..7 x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 1..N x HE-AACv2 at 64 kbps, stereo
Text           | 0..M x WebVTT
Text           | 0..M x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. All DRM system initialization and signaling data is in the manifest - the segments themselves only contain encryption-related data in a DRM-agnostic manner.

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwidmVyc2lvbiI6MSwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsInZlcnNpb24iOjIsImxpY2Vuc2UiOnsiYWxsb3dfcGVyc2lzdGVuY2UiOnRydWV9LCJjb250ZW50X2tleXNfc291cmNlIjp7ImlubGluZSI6W3siZW5jcnlwdGVkX2tleSI6IjdYSEttbi9zZnZ1UExXdFB0R1RaRFE9PSIsImlkIjoiMWViMzMyYjItNzQzNy00OWFlLWJmMzktZTcwMDEwY2I2MjBiIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJzUXRGWDh6Y2o5bEVyZ282RDdjNGh3PT0iLCJpZCI6IjlhYTYwZTNhLTljOTEtNDc0ZC04OTM3LTdkOGIzMjU5Y2NjZCIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoibzBSVjRra25UTUpMUWR5WHVrVWVPZz09IiwiaWQiOiI1OTQ3OTdhNy02YjAwLTQ2NzMtYjJlMS1hZWZjNTUyYjFiYmMiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6ImVZdXZSL0tQYVgrV1huN0ZMOVpDcUE9PSIsImlkIjoiYWFlMjU3NTgtZTQ4MS00ODk1LTgxMzMtYjgwOTQ4MzM5M2QwIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiIwQ1BUWVpMWmk1SmhZZ0NiZThKTnhRPT0iLCJpZCI6IjkzMTEzZDVlLTJlYzgtNDNjMS05MDgzLTEwZjNkZTIwM2EyOSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiUVBSUGtDT216c05GSXVwKzNIWndZZz09IiwiaWQiOiJlNDg3NzAzNy00Mzc2LTRlZGQtODU4Ni0xNDUxOTQzNTg4MDMiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IlVra1lGdE1yRjJ5RE9Ib2FsSkZmUmc9PSIsImlkIjoiZThhZDU5NzItODgxOS00MzI2LWFkNmEtZjlhMTUxNjhiY2E3IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJkdWhnRVJSRkRiZlFEcnlwUWRCUUVRPT0iLCJpZCI6IjI2YTA5MzlmLTNhMGMtNDI4OS1hZDZiLWJiNWNlYzE3ZmY0MCIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiMU5QenVDUkszenhtalgrcVlmdTVtdz09IiwiaWQiOiJhNWVkNzE3My0zNzgxLTRjNzQtOTBhYy1mMDgzNGVmMWExYzgiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6ImF1UExCY3djZk5xUkU1dVhXVGdTS1E9PSIsImlkIjoiMzI5ZjUzM2UtZmE3Ny00MDcwLWI2NWItMzkyOTgwYmFkYTBkIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiI2NkE1MnFiZEcyQlg3SUhTaml6WUpRPT0iLCJpZCI6IjE5N2Y4Yjg0LTNiZjItNDg2MC1iMjNhLTVjNTQ2MjhhZDBiMSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiWEhRQTdZaURkZnBMTTlBbHBySUMrZz09IiwiaWQiOiI0ZWNkZDRjNy00ZDI5LTQzZmYtYmRhZi0wMmI3NjkwMGYxMjMiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6Im5QajVpdzdSL2Q0dFpnSmZLaERYWGc9PSIsImlkIjoiZWU3NDZkMTItYTQ4OC00OTc3LWIxY2EtNzdhMTAxYmI0ODNjIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJ5U1Vma0Q5ZEliK0ExNmoydHNzNDV3PT0iLCJpZCI6IjQ5NGY5NmUxLTM1MzUtNGE4NC05MWMxLWZhYTI4M2IwNmE1NCIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoicmVQdWxpeDR4Vk1keWxSdWlwbkUrQT09IiwiaWQiOiI1YzA3YmZmNC1jNzBiLTRkMDItYTM3OC0zODMyNmY5MTAwMGMiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6ImpXN2dhNGsrTHA3cVk3eGZqOXRweWc9PSIsImlkIjoiMzI4M2MzNWUtYWUyYy00ZjhjLThhNDktNGE3NTBhZWRmMTQyIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJLdHNNYlZRM0JXL1dwQlIwSlQwa2R3PT0iLCJpZCI6IjhkNzdiOWM0LTdmNmQtNDdmOS04NTYyLWE1ZTVlNGMzNTFjZSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiWFFMZkpBSmZKMXJ6UUxkY0VFYzkvZz09IiwiaWQiOiI4MjMxNzFkNy1kZmMxLTRkMGUtODAzZi00MGExZjVlNDM4NjgiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IkdIUElTWE12SlhCelpLRkJtWTFxQmc9PSIsImlkIjoiYzE2MmFjN2QtNDBkNy00NmMwLWIyY2QtZTk0MjdkNDM5YzMyIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJ2bzJhamlLaWV6Yk9xY2tyNTN0U3B3PT0iLCJpZCI6ImZhYTZkNmY1LTM1MDEtNDg1MS05MmViLWM3ZGE0NDRlY2FhYyIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiODZCQTBQdjBheThSZXlaTjN4SVhrZz09IiwiaWQiOiJmYzQ5YjcxMS0xY2I2LTQwYTctOTg0MC04M2M0MWI1NWI5OWIiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6Im1IQWxEWmtDWEFqQkdaS0dodGN2aXc9PSIsImlkIjoiNDNkMDIyMDQtODYwOS00ZDQ2LTk5YWMtNDI1YTViNDgwMDk4IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJ3bWhjREdZcG84YlZBSit0OGF4SUZnPT0iLCJpZCI6IjRkNmU0OTZhLTFmOTgtNGVlOC04Zjg3LTRiMTAzYmQzOGQwZiIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiT3ZxYXdjQlVBUTdwczZPTGFKdk9GZz09IiwiaWQiOiJjNGUwZDlmNy1kNDgyLTQxYzMtOGNiYi05N2IxMTJkNzJlNjYiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IjN3UzJHaXpsVnBrbjQ5UURMcXBQYWc9PSIsImlkIjoiMWMyZGUxZTQtZWQzMC00NDUyLWExMTUtMDkyM2I5NDBjNGVkIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJTNWRGQ25yRUNjREswOEVreHllY3lRPT0iLCJpZCI6ImRjZjQzODVmLTM1MDUtNGZmNS1iMDU1LTQ2MWQ1YTA3ZjBmNSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiUGdFSHIrQ2t3clhNK2VJYWdSeXhvdz09IiwiaWQiOiJmMzI0ZjA0ZS03YzczLTRmMzctODEzNS1jODlmOGM0ZTZjZjQiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IkpMelFGRjF6eDBaWTM2WEk3WkdFWlE9PSIsImlkIjoiNWNiNTNkZDgtMTI5NC00YzhlLTk2NGUtMjU4NjlkNTNhMjRhIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJVOHBRdW1HUmtrTGppSEg1cjlqWGhnPT0iLCJpZCI6IjA1NjgyYTI2LTg4NzctNDZkMy05NDY1LTEwNGEzYTQwMDEwYSIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiVUlMNko0ZHNkSkY2L21BMzV0ci9UUT09IiwiaWQiOiJiY2U1MzQxMC0zYjBjLTQ5MTQtODdhMy03MjM2M2NhMTc1MzEiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IjN6QmltQ3NjZTE1dmJFdDJvMzRIYVE9PSIsImlkIjoiNGY0ZjhhMWMtMzIwMi00NmFlLTgwOWUtNGZjZjkzM2VlNjU0IiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJDVHdTU3RQMnV1QjVZdStNUGpZY29RPT0iLCJpZCI6Ijg1MmNkN2Y3LTQwZTktNDgyZC04MjI1LWRjYmM4ZTA4ZGI4YiIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoibW5tdG5RZUdibStlQTM3a3p0Wi9FUT09IiwiaWQiOiJlZmRkYjhlZS04Mjc4LTQ0MzYtYTY5OC03MmI4MDNkMDUwZGIiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6Im9wYnF5bWVUYk91VmpSZ2IyRzB6VXc9PSIsImlkIjoiZDViZGJhNTMtNjA2Zi00ZDQ2LTg4OGQtYTFlYjQ0Y2Q1ZjQxIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJiSWRsOFhoVmdobmc4Tis4cUZVbFRnPT0iLCJpZCI6ImFlZDQ5NjA5LTUwOTktNDExOC05YjA4LWI5NTM4ZGIwMGMwYyIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiSnVJL1QxK3lxS3NRT3kyNkRvNG5mZz09IiwiaWQiOiI3YjVjMWU5Zi1mOGI4LTQ5OTItYWEzZS1hMDg1ZmMzNjczMTEiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IjNpWnVGcWpYd284YjdZZGpsSmVFT1E9PSIsImlkIjoiNWJlNDBlYmYtMmVhNC00OWZiLWI2ZWMtYjA5ZGU1YWI2MTdmIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifSx7ImVuY3J5cHRlZF9rZXkiOiJoQ3gybzJxQlJKL2hiZVNqKzY5dHF3PT0iLCJpZCI6ImU1MzBkZjFiLWZmN2UtNDJhNC1iNTNhLThkNmRlNjhmMDAxMCIsInVzYWdlX3BvbGljeSI6IlBvbGljeSBBIn0seyJlbmNyeXB0ZWRfa2V5IjoiOG95aUYzSlBOZ3N3S09qNWtaNUhPQT09IiwiaWQiOiJiOTQ5ODc0NS04MmVhLTRmZmEtYWIyYi1kNzM3ZWY1NGY4NjMiLCJ1c2FnZV9wb2xpY3kiOiJQb2xpY3kgQSJ9LHsiZW5jcnlwdGVkX2tleSI6IkxLOExDU2NvM0JmWGV4SzJYdFlGUkE9PSIsImlkIjoiNGY1Mjk3NWItZTlmMy00ZmQ3LWJiODktNDAzYjI4MDBlOGNmIiwidXNhZ2VfcG9saWN5IjoiUG9saWN5IEEifV19LCJjb250ZW50X2tleV91c2FnZV9wb2xpY2llcyI6W3sibmFtZSI6IlBvbGljeSBBIiwicGxheXJlYWR5Ijp7Im1pbl9kZXZpY2Vfc2VjdXJpdHlfbGV2ZWwiOjE1MCwicGxheV9lbmFibGVycyI6WyI3ODY2MjdEOC1DMkE2LTQ0QkUtOEY4OC0wOEFFMjU1QjAxQTciXX19XX19.qVGhYNHDU1fQUFPbfaWbku1_0k40vG9BSsXeOchlXc8`

# Live-Clear

This is a live presentation supplied simultaneously as DASH and HLS. This is a real live stream from a development server that is expected to stay up 24/7. Given its development nature, it may experience occasional temporary disruptions.

There may occasionally be multiple periods in the content, as short placeholder periods are inserted when there is a loss of input signal for any reason while the media server remains online.

[DASH manifest link](https://akamai-axtest.akamaized.net/routes/lapd-v1-acceptance/www_c4/Manifest.mpd)

[HLS master playlist link](https://akamai-axtest.akamaized.net/routes/lapd-v1-acceptance/www_c4/Manifest.m3u8)

As HLS does not have good multiperiod feature support, the HLS master playlist is replaced in its entirety when a new period is started. Most players do not perform master playlist reloading, so beware.

The stream signals availability start time at the Unix epoch in 1970. The stream correctly follows the UTC timeline, including leap seconds. Many players are known to have problems with leap seconds because Unix timestamps do not include them. Such player defects may be easily demonstrated by this test vector - the player will play content that is 27 seconds older than expected.

There is at least one video track using H.264 High profile and exactly one audio track using AAC-LC. Detailed content parameters and available quality levels may change at any time given the dynamic nature of this stream - look in the manifest files to find out the latest details with accuracy.

There is a text track with different debugging timestamps visible:

* The authoring timestamp is when the sample in question was authored. Filenames and paths reference authoring time.
* The availability timestamp is when the sample in question should become available to players.
* The segment timestamp is the availability timestamp of the start of the current segment.

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

# Credits

Original content:

* "Tears of Steel" by [Blender Foundation](https://mango.blender.org).
* Various clips from the [SVT HD multiformat test set](https://media.xiph.org/video/derf/vqeg.its.bldrdoc.gov/HDTV/SVT_MultiFormat/SVT_MultiFormat_v10.pdf) and other [SVT test sets](https://media.xiph.org/video/derf/ftp.ldv.e-technik.tu-muenchen.de/pub/test_sequences/720p/ReadMe_720p.txt)
* [Caminandes 3: Llamigos](http://www.caminandes.com/)
* [Fires beneath water](https://archive.org/details/Fires_beneath_water)
* "life" by [HDgreetings](https://media.xiph.org/video/derf/www.hdgreetings.com/copyright.txt)
* "WestWindEasy" by [NTIA/ITS](https://media.xiph.org/video/derf/vqeg.its.bldrdoc.gov/HDTV/NTIA_source/HDTV_Readme.txt)
* [Music by bensound.com](https://www.bensound.com)

# Disclaimer

Axinom does not guarantee the continued availability of the test vectors or the license server nor the accuracy of any descriptive metadata.
