# portable music player avi video converter tool 2025 version

## What it does

Scripts to convert videos for avi format of portable music player through ffmpeg. It creates a file with the same name than source but ended in "-p".  
  
These scripts use a modified ffmpeg version with extra params for x264 codec. normal ffmpeg can't take those params.  
The ffmpeg was modified by the manufacturer of portable players, I'm not the manufacturer. I'm trying to discover those modifications to offer the ffmpeg mod source code and compiled versions for more platforms (linux, android, and so on).  
  
ffmpeg-mod was extracted from the official conversion tool SetupPxConverter(2.0.10).exe  

## Dependencies

ffmpeg-mod.exe  

these scripts are designed to run in Windows.  

## Players supported

AVI Format H264 modified video codec - Portable Music Player 2.0 inch 288x240 branded as Benjie D30 https://www.benjie-tx.com/mp3player/217.html  
AVI Format H264 modified video codec - Portable Music Player 2.4 inch 320x240  

## How to know the player format

Brandless portable players often don't specify clearly the video format that is supported, to know what type of format is there is available sample videos in the folder test_videos_to_know_format_supported.  

For another (older) portable players check out the related project https://github.com/fdd4s/portable_mp3_player_video_converter_tools
  
The sample is a fragment of 30 seconds of the Creative Commons video Big Buck Bunny https://en.wikipedia.org/wiki/Big_Buck_Bunny  

## Usage

    $ video2avi288.bat <video file>
    $ video2avi320.bat <video file>
    
## Example

    $ video2avi288.bat video.mp4

## Syntax to use

Use the next syntax of FFmpeg:  

Portable Music Player 288x240 AVI Format - Button 1.8 inch and Touch 2.0:  
ffmpeg-mod.exe -i source.mp4 -f avi -vcodec libx264 -vb 1500000 -r 14 -pix_fmt yuv420p -bufsize 25000k -maxrate 25000k -g 7 -refs 1 -qmin 18 -qmax 43 -profile:v baseline -x264-params imax=98304:pmax=65536:ipmax=163840 -vf "scale=-2:240, crop=288:240, transpose=2" -acodec pcm_s16le -ab 128k -ar 16000 -ac 1 dest.avi  
  
Portable Music Player 320x240 AVI Format - Touch 2.4 inch:  
ffmpeg-mod.exe -i source.mp4 -f avi -vcodec libx264 -vb 1500000 -r 14 -pix_fmt yuv420p -bufsize 25000k -maxrate 25000k -g 7 -refs 1 -qmin 18 -qmax 43 -profile:v baseline -x264-params imax=98304:pmax=65536:ipmax=163840 -vf "scale=-2:240, crop=320:240, transpose=2" -acodec pcm_s16le -ab 128k -ar 16000 -ac 1 dest.avi  
  
## How to add subtitles

Add ",subtitles=source.srt:force_style='Fontname=Arial,Fontsize=28,PrimaryColour=&H00FFFFFF,SecondaryColour=&H000000FF,BorderStyle=1,Shadow=2'" to "vf" argument if the subtitle filename is source.srt.  
  
e.g: ffmpeg-mod.exe -i source.mp4 -f avi -vcodec libx264 -vb 1500000 -r 14 -pix_fmt yuv420p -bufsize 25000k -maxrate 25000k -g 7 -refs 1 -qmin 18 -qmax 43 -profile:v baseline -x264-params imax=98304:pmax=65536:ipmax=163840 -vf "scale=-2:240, crop=288:240, subtitles=source.srt:force_style='Fontname=Arial,Fontsize=28,PrimaryColour=&H00FFFFFF,SecondaryColour=&H000000FF,BorderStyle=1,Shadow=2', transpose=2" -acodec pcm_s16le -ab 128k -ar 16000 -ac 1 dest.avi  

## How to cut video in fragments every 5 minutes

Add "-map 0 -segment_time 00:05:00 -f segment -reset_timestamps 1" before destination name, and "%02d" (fragment number) in the destination filename.  
  
e.g:  
ffmpeg-mod.exe -i source.mp4 -f avi -vcodec libx264 -vb 1500000 -r 14 -pix_fmt yuv420p -bufsize 25000k -maxrate 25000k -g 7 -refs 1 -qmin 18 -qmax 43 -profile:v baseline -x264-params imax=98304:pmax=65536:ipmax=163840 -vf "scale=-2:240, crop=288:240, transpose=2" -acodec pcm_s16le -ab 128k -ar 16000 -ac 1 -map 0 -segment_time 00:05:00 -f segment -reset_timestamps 1 dest%02d.avi

## Where to get those players?

All those players are/were available to buy in AliExpress and similar online shops (Shopee, eBay, and so on).  
  
1.8 inch Button Portable Music Player https://s.click.aliexpress.com/e/_oCC1BC9  
2.0 inch Touch Portable Music Player https://s.click.aliexpress.com/e/_oC3nAlL  
2.4 inch Touch Portable Music Player https://s.click.aliexpress.com/e/_oo806v7  
2.4 inch Touch Portable Music Player 2 https://s.click.aliexpress.com/e/_ooyuSkf  

## Related projects

https://github.com/tytydraco/ffmpeg-atj-patch  
https://github.com/fdd4s/portable_mp3_player_video_converter_tools  
https://github.com/fdd4s/shazam-autotag  

## Open Source implementation for all operating systems

https://github.com/tytydraco/ffmpeg-atj-patch  

## Credits

Created by fdd4s  
Send feedback and questions to fc1471789@gmail.com  
All script files are public domain https://unlicense.org/  
