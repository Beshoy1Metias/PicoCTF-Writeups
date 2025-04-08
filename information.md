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
✅ Output:

arduino
Copy
Edit
flag.png: PNG image data, 450 x 450, 8-bit/color RGB, non-interlaced
Looks like a regular image.

🧪 Step 2: Look for Metadata (EXIF)
Use exiftool to inspect metadata:

bash
Copy
Edit
exiftool flag.png
✅ Output:

css
Copy
Edit
Comment                        : picoCTF{h1dd3n_1n_pLa1n_s1ghT}
🎉 The flag is hidden inside the image’s metadata!

🧪 Step 3 (Optional): Use strings
If you don’t have exiftool, use:

bash
Copy
Edit
strings flag.png | findstr pico
✅ Output:

Copy
Edit
picoCTF{h1dd3n_1n_pLa1n_s1ghT}
🏁 Flag
Copy
Edit
picoCTF{h1dd3n_1n_pLa1n_s1ghT}
🧠 What We Learned
Images can hide flags inside metadata

exiftool is very useful for forensic tasks

strings can be a quick alternative to pull visible text

📚 Commands Recap
bash
Copy
Edit
file flag.png
exiftool flag.png
strings flag.png | findstr pico
yaml
Copy
Edit

---

### 🚀 Next Steps

1. Create the folder if needed:
```bash
mkdir -p 2021/General_Skills
