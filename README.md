# FFMPEG

- ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output_compressed.mp4 
- ffmpeg -i GOPR0327.MP4 -y -f mp4 -b:a 192k -c:v libx265 -crf 23 -preset slow GOPR0327_comp2.avi (GOPRO)
- ffmpeg -i GOPR0327_comp2.avi -strict -2 GOPR0327_comp2.mp4 (GOPRO)
- ffmpeg -i GOPR0327.MP4 -strict -2 GOPR0327_comp.mp4 (GOPRO)
- ffmpeg -i GOPR0327.MP4 -strict -2 -vcodec libx265 -crf 28  GOPR0327_comp.mp4 (avec comp)
- ffmpeg -i GOPR0327.MP4 -strict -2 -vcodec libx265 -crf 28 -preset [fast/slow] GOPR0327_comp.mp4 (avec comp)

bash convFile.bat :

````
@echo ON
rd /s /q "comp"
mkdir comp
for f in *.mp4; do ffmpeg -i "$f" -y -f mp4 -b:a 192k -c:v libx264 -crf 23 -preset fast "comp/$f.mp4";
done
for f in comp/*.mp4.mp4; do mv "$f" "${f%.mp4.mp4}.mp4";
done
for f in *.MP4; do ffmpeg -i "$f" -y -f mp4 -b:a 192k -c:v libx264 -crf 23 -preset fast "comp/$f.mp4";
done 
for f in comp/*.MP4.mp4; do mv "$f" "${f%.MP4.mp4}.mp4";
done
````

```
@echo ON
rd /s /q "comp"
mkdir comp
for f in *.mp4; do ffmpeg -i "$f" -y -f mp4 -b:a 192k -c:v libx265 -crf 23 -preset fast "comp/$f.avi";
done
for f in comp/*.mp4.avi; do mv "$f" "${f%.mp4.avi}.avi";
done
for f in *.MP4; do ffmpeg -i "$f" -y -f mp4 -b:a 192k -c:v libx265 -crf 23 -preset fast "comp/$f.avi";
done 
for f in comp/*.MP4.avi; do mv "$f" "${f%.MP4.avi}.avi";
done
```

```
@ECHO ON
if not exist "comp" mkdir comp
for /f "tokens=1 delims=." %a in ('dir /B *.mp4') do ffmpeg -i "%a.mp4" "%a_comp.mp4"
```


```
@echo ON
rd /s /q "comp"
mkdir comp
for f in *.mp4; do ffmpeg -i "$f" -preset fast "comp/$f.mp4";
done
for f in comp/*.mp4.mp4; do mv "$f" "${f%.mp4.mp4}.mp4";
done
for f in *.MP4; do ffmpeg -i "$f" -preset fast "comp/$f.mp4";
done
for f in comp/*.MP4.mp4; do mv "$f" "${f%.MP4.mp4}.mp4";
done
```

bash rotate90.bat :

```
@echo ON
ffmpeg -hide_banner -noautorotate -i "input.mp4" -vf "transpose=cclock" -metadata:s:v:0 rotate=0 -c:v libx264 -preset veryfast -crf 22 -c:a copy "input90.mp4";

```

bash convWAWtoMP3.bat :
```
@echo ON
rd /s /q "compMP3"
mkdir compMP3
for f in *.wav; do ffmpeg -i "$f" -ab 320k -f mp3 "compMP3/$f.mp3";
done
for f in compMP3/*.wav.mp3; do mv "$f" "${f%.wav.mp3}.mp3";
done
```
