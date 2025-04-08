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
Comment                        : picoCTF{h1dd3n_1n_pLa1n_s1ghT}

🎉 The flag is hidden inside the image’s metadata!

🧠 What We Learned
Images can hide flags inside metadata

exiftool is very useful for forensic tasks


📚 Commands Recap
file flag.png
exiftool flag.png
