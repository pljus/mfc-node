What's new?
==========
In v.3.0.3 version is added an auto-save URL's of HD models because I've noticed that sometimes it's possible to watch or record some HD models while in AWAY mode if we have a fresh URL meaning it's enough to briefly capture your favorite model while in PUBLIC because the URL which may occur on that occasion may later be of benefit. Also is added keyword search capability for 'hdv', 'sdv' and 'ldv' words which can be easier than sorting by quality.
In v.3.0.2 Basic and HD version merged into one. It should be noted that HD models can be recorded like other SD models now. HD and SD models now using unique `config.yml` and `index.html`.
Now it is possible by simply editing the `config.yml` and `index.html` file to select the program we want to use to record your favorite models show's on myfreecams.com.
There are six choices available. I would recommend using three methods that do not freeze MFC recorded videos:

1. rtmpdump
2. streamlink
3. livestreamer

The program ffmpeg still has a problem with freeze MFC videos:

4. ffmpeg - ts
5. ffmpeg - flv
6. hsldl

File mfcd.exe using rtmp for download but should not mention more than 8 models at the same time.

mfc-node
========
mfc-node lets you follow and record your favorite models' shows on myfreecams.com
This is an attempt to create a script similar to [capturbate-node] based on different pieces of code found on the Internet.

Credits:
* [capturbate-node](https://github.com/SN4T14/capturebate-node)
* [mfc-node](https://github.com/sstativa/mfc-node)
* [MFCAuto](https://github.com/ZombieAlex/MFCAuto)
* [MFCD.exe](https://github.com/ruzzy/)
* [rtmpdump.exe](https://github.com/K-S-V/Scripts/releases)

Requirements
============
1. [Node.js](https://nodejs.org/download/release/) used to run mfc-node, hence the name. (tested with node v11.9.0)
2. [Livestreamer](https://github.com/chrippa/livestreamer/releases) last version 1.12.2 It's best to be in C:/Livestreamer
3. [Streamlink](https://github.com/streamlink/streamlink) (tested with version 0.9.0) - better to install it independently (not in python)
4. [ffmpeg](https://ffmpeg.zeranoe.com/builds/) must be a last version somewere in the path.
5. [MFCD.exe](http://www.mediafire.com/file/aim84bicrsbbvci/MFCD.rar) MFC Dump by @RuzzyRullez (little modified)
6. [hlsdl.exe](https://github.com/samsamsam-iptvplayer/hlsdl) or (https://www.mediafire.com/file/d9obqdq71cqeehr/hlsdl.exe/file) for windows.
7. [rtmp.exe](http://www.mediafire.com/file/2rpqt3dl3ed8k9z/rtmpdump2.4patch.rar/file) I've tested a lot of version 2.4 and they are all good but file must be renamed to `rtmp.exe`

Setup
=====
1. Install [Node.js](https://nodejs.org/download/) (minimum node version requirement: v9.4).
2. Download and unpack the [code](https://codeload.github.com/horacio9a/mfc-node/zip/v2).
3. Open Terminal (macOS) or Command Prompt (Windows) and go into the directory where you unpacked the files.
4. Install requirements by running `npm install` in the same directory as `main.js` is (Windows users have to install [Git](https://git-scm.com/download/win)).
5. Edit `config.yml` file and set desirable values for `captureDirectory`, `completeDirectory`, `modelScanInterval`.
6. Put `ffmpeg.exe`, `MFCD.exe`, `rtmp.exe` and `hlsdl.exe` into same directory as `main.js` or somewhere in the windows path.

Running
=======
1. Open Terminal (macOS) or Command Prompt (Windows) and go into the directory where you unpacked the files.
2. Run `node main.js`.
3. Open [http://localhost:8888](http://localhost:8888) in you browser. The list of online models will be displayed with a set of allowed commands for each model:

- The online model list can be sorted by various criteria (default is 'state' because at the top are the models currently being recorded). Thumbnails of models ('menu' small preview) with camscore greater than 350 will be displayed immediately. After about 60 seconds, thumbnails of other models will be visible when the mouse cursor is hover and will be updated.
- If you want to look at some of the models, click on the model name and a 'spinner' will appear with the model image in resolution 400x300 with all available model data.
- If you want to start recording, you need to click the red button ('Japanese flag'). If you want to stop recording, you need to click the stop button (right of the red button).
- If some model does not want to recording constantly click red button right from 'Japanese flag' and after 24 hours that model will be expired (Mode in config.yml will become 0).
- All this can be done online and track what is happening on the console, and you can view recorded file immediately if you start some media player, for example VLC.
- When you click on a preview thumbnail the large image is obtained in the next tab of your browser.
- The MFC Recorder now can record the MFC streams with six different programs (rtmp, livestreamer, streamlink, hsldl and ffmpeg in ts or flv) depending on the data in config.yml ('rtmp', 'ls', 'sl', 'hsldl', 'ff-ts' or 'ff-flv'). Currently it is better to use 'livestreamer' or 'streamlink' because they do not have the so-called 'freeze' problem as it currently has 'ffmpeg' for some models.
- By pressing 'State/Online' you can enter in the model room with your browser.
- By pressing the model 'Mob./true' you get a video preview of the current model in separate window of your browser. For this feature in My recommendation is to use the Chrome browser with the installed add-on [Play HLS M3u8](https://chrome.google.com/webstore/detail/play-hls-m3u8/ckblfoghkjhaclegefojbgllenffajdc/related) but if you want firefox then need to install [Native HLS Playback](https://addons.mozilla.org/en-US/firefox/addon/native_hls_playback/)
- If we already have to look at the lines of livestreamer and streamlink I made it to look better and to be useful because we will now know how is big files we are currently recording. This can be of help with other downloadings that we do with livestreamer and streamlink. In your instalation you must found:
- A new 'quality' column has been added so it is easy to find HD models. It is also possible to sort by the quality criteria that can further facilitate finding the HD models.

   ... /livestreamer_cli/utils/progress.pyc
   or
   ... /streamlink_cli/utils/progress.py

   ... and owerwrite existing files with 'progress.py' on this page.

The list of online models will be displayed with a set of allowed commands for each model:
	Include - if you want to record the model
	Exclude - if you don't want to record the model anymore
	Delete - if you are not interested in the model and wanna hide her permanently

This is not a real-time application. Whenever your 'include', 'exclude' or 'delete' the model your changes will be applied only with the next iteration of 'mainLoop' function of the script. 'mainLoop' runs every 30 seconds (default value for 'modelScanInterval').
There is no 'auto reload' feature, you have to reload the list manually with 'big red button', however, keep in mind the script updates the list internally every 30 seconds ('modelScanInterval'), therefore sometimes you'll have to wait 30 seconds to see any updates.
Be mindful when capturing many streams at once to have plenty of space on disk and the bandwidth available or you’ll end up dropping a lot of frames and the files will be useless.

Converting
===========
I've made a unique script to convert all three formats (ts, flv and mp4) to the final `.flv` format, which can be easily watch or edit after. I added the configuration option for last version or v.2.8.4 of ffmpeg. Mostly, the script processes all files regardless of whether they have audio or not.Newer versions of ffmpeg have problems with some codec's like speex audio and I recommend using ffmpeg v.2.8.4. The renamed files of ffmpeg v.2.8.4 is here: [ffmpeg284] (https://www.mediafire.com/file/o9wifql28cx2qqh/ffmpeg-2.8.4-win32.rar/file). Just put `ffmpeg284.exe` in the same directory where `ffmpeg.exe` is located, and enter `ffmpeg284` in config.yml. Don't think it is stupid `.flv` convert to `.flv` because the script fixed and after that is no problem for viewing or editing. Just edit `convert.yml` with appropriate values for `srcDirectory`, `dstDirectory` and choose ffmpeg version.

For advanced users
==================
There are several special URLs that allow implementing some operations with a model even if she is offline.

__Include__

```
http://localhost:8888/models/include?nm=modelname
http://localhost:8888/models/include?uid=12345678
```

__Exclude__

```
http://localhost:8888/models/exclude?nm=modelname
http://localhost:8888/models/exclude?uid=12345678
```

__Delete__

```
http://localhost:8888/models/delete?nm=modelname
http://localhost:8888/models/delete?uid=12345678
```

Proxy
=====
This is just a Proof of Concept to avoid region block.
To use it you have to start `proxy.js` on some remote server located in a different region then add a parameter `proxyServer` to your local `config.yml`, for example, `proxyServer: '54.206.109.161:9090'`.
The `main.js` script will try to get models from the remote region then merge them with the list of models available in your region.

Places that can be clicked

![alt screenshot](./screenshot.jpg)

New look of 'spinner'

![alt screenshot](./screenshot1.jpg)

Look after replacement of 'progress.py'

![alt screenshot](./screenshot2.jpg)
