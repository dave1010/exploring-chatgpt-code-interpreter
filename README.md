# Exploring ChatGPT Code Interpreter (CI)

*Exploring what's possible with the ChatGPT Code Interpreter and how to use it effectively.*

CI can do basically anything that's possible on a Linux box without root or internet access. With some creativity, almost any software can be ran.

If you want internet access or root permissions then check out [Pandora](https://github.com/dave1010/pandora), an open source ChatGPT plugin I made that is like an unrestricted CI.

# General info environment and limitations

## Basics

* Runs Python in a [Jupyter notebook](https://en.wikipedia.org/wiki/Project_Jupyter) environment
* Upload files. At least 50MB
* Download files. CI will provide a link like `[Link text](sandbox:/mnt/data/filename)`
* Display images

## Environment

* Home `/home/sandbox`
* User `sandbox`
* amd64

## Hard limitations

* No root access
* No internet access
* Commands timeout after 120 seconds
* Interactive session is reset after a few minutes of inactivity
* Stored files are lost after longer inactivity

## Soft limitations

CI thinks it's just for Python but you can get it to do much more...

* It wants to just let you download files in `/mnt/data` but it can link to any file on the system readable by the user.
  This isn't particularly beneficial, as you can just copy a file there anyway.
* Run sub processes. CI really thinks it's not able to do this.
* Run local servers, like web servers (opening a network socket, binding it to a local address and port, and accepting incoming connections.)
* Execute uploaded files

These are left as an exercise for the reader.

# What's available

* Barebones Ubuntu packages are installed. Use `dpkg -l` to list them
* Interesting packages:
  * System: `bash`, 
  * Text: `diffutils`, `graphviz`, `patch`, `poppler-utils`, `pstotext`, `vim`
  * Media:  `espeak`, `ffmpeg`, `lame`, `sox`, `tesseract-ocr`
  * Programming and building: `binutils`, `build-essential`, `cpp`, `g++`, `perl`,
  * Python: `python3`, `python3.8`, `python3-requests`
  * Networking, servers, clients: `curl`, `libmysqlclient21`, `mysql-common`, `openssl`
 
See [dpkg list](dpkg_output.txt) for more. 


* Commands available:
  * `python3`

# Installing other software

CI comes with lots of stuff out the box but not everything. You might need to install other software.

Here's a few handy things I've got working. Some of these are AppImage files

* [Deno](https://github.com/denoland/deno/releases) (JavaScript runtime, like Node))
* [ImageMagick](https://imagemagick.org/archive/binaries/) (magick)
* [PHP](https://github.com/scorninpc/php-gtk3/releases) (actually PHP-GTK3 but I haven't found another version that works yet)
* [Python 3.11](https://github.com/niess/python-appimage/releases) - CI comes with Python 3.8. Some packages only work with later verions like 3.11
* [pocketsphinx](https://pypi.org/project/pocketsphinx/#files) - speech recognition (requires [sounddevice](https://pypi.org/project/sounddevice/#files) )


# Interesting things it can do out the box

* Make PowerPoint files
* OCR

# Tips for working on code bases

* Upload a zip file
* You can get CI to give you chabged fikes or zip up the whole code base again
* git isnt available and i haven't got it working but dulwich is easy to get working for basic diffs and commits
* CI can also diff an original and modified code base and give you a patch file to download ana apply
