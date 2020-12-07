# FFMPEG

- ffmpeg -i input.mp4 -vcodec libx265 -crf 28 output_compressed.mp4 
- ffmpeg -i GOPR0327.MP4 -y -f mp4 -b:a 192k -c:v libx265 -crf 23 -preset slow GOPR0327_comp2.avi (GOPRO)
- ffmpeg -i GOPR0327_comp2.avi -strict -2 GOPR0327_comp2.mp4 (GOPRO)
- ffmpeg -i GOPR0327.MP4 -strict -2 GOPR0327_comp.mp4 (GOPRO)
- ffmpeg -i GOPR0327.MP4 -strict -2 -vcodec libx265 -crf 28  GOPR0327_comp.mp4 (avec comp)
- ffmpeg -i GOPR0327.MP4 -strict -2 -vcodec libx265 -crf 28 -preset [fast/slow] GOPR0327_comp.mp4 (avec comp)

mkdir comp
for f in *.mp4; do ffmpeg -i "$f" -strict -2 -vcodec libx265 -crf 28 -preset fast "comp/$f"; done
for f in *.MP4; do ffmpeg -i "$f" -strict -2 -vcodec libx265 -crf 28 -preset fast "comp/$f"; done

