# hugo-isaac
This is the repo for hugo-isaac website I worked on in Barcelona. For the live website I am creating. 

this is the link to the live page hugo-isaac:
https://isaacpierreracine.github.io/hugo-isaac/

Run site locally: hugo serve 
or 
make dev

insert local address in browser: http://localhost:1313/

Reminder session with Lairs 18 mars 2025:
when making changes always:
git status
git add name of file with changes to commit
or
git add . (adds all files with changes)

git commit -m 'commit message'
git push

remove a file: rm -r (name of the file)

to get into the zen mode: command k and z

to create a new post:hugo new content/content/post/nameofpost.md

Simple workflow:

Work on your site locally, running: 
hugo server --baseURL "http://localhost:1313/"
When you're ready to deploy, commit your changes and push to GitHub
GitHub Pages will use the production baseURL setting in your config file to serve your site
This approach keeps your workflow simple and avoids the need for separate config files or environment variables. Just remember to use the --baseURL flag when running hugo server locally.

this is my yaml file as per april 6 2025:
# todo: try dropping the /hugo-isaac/ from the base url + in images synthax
baseURL: "https://isaacpierreracine.github.io/hugo-isaac/" 
languageCode: en-us
title: isaac pierre racine
theme: PaperMod
publishDir: public

params:
  homeInfoParams:
    title: "Archive et portfolio de mon travail"
    content: Utiliser l'onglet 'Categories' pour choisir une discipline. 
  showbreadcrumbs: true
  cover:
    linkfullimages: true
  
menu:
  main:
    - name: About
      url: /about/
      weight: 10
    - name: Contact
      url: /contact/
      weight: 50
    - identifier: categories
      name: Categories
      url: /categories/
      weight: 20
    - identifier: tags
      name: Tags
      url: /tags/
      weight: 30
    - identifier: Archives
      name: Archives
      url: /Archives/
      weight: 40

      Notes on coding with ffmpeg to reduce video size, add titles with shadow block and with fade in at beginning and fade out at the end of video: (provided by Claude AI)
      ffmpeg -i MVI_3972.MOV -vf "scale=1920x1080,fade=in:d=3,fade=out:st=47.43:d=1,drawtext=text='Le vent souffle toujours, 2025':fontcolor=white:fontsize=48:x=(w-text_w)/2:y=h-125-text_h:enable='between(t,2,5)':alpha='if(between(t,2,3),t-2,if(between(t,4,5),5-t,1))':box=1:boxcolor=black@0.7:boxborderw=10" -c:v libx264 -crf 28 -preset medium -c:a aac -b:a 128k -movflags +faststart MVI_3972withtitlefadein.MOV  


On Mac with US keyboard layout, here are the terminal cursor shortcuts:
Move to beginning/end of line:

Ctrl + A - Move cursor to beginning of line
Ctrl + E - Move cursor to end of line

Word movement:

Option + Left Arrow - Move backward one word
Option + Right Arrow - Move forward one word

Other useful shortcuts:

Ctrl + F - Move forward one character
Ctrl + B - Move backward one character
Ctrl + U - Delete from cursor to beginning of line
Ctrl + K - Delete from cursor to end of line
Ctrl + W - Delete the word before cursor

Note: On Mac, use Ctrl (not Cmd) for these terminal shortcuts. The Option key is used instead of Alt for word movement.
So Ctrl + A will instantly move your cursor to the beginning of the line without having to delete each character!

# ffmpeg convert hi-res video to web format 
Here's the ffmpeg command to convert your h264 MOV file for optimal Vimeo hosting and web playback:
bashffmpeg -i MVI_4105.MOV -c:v libx264 -preset slow -crf 18 -c:a aac -b:a 192k -movflags +faststart -pix_fmt yuv420p MVI_4105_web.mp4
Command breakdown:

-c:v libx264 - Uses H.264 video codec (Vimeo's preferred format)
-preset slow - Higher quality encoding (takes longer but better compression)
-crf 18 - Constant Rate Factor for high quality (lower = higher quality, 18-23 is good range)
-c:a aac -b:a 192k - AAC audio at 192kbps bitrate
-movflags +faststart - Critical for web - moves metadata to beginning so video starts playing before fully downloaded
-pix_fmt yuv420p - Ensures compatibility across all browsers and devices

For even faster web loading, you might also want to create a lower quality version for initial preview:
bashffmpeg -i MVI_4105.MOV -c:v libx264 -preset fast -crf 23 -vf "scale=-2:720" -c:a aac -b:a 128k -movflags +faststart -pix_fmt yuv420p MVI_4105_720p.mp4
This second command scales to 720p height while maintaining aspect ratio, which loads much faster on web pages while still looking good.
The +faststart flag is particularly important for web hosting as it allows progressive download - users can start watching before the entire file downloads.

# Convert cr2 files to 200kb fiile in .jpg or .webp 
Yes, there are several command-line tools for Mac that can handle .cr2 (Canon RAW) files, similar to how ffmpeg works for videos. Here are your best options:
ImageMagick (Most Similar to ffmpeg)
ImageMagick is the closest equivalent to ffmpeg for images. Install it via Homebrew:
bashbrew install imagemagick
Convert and compress your .cr2 file:
bash# Convert to JPEG with quality setting (1-100, lower = smaller file)
magick input.cr2 -quality 75 output.jpg

# Resize and convert (useful for web)
magick input.cr2 -resize 1920x1080 -quality 80 output.jpg

# Convert to WebP for even better compression
magick input.cr2 -quality 75 output.webp
dcraw + ImageMagick (Better RAW Processing)
For higher quality RAW processing, combine dcraw with ImageMagick:
bashbrew install dcraw imagemagick

# Process RAW then compress
dcraw -c -w input.cr2 | magick - -quality 75 output.jpg
exiftool (Remove Metadata)
Reduce file size further by stripping metadata:
bashbrew install exiftool
exiftool -all= output.jpg
Complete Workflow Example
bash# Convert CR2 to web-optimized JPEG
magick input.cr2 -resize 1920x1080 -quality 75 -strip output.jpg

# Or for maximum compression with WebP
magick input.cr2 -resize 1920x1080 -quality 70 output.webp
For GitHub Pages, JPEG or WebP formats work best. Start with quality 75-80 and adjust based on your file size needs vs. image quality requirements.

# Best solution
all of these work but for best result is with 2 seperate pass. One with sips that is native mac and interprets well raw files to reduce size and convert to jpeg:
sips -s format jpeg -s formatOptions 90 Isaac_cirque_006_.cr2 --out Isaac_cirque_006_.jpg
and after to reduce size to 150k in webp format:
magick Isaac_cirque_006_.jpg -define webp:target-size=150KB Isaac_cirque_006_.webp
or:
sips -s format jpeg Isaac_cirque_006_.CR2 --out Isaac_cirque_006_.jpg
cwebp Isaac_cirque_006_.jpg -o Isaac_cirque_006_.webp -size 200000

# batch the whole folder in one pass

for file in *.CR2; do
    basename="${file%.CR2}"
    sips -s format jpeg "$file" --out "${basename}.jpg"
    cwebp "${basename}.jpg" -o "${basename}.webp" -size 200000
    rm "${basename}.jpg"  # Remove intermediate JPEG
done

# batch command each path seperately

for file in *.CR2; do
    basename="${file%.CR2}"
    sips -s format jpeg "$file" --out "${basename}.jpg"
done

for file in *.jpg; do
    basename="${file%.jpg}"
    cwebp "$file" -o "${basename}.webp" -size 200000
done

and to clean up the intermediate file (1st pass output)
rm *.jpg

# preserving orientation of webp file 

Actually, let me give you a better version that explicitly handles the orientation:

for file in *.CR2; do
    basename="${file%.CR2}"
    sips -s format jpeg "$file" --out "${basename}.jpg"
    sips --setProperty orientation 1 "${basename}.jpg"  # This applies any rotation and resets orientation flag
    cwebp "${basename}.jpg" -o "${basename}.webp" -size 200000
    rm "${basename}.jpg"
done

The key is the --setProperty orientation 1 command, which: Applies any rotation indicated by the EXIF orientation flag
Physically rotates the pixel data
Resets the orientation flag to 1 (normal)

This ensures that when cwebp processes the JPEG, the image data is already in the correct orientation and doesn't rely on EXIF data that WebP might ignore.

# Here are the separate batch commands:
Pass 1: Convert CR2 to JPEG
bash
for file in *.CR2; do
    basename="${file%.CR2}"
    sips -s format jpeg "$file" --out "${basename}.jpg"
done

Pass 2: Fix orientation on all JPEGs
bash
for file in *.jpg; do
    # Get the EXIF orientation value
    orientation=$(sips -g orientation "$file" 2>/dev/null | tail -1 | awk '{print $2}')

    case $orientation in
        3) sips -r 180 "$file" ;;
        6) sips -r 90 "$file" ;;
        8) sips -r 270 "$file" ;;
    esac
done

Pass 3: Convert JPEG to WebP
bash
for file in *.jpg; do
    basename="${file%.jpg}"
    cwebp "$file" -o "${basename}.webp" -size 200000
done

# the best is to do the following:
Pass 1: Convert CR2 to JPEG
bash
for file in *.CR2; do
    basename="${file%.CR2}"
    sips -s format jpeg "$file" --out "${basename}.jpg"
done

Pass 2: Fix orientation on all JPEGs
bashfor 
file in *.jpg; do
    # Get the EXIF orientation value
    orientation=$(sips -g orientation "$file" 2>/dev/null | tail -1 | awk '{print $2}')
    
    # Apply rotation based on orientation value
    case $orientation in
        3) sips -r 180 "$file" ;;
        6) sips -r 90 "$file" ;;
        8) sips -r 270 "$file" ;;
    esac
done

Pass 3: Convert JPEG to WebP
bash
for file in *.jpg; do
    basename="${file%.jpg}"
    cwebp "$file" -o "${basename}.webp" -size 150000
done

# To fix orientation for multiple JPEGs
for file in Isaac_cirque_{007..016}_.webp; do
    magick "$file" -rotate 90 "$file"
done

and for single file
Here's the command for lossless rotation of a single WebP file:

bash
magick Isaac_cirque_007_.webp -rotate 90 Isaac_cirque_007_.webp    # 90° clockwise
magick Isaac_cirque_007_.webp -rotate 270 Isaac_cirque_007_.webp   # 90° counter-clockwise
magick Isaac_cirque_007_.webp -rotate 180 Isaac_cirque_007_.webp   # 180°

Or if you want to save to a different filename:
bashmagick Isaac_cirque_007_.webp -rotate 90 Isaac_cirque_007_rotated.webp

Remember: Only 90°, 180°, and 270° rotations are truly lossless. Any other angle will cause quality loss due to pixel interpolation.