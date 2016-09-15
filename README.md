# Axinom DASH test vectors

This document lists the test vectors that Axinom offers for customers, partners and the general public.

These test vectors make use of modern DASH features and conform to the latest industry standards, among these the *DASH-IF Interoperability Points* and the upcoming *ISO/IEC CD 23000-19 "Common Media Application Format"* (or its latest draft).

As such, the scope of features utilized intentionally exceeds that seen with more traditional conservative test vectors - the below data is designed to push the boundaries of implementations and to encourage uptake of modern features. Please use the [conservative branch](https://github.com/Axinom/dash-test-vectors/tree/conservative) for a more widely-compatible (but less modern) version of the content.

# Quick playback in common players

Most modern players include a demo application that enables you to easily play these test vectors:

* [dash.js](https://github.com/Dash-Industry-Forum/dash.js/) includes these test vectors on the [demo page](http://mediapm.edgesuite.net/dash/public/nightly/samples/dash-if-reference-player/index.html).
* The [ExoPlayer](https://github.com/google/ExoPlayer) demo app can load the [Axinom playlist](https://raw.githubusercontent.com/Axinom/dash-test-vectors/master/axinom.exolist.json) (click this link on an Android device with ExoPlayer demo app installed; [more info](https://google.github.io/ExoPlayer/demo-application.html))

# Usage of Axinom DRM

All test vectors can be played back using both the PlayReady and Widevine DRM technologies for decryption.

PlayReady license server URL: http://drm-playready-licensing.axtest.net/AcquireLicense

Widevine license server URL: http://drm-widevine-licensing.axtest.net/AcquireLicense

The license server will provide nonpersistent licenses for the relevant keys upon each license request. To receive a license, you must add the HTTP header `X-AxDRM-Message` to the license request, with the value being a constant unique to each test vector. Example of license request:

    POST http://drm-widevine-licensing.axtest.net/AcquireLicense HTTP/1.1
    Host: drm-widevine-licensing.axtest.net
    X-AxDRM-Message: eyJ0eX...

# Customization of DRM behavior

To customize the DRM parameters (e.g. license persistence/expiration or HDCP configuration) you must create your own license tokens instead of using the pre-generated ones provided below. Please refer to the [Axinom DRM Quick Start](https://github.com/Axinom/drm-quick-start) repository for more information on how to achieve this.

# HTTPS compatibility notice

All URLs in this document are also accessible over HTTPS.

# Audio content description

The audio tracks contain the same content but at a different pitch.

* "en" language is the original audio.
* "en-AU" language is the same content at a higher pitch.
* "et-ET" language is the same content at a lower pitch.

# v7-MultiDRM-SingleKey

Single-period presentation using DASH live profile. All video and audio representations are encrypted using the same key. Text representations are not encrypted.

[4K variant](http://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest.mpd)

[1080p variant](http://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_1080p.mpd)

[Audio-only variant](http://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey/Manifest_AudioOnly.mpd)

[Download](http://media.axprod.net/TestVectors/v7-MultiDRM-SingleKey.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
               | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
               | 5x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. Manifest contains PlayReady and Widevine DRM system initialization data. Segments do not contain DRM system initialization data. Manifest does not contain any license server URLs.

Adaptation set | Key ID                               | Content key
:--------------|:-------------------------------------|:------------------------
Video (all)    | 9eb4050d-e44b-4802-932e-27d75083e266 | FmY0xnWCPCNaSpRG+tUuTQ==
Audio (all)    | 9eb4050d-e44b-4802-932e-27d75083e266 | FmY0xnWCPCNaSpRG+tUuTQ==
Text (all)     | -                                    | -

Value to use for X-AxDRM-Message header: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ2ZXJzaW9uIjoxLCJjb21fa2V5X2lkIjoiYjMzNjRlYjUtNTFmNi00YWUzLThjOTgtMzNjZWQ1ZTMxYzc4IiwibWVzc2FnZSI6eyJ0eXBlIjoiZW50aXRsZW1lbnRfbWVzc2FnZSIsImtleXMiOlt7ImlkIjoiOWViNDA1MGQtZTQ0Yi00ODAyLTkzMmUtMjdkNzUwODNlMjY2IiwiZW5jcnlwdGVkX2tleSI6ImxLM09qSExZVzI0Y3Iya3RSNzRmbnc9PSJ9XX19.4lWwW46k-oWcah8oN18LPj5OLS5ZU-_AQv7fe0JhNjA`

# v7-MultiDRM-MultiKey

Single-period presentation using DASH live profile. Video and audio representations are encrypted using multiple keys. Text representations are not encrypted.

[4K variant](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest.mpd)

[1080p variant](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_1080p.mpd)

[Audio-only variant](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey/Manifest_AudioOnly.mpd)

[Download](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
               | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
               | 5x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. Manifest contains PlayReady and Widevine DRM system initialization data. Segments do not contain DRM system initialization data. Manifest does not contain any license server URLs.

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

[4K variant](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest.mpd)

[1080p variant](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_1080p.mpd)

[Audio-only variant](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod/Manifest_AudioOnly.mpd)

[Download](http://media.axprod.net/TestVectors/v7-MultiDRM-MultiKey-MultiPeriod.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
               | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
               | 5x IMSC 1.0 Text Profile

Samples are encrypted using the `cenc` encryption scheme. Manifest contains PlayReady and Widevine DRM system initialization data. Segments do not contain DRM system initialization data. Manifest does not contain any license server URLs.

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

[Single-period 4K variant](http://media.axprod.net/TestVectors/v7-Clear/Manifest.mpd)

[Single-period 1080p variant](http://media.axprod.net/TestVectors/v7-Clear/Manifest_1080p.mpd)

[Single-period audio-only variant](http://media.axprod.net/TestVectors/v7-Clear/Manifest_AudioOnly.mpd)

[Multi-period 4K variant](http://media.axprod.net/TestVectors/v7-Clear/Manifest_MultiPeriod.mpd)

[Multi-period 1080p variant](http://media.axprod.net/TestVectors/v7-Clear/Manifest_MultiPeriod_1080p.mpd)

[Multi-period audio-only variant](http://media.axprod.net/TestVectors/v7-Clear/Manifest_MultiPeriod_AudioOnly.mpd)

[Download](http://media.axprod.net/TestVectors/v7-Clear.7z)

Track          | Parameters
:--------------|:----------
Video          | 7x H.264 High Profile, 288p...2160p @ max 6 Mbps
               | 7x H.265 Main 10 Profile, 288p...2160p @ max 4.5 Mbps
Audio          | 3x HE-AACv2 at 64 kbps, stereo
Text           | 5x WebVTT
               | 5x IMSC 1.0 Text Profile

# Credits

Original content "Tears of Steel" by [Blender Foundation](http://mango.blender.org).

# Disclaimer

Axinom does not guarantee the continued availability of the test vectors or the license server nor the accuracy of any descriptive metadata.
