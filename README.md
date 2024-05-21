# FFmpeg NDI patch

Just a patch that add NDI from Newtek back in [FFmpeg](http://ffmpeg.org/). Newtek distributed FFmpeg compiled with non-free component infringing FFmpeg's license, then FFmpeg team decide to remove NDI protocol from it. ([source](https://trac.ffmpeg.org/ticket/7589))
This patch adds it back. Remember don't distribute a FFmpeg package with non-free enabled.

Forked from Tytan652.

The patch file modifies FFmpeg code, and other files are added to it.
Then the licensing of those files will be and should be the same as [FFmpeg](https://git.ffmpeg.org/gitweb/ffmpeg.git/blob/HEAD:/LICENSE.md).

Reminder, the header files from NDI SDK are under MIT license.

## Usage :

``` bash
git clone https://github.com/moocowsheep/ffmpeg-ndi-patch.git
git clone -b n7.0 https://git.ffmpeg.org/ffmpeg.git
cd ffmpeg

# Apply the patch

patch -Np1 -i ../ffmpeg-ndi-patch/7.0_add_ndi.patch

# Add needed files
cp ../ffmpeg-ndi-patch/libavdevice/libndi_newtek_* libavdevice/

# Build FFmpeg with NDI
./configure --enable-nonfree --enable-libndi_newtek

make -j $(nproc)
```
