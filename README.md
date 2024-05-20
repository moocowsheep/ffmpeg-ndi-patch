# FFmpeg NDI patch

Just a patch that add NDI from Newtek back in [FFmpeg](http://ffmpeg.org/). Newtek distributed FFmpeg compiled with non-free component infringing FFmpeg's license, then FFmpeg team decide to remove NDI protocol from it. ([source](https://trac.ffmpeg.org/ticket/7589))
Then I create this patch. Remember don't distribute a FFmpeg package with non-free enabled.

The patch file has for purpose to modify FFmpeg code, and other files to be added to it.
Then the licensing of those files will be and should be the same as [FFmpeg](https://git.ffmpeg.org/gitweb/ffmpeg.git/blob/HEAD:/LICENSE.md).

Reminder, the called headers files from NDI SDK are under MIT license.

## Usage :

``` bash
git clone https://framagit.org/tytan652/ffmpeg-ndi-patch.git
git clone https://git.ffmpeg.org/ffmpeg.git
cd ffmpeg

# Checkout to 4.2 version or later
git checkout n4.4

# Apply the patch

#For 4.2.x or 4.3.x versions
git am ../ffmpeg-ndi-patch/4.2-4.3_Revert-lavd-Remove-libndi_newtek.patch

#For 4.4.x versions
git am ../ffmpeg-ndi-patch/4.4_Revert-lavd-Remove-libndi_newtek.patch

#For 5.x and later versions
git am ../ffmpeg-ndi-patch/master_Revert-lavd-Remove-libndi_newtek.patch

# Add needed files
cp ../ffmpeg-ndi-patch/libavdevice/libndi_newtek_* libavdevice/

# Build FFmpeg with NDI
./configure --enable-nonfree --enable-libndi_newtek

make -j $(nproc)
```
