# Information - [General Skills] - [100 Points]

**Description:**
> Files can always be changed in a secret way. Can you find the flag?  
> [Download the file here](https://artifacts.picoctf.net/c/91/flag.png)

---

## 🔍 Step-by-Step Solution

We are given a file called `flag.png`. The challenge hints that the image may have **hidden data**.

### 🔧 Tools Used:
- `file`
- `exiftool`
- `strings`

---

### 🧪 Step 1: Inspect the File Type

Check what kind of file it is:

```bash
file flag.png
```
✅ Output:
flag.png: PNG image data, 450 x 450, 8-bit/color RGB, non-interlaced
Looks like a regular image.

🧪 Step 2: Look for Metadata (EXIF)
Use exiftool to inspect metadata:
```
exiftool flag.png
```
✅ Output:
```
ExifTool Version Number         : 12.76
File Name                       : cat.jpg
Directory                       : .
File Size                       : 878 kB
File Modification Date/Time     : 2021:03:15 18:24:46+00:00
File Access Date/Time           : 2025:04:08 02:23:25+00:00
File Inode Change Date/Time     : 2025:04:08 02:23:25+00:00
File Permissions                : -rw-rw-r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.02
Resolution Unit                 : None
X Resolution                    : 1
Y Resolution                    : 1
Current IPTC Digest             : 7a78f3d9cfb1ce42ab5a3aa30573d617
Copyright Notice                : PicoCTF
Application Record Version      : 4
XMP Toolkit                     : Image::ExifTool 10.80
License                         : cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9
Rights                          : PicoCTF
Image Width                     : 2560
Image Height                    : 1598
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 2560x1598
Megapixels                      : 4.1
```
so I thought the license looked a bit weird to be a normal so I tried decoding it from base64 using this command (you can also use cyberchef for this):
```
echo "cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9" | base64 --decode
```
which gave me this: picoCTF{the_m3tadata_1s_modified}

🎉 The flag is hidden inside the image’s metadata!
