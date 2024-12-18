﻿# LSB-Steganography
This python program is based on the repository with the same name of [RobinDavid](https://github.com/RobinDavid/LSB-Steganography/blob/master/README.md#lsb-steganography).

# Table of Contents
- [Idea](#idea)
- [Installation - Quick-Setup](#installation---quick-setup)
- [Installation - Step-By-Step](#installation---step-by-step)
- [Examples](#examples)
- [Usage](#usage)
- [License](#license)

## Idea
Python program based on stegonographical methods to hide files in images using the Least Significant Bit technique.

I used the most basic method which is the least significant bit. A colour pixel is composed of red, green and blue, encoded on one byte. The idea is to store information in the first bit of every pixel's RGB component. In the worst case, the decimal value is different by one which is not visible to the human eye. In practice, if you don't have space to store all of your data in the first bit of every pixel you should start using the second bit, and so on. You have to keep in mind that the more your store data in an image, the more it can be detected.

This version tries to guess the correct filetype after decoding by reading the files binary signature and adds the correct extension to the file.

## Installation - Quick-Setup

Download steg.py and requirements.txt, then:  
`$ pip install -r requirements.txt`


## Installation - Step-By-Step
- [ ] **Install Python**  
Install the latest version of python from the [python homepage](https://www.python.org/downloads/).  
The latest version for Windows 64-bit can be found here: [Windows installer (64-bit)](https://www.python.org/ftp/python/3.13.0/python-3.13.0-amd64.exe)  
Be sure to check the box for "**Add python.exe to PATH**" in the installation wizard.
![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/AddToPath.PNG)  
<sup>Screenshot showing the relevant option in the installer</sup>  

- [ ] **Download files**  
Create a new folder/directory, e.g. on your desktop and download steg.py and _requirements.txt_

- [ ] **(Optional but recommended) Install a virtual environment**  
*Using a virtual environment (venv) let's you install all the needed packages in one place so you can just delete the folder afterwards and don't need to cleanup too much.*
	- Open a cli in the new folder/directory (just type `cmd` in the top part of the windows file explorer)   
![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/CmdAtTop.PNG)  
<sup>Where to write "cmd"</sup>  
	- Enter `python -m venv venv_steg` and wait  
	- Run `venv_steg\Scripts\activate` 
	to start the virtual environment, which will be recognizable by printing _(venv_steg)_ in the beginning of the command line.  
- [ ] **Install the required python packages**  
	-  Run `pip install -r requirements.txt` and wait for installation to finish

![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/Venv.PNG)  
<sup>CLI while installing venv and requirements</sup>  

## Examples

#### #decode
To retrieve the hidden file from new_cat.png (=input)  
and save it as _hidden_message_ (=output)  
put the image in the same directory/folder as _steg_._py_  
![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/directory_view.PNG)  

and run this
`python steg.py decode -i new_cat.png -o hidden_message`  
![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/example_decode.PNG)  

The extracted file will be saved in the same directory/folder as _hidden_message_.


#### #encode
To hide the text file _helloworld.txt_ (=file)  
in the image _cat.png_ (=input)  
and save the file as _new_cat.png_ (=output)  
place all the files in the same directory/folder as the _steg_._py_ script and use:  
`python steg.py encode -i cat.png -o new_cat.png -f helloworld.txt`  


## Usage

There are two main functions and a few options:  
| Name | Type | Description                    |
| ------------- | ------------- | ------------------------------ |
| `encode`      | function | Hide one file in another.       |
| `decode`   | function | Retrieve a hidden file.       |
| `-h, --help`   | option | Show this help.       |
| `--version`   | option | Show the version.       |
| `-i,--in=<input>`   | option | Input image (carrier).       |
| ` -o,--out=<output>`   | option | Output image (or extracted file).       |
| `-f,--file=<file> `   | option |  File to hide.       |


### #encode

To hide data inside of an image. What you need:  
- [ ] A carrier image `input`, in which the content will be hidden.  
      **.JPG** or **.JPEG** images can not be used, because of their lossy compressions.  
      An example image:  
![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/cat.png)  
<sup>cat.png</sup>  
- [ ] A file you want to hide `file`.  
      This can be any file (e.g. another image, a text file...), however the size is limited by the size of the carrier image.  
      As a rule of thumb: The larger the carrier image, the more data can be hidden inside.

- [ ] A name for the resulting image `output`.

To use the `encode` function, use the following console command (from within the virtual environment) and replace \<input\>, \<output\> and \<file\> with the aforementioned parts. 

`python steg.py encode -i <input> -o <output> -f <file>`
  

### #decode
To extract data from an image. What you need:  
- [ ] An image containing a hidden message/file `input`. Copy the image into the same folder/directory as the steg.py file.   
      For example this one:  
![](https://github.com/Yeltsa-Kcir/stegano_files/blob/main/md_images/new_cat.png)  
<sup>new_cat.png</sup>  


- [ ] A name for the hidden file once it's extracted `output`. 

To use the `decode` function, use the following console command (from within the virtual environment) and replace \<input\>, \<output\> and \<file\> with the aforementioned parts. 

`python steg.py decode -i <input> -o <output>`

You don't need to guess a filetype for the hidden message as the script will try to match it accordingly. 


## License

[](https://github.com/RobinDavid/LSB-Steganography/blob/master/README.md#license)

This software is MIT-Licensed.
