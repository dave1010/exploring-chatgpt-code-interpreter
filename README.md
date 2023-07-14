# Exploring ChatGPT Code Interpreter (CI)

*Exploring what's possible with the ChatGPT Code Interpreter and how to use it effectively.*

# General info environment and limitations

## Basics

* Runs Python in a [Jupyter notebook](https://en.wikipedia.org/wiki/Project_Jupyter) environment
* Upload files. At least 50MB
* Download files. CI will provide a link like `[Link text](sandbox:/mnt/data/filename)`
* Display images

## Environment

* Home `/home/sandbox`
* User `sandbox`

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

# What's available

* Barebones Ubuntu packages are installed. Use `dpkg -l` to list them
* Interesting packages:
  * System: `bash`, 
  * Text: `diffutils`, `graphviz`, `patch`, `poppler-utils`, `pstotext`, `vim`
  * Media:  `espeak`, `ffmpeg`, `lame`, `sox`, `tesseract-ocr`
  * Programming and building: `binutils`, `build-essential`, `cpp`, `g++`, `perl`, `python3.8`,
  * Python: `python3`, `python3.8`, `python3-requests`
  * Networking, servers, clients: `curl`, `libmysqlclient21`, `mysql-common`, `openssl`
* Commands:
  * `python3`

# Installing other software

(TODO)

# Interesting things it can do out the box

* Make PowerPoint files
* OCR

# Tips for working on code bases

(TODO)
