# Apple iPhone Photos

- Download 1000 photos at a time using icloud.com with original unmodified enabled
- LIVE photos will get converted to still image + .mov
- location data is attached to photo

DO NOT EXPORT WITH MODIFICATIONS in APPLE PHOTOS APPLICATION. Use 'export originals'

# Sort Photos

https://github.com/andrewning/sortphotos/issues/133

Verified with Python3.6.5, 
- pip install tqdm

## Windows

HEIC Codec: 
    Open in browser: ms-windows-store://pdp/?ProductId=9n4wgh0z6vhq

## Linux

```bash
$ cd /Volumes/Pathak_Fam/Media/_scripts/src

# Unzip files first
$ find . -iname '*.zip' -exec sh -c 'unzip -o -d "${0%.*}" "$0"' '{}' ';'
### Check with test flag first

$ python3 sortphotos.py -r -t -s /Volumes/Pathak_Fam/Media/Staging\ area\ for\ unsorted/Niral\ iPhone\ Photos\ v2 /Volumes/Pathak_Fam/Media/Media_sorted --ignore-tags IPTC:TimeCreated IPTC:DigitalCreationTime MakerNotes:Time ZIP:ZipModifyDate


```

### Flags

Always use:
`--ignore-tags IPTC:TimeCreated IPTC:DigitalCreationTime MakerNotes:Time ZIP:ZipModifyDate`

Also useful:
`--use-only-tags EXIF:CreateDate EXIF:DateTimeOriginal`

Bad metadata can cause bad sort:
```python
[{
  "SourceFile": "/Volumes/Pathak_Fam/Media/Media_sorted/0007/05-May/IMG_6304.JPG",
  "File:FileModifyDate": "2022:08:21 23:45:42-07:00",
  "File:FileAccessDate": "2022:08:26 21:35:02-07:00",
  "File:FileInodeChangeDate": "2022:08:21 23:45:42-07:00",
  "EXIF:ModifyDate": "2019:11:22 07:05:29",
  "EXIF:DateTimeOriginal": "2019:11:22 07:05:29",
  "EXIF:CreateDate": "2019:11:22 07:05:29",
  "EXIF:SubSecTimeOriginal": "000",
  "EXIF:SubSecTimeDigitized": "000",
  "IPTC:DigitalCreationTime": "07:05:29",
  "IPTC:DigitalCreationDate": "2019:11:22",
  "IPTC:DateCreated": "2019:11:22",
  "IPTC:TimeCreated": "07:05:29",
  "Composite:DateTimeCreated": "2019:11:22 07:05:29",
  "Composite:DigitalCreationDateTime": "2019:11:22 07:05:29",
  "Composite:SubSecCreateDate": "2019:11:22 07:05:29.000",
  "Composite:SubSecDateTimeOriginal": "2019:11:22 07:05:29.000"
}]
```

# Misc

Lists types of extensions in directory, recursively:

find . -type f | sed -n 's/..*\.//p' | sort | uniq -c


sudo rsync -vaE --progress source/ destination/
    use rsync for moving large # of files


find . -mindepth 2 -type f -print -exec mv {} . \;
    Above moves all files in subdirs to current dir

# Print empty directories
find . -type d -empty -print
# Delete empty directories
find . -type d -empty -delete