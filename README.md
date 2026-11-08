# cinemaplayer-ffmpeg

The FFmpeg libraries that [CinemaPlayer](https://github.com/mahdiibakhshii) ships, built from the
unmodified upstream FFmpeg release source with a minimal configuration and no external libraries.

Each release has one asset, a zip holding one folder:

- `bin/` - the five FFmpeg DLLs (`avcodec`, `avformat`, `avfilter`, `avutil`, `swresample`),
  unmodified and with their standard names; any interface-compatible FFmpeg 8.1 shared build may
  replace them;
- `lib/`, `include/` - import libraries and headers to link against them;
- `CONFIGURE.txt` - the exact configure line; `BUILDINFO.txt` - source, toolchain and hashes;
- `LICENSES/` - the GNU LGPL 2.1, FFmpeg's licence summary, the per-file notices of the FFmpeg
  sources compiled in, and the mingw-w64 runtime notices;
- `source/` - the complete corresponding source: the upstream `ffmpeg-8.1.3.tar.xz` with its
  signature, and the scripts and component list used to configure, build and package it.

## Licence

FFmpeg, as built here, is licensed under the GNU Lesser General Public License version 2.1 or (at
your option) any later version. The builds use no `--enable-gpl`, `--enable-nonfree` or
`--enable-version3`. FFmpeg is a trademark of Fabrice Bellard; see https://ffmpeg.org.

## Rebuilding

`source/build_ffmpeg.md` describes the build. On macOS or Linux, with llvm-mingw
20261020 in `<toolcache>/llvm-mingw` (Linux downloads its own pinned copy):

    TOOLCACHE=<toolcache> bash source/build_ffmpeg.sh
