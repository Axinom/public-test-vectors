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

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsImtleXMiOlt7ImlkIjoiOWViNDA1MGQtZTQ0Yi00ODAyLTkzMmUtMjdkNzUwODNlMjY2IiwiZW5jcnlwdGVkX2tleSI6ImxLM09qSExZVzI0Y3Iya3RSNzRmbnc9PSJ9XX19.4lWwW46k-oWcah8oN18LPj5OLS5ZU-_AQv7fe0JhNjA`

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

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsImtleXMiOlt7ImlkIjoiODAzOTliZjUtOGEyMS00MDE0LTgwNTMtZTI3ZTc0OGU5OGMwIiwiZW5jcnlwdGVkX2tleSI6ImxpTkpxVmFZa05oK01LY3hKRms3SWc9PSJ9LHsiaWQiOiI5MDk1M2UwOS02Y2IyLTQ5YTMtYTI2MC03YTVmZWZlYWQ0OTkiLCJlbmNyeXB0ZWRfa2V5Ijoia1l0SEh2cnJmQ01lVmRKNkxrYmtuZz09In0seyJpZCI6IjBlNGRhOTJiLWQwZTgtNGE2Ni04YzNmLWMyNWE5N2ViNjUzMiIsImVuY3J5cHRlZF9rZXkiOiI3dzdOWkhITE1nSjRtUUtFSzVMVE1RPT0ifSx7ImlkIjoiNTg1ZjIzM2YtMzA3Mi00NmYxLTlmYTQtNmRjMjJjNjZhMDE0IiwiZW5jcnlwdGVkX2tleSI6IkFjNFVVbVl0Qko1blBROU4xNXJjM2c9PSJ9LHsiaWQiOiI0MjIyYmQ3OC1iYzQ1LTQxYmYtYjYzZS02ZjgxNGRjMzkxZGYiLCJlbmNyeXB0ZWRfa2V5IjoiTzZGTzBmcVNXb3BwN2JqYy9ENGxNQT09In1dfX0.uF6YlKAREOmbniAeYiH070HSJhV0YS7zSKjlCtiDR5Y`

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

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsImtleXMiOlt7ImlkIjoiMDg3Mjc4NmUtZjllNy00NjVmLWEzYTItNGU1YjBlZjhmYTQ1IiwiZW5jcnlwdGVkX2tleSI6IlB3NitlRVlOY3ZqWWJmc2gzWDNmbWc9PSJ9LHsiaWQiOiJjMTRmMDcwOS1mMmI5LTQ0MjctOTE2Yi02MWI1MjU4NjUwNmEiLCJlbmNyeXB0ZWRfa2V5IjoiLzErZk5paDM4bXFSdjR5Y1l6bnQvdz09In0seyJpZCI6IjhiMDI5ZTUxLWQ1NmEtNDRiZC05MTBmLWQ0YjVmZDkwZmJhMiIsImVuY3J5cHRlZF9rZXkiOiJrcTBKdVpFanBGTjhzYVRtdDU2ME9nPT0ifSx7ImlkIjoiMmQ2ZTkzODctNjBjYS00MTQ1LWFlYzItYzQwODM3YjRiMDI2IiwiZW5jcnlwdGVkX2tleSI6IlRjUlFlQld4RW9IT0tIcmFkNFNlVlE9PSJ9LHsiaWQiOiJkZTAyZjA3Zi1hMDk4LTRlZTAtYjU1Ni05MDdjMGQxN2ZiYmMiLCJlbmNyeXB0ZWRfa2V5IjoicG9lbmNTN0dnbWVHRmVvSjZQRUFUUT09In0seyJpZCI6IjkxNGU2OWY0LTBhYjMtNDUzNC05ZTlmLTk4NTM2MTVlMjZmNiIsImVuY3J5cHRlZF9rZXkiOiJlaUkvTXNsbHJRNHdDbFJUL0xObUNBPT0ifSx7ImlkIjoiZGE0NDQ1YzItZGI1ZS00OGVmLWIwOTYtM2VmMzQ3YjE2YzdmIiwiZW5jcnlwdGVkX2tleSI6IjJ3K3pkdnFycERWM3hSMGJKeTR1Z3c9PSJ9LHsiaWQiOiIyOWYwNWU4Zi1hMWFlLTQ2ZTQtODBlOS0yMmRjZDQ0Y2Q3YTEiLCJlbmNyeXB0ZWRfa2V5IjoiL3hsU0hweHdxdTNnby9nbHBtU2dhUT09In0seyJpZCI6IjY5ZmU3MDc3LWRhZGQtNGI1NS05NmNkLWMzZWRiMzk5MTg1MyIsImVuY3J5cHRlZF9rZXkiOiJ6dTZpdXpOMnBzaTBaU3hRaUFUa1JRPT0ifV19fQ.BXr93Et1krYMVs-CUnf7F3ywJWFRtxYdkR7Qn4w3-to`

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

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJtZXNzYWdlIjp7InBsYXlyZWFkeSI6eyJtaW5fYXBwX3NlY3VyaXR5X2xldmVsIjoxNTAsInBsYXlfZW5hYmxlcnMiOlsiNzg2NjI3RDgtQzJBNi00NEJFLThGODgtMDhBRTI1NUIwMUE3Il19LCJrZXlzIjpbeyJlbmNyeXB0ZWRfa2V5IjoiN1hIS21uL3NmdnVQTFd0UHRHVFpEUT09IiwiaWQiOiIxZWIzMzJiMi03NDM3LTQ5YWUtYmYzOS1lNzAwMTBjYjYyMGIifSx7ImVuY3J5cHRlZF9rZXkiOiJzUXRGWDh6Y2o5bEVyZ282RDdjNGh3PT0iLCJpZCI6IjlhYTYwZTNhLTljOTEtNDc0ZC04OTM3LTdkOGIzMjU5Y2NjZCJ9LHsiZW5jcnlwdGVkX2tleSI6Im8wUlY0a2tuVE1KTFFkeVh1a1VlT2c9PSIsImlkIjoiNTk0Nzk3YTctNmIwMC00NjczLWIyZTEtYWVmYzU1MmIxYmJjIn0seyJlbmNyeXB0ZWRfa2V5IjoiZVl1dlIvS1BhWCtXWG43Rkw5WkNxQT09IiwiaWQiOiJhYWUyNTc1OC1lNDgxLTQ4OTUtODEzMy1iODA5NDgzMzkzZDAifSx7ImVuY3J5cHRlZF9rZXkiOiIwQ1BUWVpMWmk1SmhZZ0NiZThKTnhRPT0iLCJpZCI6IjkzMTEzZDVlLTJlYzgtNDNjMS05MDgzLTEwZjNkZTIwM2EyOSJ9LHsiZW5jcnlwdGVkX2tleSI6IlFQUlBrQ09tenNORkl1cCszSFp3WWc9PSIsImlkIjoiZTQ4NzcwMzctNDM3Ni00ZWRkLTg1ODYtMTQ1MTk0MzU4ODAzIn0seyJlbmNyeXB0ZWRfa2V5IjoiVWtrWUZ0TXJGMnlET0hvYWxKRmZSZz09IiwiaWQiOiJlOGFkNTk3Mi04ODE5LTQzMjYtYWQ2YS1mOWExNTE2OGJjYTcifSx7ImVuY3J5cHRlZF9rZXkiOiJkdWhnRVJSRkRiZlFEcnlwUWRCUUVRPT0iLCJpZCI6IjI2YTA5MzlmLTNhMGMtNDI4OS1hZDZiLWJiNWNlYzE3ZmY0MCJ9LHsiZW5jcnlwdGVkX2tleSI6IjFOUHp1Q1JLM3p4bWpYK3FZZnU1bXc9PSIsImlkIjoiYTVlZDcxNzMtMzc4MS00Yzc0LTkwYWMtZjA4MzRlZjFhMWM4In0seyJlbmNyeXB0ZWRfa2V5IjoiYXVQTEJjd2NmTnFSRTV1WFdUZ1NLUT09IiwiaWQiOiIzMjlmNTMzZS1mYTc3LTQwNzAtYjY1Yi0zOTI5ODBiYWRhMGQifSx7ImVuY3J5cHRlZF9rZXkiOiI2NkE1MnFiZEcyQlg3SUhTaml6WUpRPT0iLCJpZCI6IjE5N2Y4Yjg0LTNiZjItNDg2MC1iMjNhLTVjNTQ2MjhhZDBiMSJ9LHsiZW5jcnlwdGVkX2tleSI6IlhIUUE3WWlEZGZwTE05QWxwcklDK2c9PSIsImlkIjoiNGVjZGQ0YzctNGQyOS00M2ZmLWJkYWYtMDJiNzY5MDBmMTIzIn0seyJlbmNyeXB0ZWRfa2V5IjoiblBqNWl3N1IvZDR0WmdKZktoRFhYZz09IiwiaWQiOiJlZTc0NmQxMi1hNDg4LTQ5NzctYjFjYS03N2ExMDFiYjQ4M2MifSx7ImVuY3J5cHRlZF9rZXkiOiJ5U1Vma0Q5ZEliK0ExNmoydHNzNDV3PT0iLCJpZCI6IjQ5NGY5NmUxLTM1MzUtNGE4NC05MWMxLWZhYTI4M2IwNmE1NCJ9LHsiZW5jcnlwdGVkX2tleSI6InJlUHVsaXg0eFZNZHlsUnVpcG5FK0E9PSIsImlkIjoiNWMwN2JmZjQtYzcwYi00ZDAyLWEzNzgtMzgzMjZmOTEwMDBjIn0seyJlbmNyeXB0ZWRfa2V5Ijoialc3Z2E0aytMcDdxWTd4Zmo5dHB5Zz09IiwiaWQiOiIzMjgzYzM1ZS1hZTJjLTRmOGMtOGE0OS00YTc1MGFlZGYxNDIifSx7ImVuY3J5cHRlZF9rZXkiOiJLdHNNYlZRM0JXL1dwQlIwSlQwa2R3PT0iLCJpZCI6IjhkNzdiOWM0LTdmNmQtNDdmOS04NTYyLWE1ZTVlNGMzNTFjZSJ9LHsiZW5jcnlwdGVkX2tleSI6IlhRTGZKQUpmSjFyelFMZGNFRWM5L2c9PSIsImlkIjoiODIzMTcxZDctZGZjMS00ZDBlLTgwM2YtNDBhMWY1ZTQzODY4In0seyJlbmNyeXB0ZWRfa2V5IjoiR0hQSVNYTXZKWEJ6WktGQm1ZMXFCZz09IiwiaWQiOiJjMTYyYWM3ZC00MGQ3LTQ2YzAtYjJjZC1lOTQyN2Q0MzljMzIifSx7ImVuY3J5cHRlZF9rZXkiOiJ2bzJhamlLaWV6Yk9xY2tyNTN0U3B3PT0iLCJpZCI6ImZhYTZkNmY1LTM1MDEtNDg1MS05MmViLWM3ZGE0NDRlY2FhYyJ9LHsiZW5jcnlwdGVkX2tleSI6Ijg2QkEwUHYwYXk4UmV5Wk4zeElYa2c9PSIsImlkIjoiZmM0OWI3MTEtMWNiNi00MGE3LTk4NDAtODNjNDFiNTViOTliIn0seyJlbmNyeXB0ZWRfa2V5IjoibUhBbERaa0NYQWpCR1pLR2h0Y3Zpdz09IiwiaWQiOiI0M2QwMjIwNC04NjA5LTRkNDYtOTlhYy00MjVhNWI0ODAwOTgifSx7ImVuY3J5cHRlZF9rZXkiOiJ3bWhjREdZcG84YlZBSit0OGF4SUZnPT0iLCJpZCI6IjRkNmU0OTZhLTFmOTgtNGVlOC04Zjg3LTRiMTAzYmQzOGQwZiJ9LHsiZW5jcnlwdGVkX2tleSI6Ik92cWF3Y0JVQVE3cHM2T0xhSnZPRmc9PSIsImlkIjoiYzRlMGQ5ZjctZDQ4Mi00MWMzLThjYmItOTdiMTEyZDcyZTY2In0seyJlbmNyeXB0ZWRfa2V5IjoiM3dTMkdpemxWcGtuNDlRRExxcFBhZz09IiwiaWQiOiIxYzJkZTFlNC1lZDMwLTQ0NTItYTExNS0wOTIzYjk0MGM0ZWQifSx7ImVuY3J5cHRlZF9rZXkiOiJTNWRGQ25yRUNjREswOEVreHllY3lRPT0iLCJpZCI6ImRjZjQzODVmLTM1MDUtNGZmNS1iMDU1LTQ2MWQ1YTA3ZjBmNSJ9LHsiZW5jcnlwdGVkX2tleSI6IlBnRUhyK0Nrd3JYTStlSWFnUnl4b3c9PSIsImlkIjoiZjMyNGYwNGUtN2M3My00ZjM3LTgxMzUtYzg5ZjhjNGU2Y2Y0In0seyJlbmNyeXB0ZWRfa2V5IjoiSkx6UUZGMXp4MFpZMzZYSTdaR0VaUT09IiwiaWQiOiI1Y2I1M2RkOC0xMjk0LTRjOGUtOTY0ZS0yNTg2OWQ1M2EyNGEifSx7ImVuY3J5cHRlZF9rZXkiOiJVOHBRdW1HUmtrTGppSEg1cjlqWGhnPT0iLCJpZCI6IjA1NjgyYTI2LTg4NzctNDZkMy05NDY1LTEwNGEzYTQwMDEwYSJ9LHsiZW5jcnlwdGVkX2tleSI6IlVJTDZKNGRzZEpGNi9tQTM1dHIvVFE9PSIsImlkIjoiYmNlNTM0MTAtM2IwYy00OTE0LTg3YTMtNzIzNjNjYTE3NTMxIn0seyJlbmNyeXB0ZWRfa2V5IjoiM3pCaW1Dc2NlMTV2YkV0Mm8zNEhhUT09IiwiaWQiOiI0ZjRmOGExYy0zMjAyLTQ2YWUtODA5ZS00ZmNmOTMzZWU2NTQifSx7ImVuY3J5cHRlZF9rZXkiOiJDVHdTU3RQMnV1QjVZdStNUGpZY29RPT0iLCJpZCI6Ijg1MmNkN2Y3LTQwZTktNDgyZC04MjI1LWRjYmM4ZTA4ZGI4YiJ9LHsiZW5jcnlwdGVkX2tleSI6Im1ubXRuUWVHYm0rZUEzN2t6dFovRVE9PSIsImlkIjoiZWZkZGI4ZWUtODI3OC00NDM2LWE2OTgtNzJiODAzZDA1MGRiIn0seyJlbmNyeXB0ZWRfa2V5Ijoib3BicXltZVRiT3VWalJnYjJHMHpVdz09IiwiaWQiOiJkNWJkYmE1My02MDZmLTRkNDYtODg4ZC1hMWViNDRjZDVmNDEifSx7ImVuY3J5cHRlZF9rZXkiOiJiSWRsOFhoVmdobmc4Tis4cUZVbFRnPT0iLCJpZCI6ImFlZDQ5NjA5LTUwOTktNDExOC05YjA4LWI5NTM4ZGIwMGMwYyJ9LHsiZW5jcnlwdGVkX2tleSI6Ikp1SS9UMSt5cUtzUU95MjZEbzRuZmc9PSIsImlkIjoiN2I1YzFlOWYtZjhiOC00OTkyLWFhM2UtYTA4NWZjMzY3MzExIn0seyJlbmNyeXB0ZWRfa2V5IjoiM2ladUZxalh3bzhiN1lkamxKZUVPUT09IiwiaWQiOiI1YmU0MGViZi0yZWE0LTQ5ZmItYjZlYy1iMDlkZTVhYjYxN2YifSx7ImVuY3J5cHRlZF9rZXkiOiJoQ3gybzJxQlJKL2hiZVNqKzY5dHF3PT0iLCJpZCI6ImU1MzBkZjFiLWZmN2UtNDJhNC1iNTNhLThkNmRlNjhmMDAxMCJ9LHsiZW5jcnlwdGVkX2tleSI6IjhveWlGM0pQTmdzd0tPajVrWjVIT0E9PSIsImlkIjoiYjk0OTg3NDUtODJlYS00ZmZhLWFiMmItZDczN2VmNTRmODYzIn0seyJlbmNyeXB0ZWRfa2V5IjoiTEs4TENTY28zQmZYZXhLMlh0WUZSQT09IiwiaWQiOiI0ZjUyOTc1Yi1lOWYzLTRmZDctYmI4OS00MDNiMjgwMGU4Y2YifV0sInR5cGUiOiJlbnRpdGxlbWVudF9tZXNzYWdlIn0sImNvbV9rZXlfaWQiOiJiMzM2NGViNS01MWY2LTRhZTMtOGM5OC0zM2NlZDVlMzFjNzgiLCJ2ZXJzaW9uIjoxfQ.kuZip7wOBZ6-FjAO_VcBq0r816426dFK4fTdfm99NqE`

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

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiNjllNTQwODgtZTllMC00NTMwLThjMWEtMWViNmRjZDBkMTRlIiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsImtleXMiOlt7ImlkIjoiZjhjODBjMjUtNjkwZi00NzM2LTgxMzItNDMwZTVjNjk5NGNlIiwiZW5jcnlwdGVkX2tleSI6ImlYcTQ5Wjg5czhkQ2owam0yQTdYelE9PSJ9XSwicGxheXJlYWR5Ijp7Im1pbl9hcHBfc2VjdXJpdHlfbGV2ZWwiOjE1MCwicGxheV9lbmFibGVycyI6WyI3ODY2MjdEOC1DMkE2LTQ0QkUtOEY4OC0wOEFFMjU1QjAxQTciXX19fQ.hRBkpC-9i6nXUmxTPLEfb16MAwh5LhxUZ2b8z1o1e5g`

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
