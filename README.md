# Pwn-plugins
Series of PWN tools and plugins

## First Step of your Configuration.
### 1. pwndbg installation
	Once you clone this repository into your directory, you'd better apply some changes into the file named **setup.sh** of *pwndbg/*  

	The following codes are the original.
```Bash
# Upgrade pip itself
${PYTHON} -m pip install ${INSTALLFLAGS} --upgrade pip

# Install Python dependencies
${PYTHON} -m pip install ${INSTALLFLAGS} -Ur requirements.txt

```
	The following codes are the modified.
```Bash
# Upgrade pip itself
${PYTHON} -m pip install ${INSTALLFLAGS} --upgrade pip -i https://pypi.tuna.tsinghua.edu.cn/simple/

# Install Python dependencies
${PYTHON} -m pip install ${INSTALLFLAGS} -Ur requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple/
```
	This can speed up your download of pip

	Then execute the file--setup.sh by run "./setup.sh"

### 2. peda installation
....
### 3. gef installation
....

## Combine pwndbg, gef and peda by a trick
The fils needed:
- /pwndbg/gdbinit.py
- /peda/peda.py
- /gef/gef.py
    Then you should touch a file in ~/ named .gdbinit and paste the following codes into this file
```Bash
define init-peda
source ~/.peda/peda.py
end
document init-peda
Initializes the PEDA (Python Exploit Development Assistant for GDB) framework
end

define init-pwndbg
source ~/.pwndbg/gdbinit.py
end

define init-gef
source ~/.gef/gef.py
end
document init-gef
Initializes GEF (GDB Enhanced Features)
end
```
## The last step is make three files as following
### /bin/gdb-pwndbg
```Bash
#!/bin/sh
exec gdb -q -ex init-pwndbg "$@"
```
### /bin/gdb-peda
```Bash
#!/bin/sh
exec gdb -q -ex init-peda "$@"
```
### /bin/geb-gef
```Bash
#!/bin/sh
exec gdb -q -ex init-gef "$@"
```
Then you should attribute "x" privilege to these files
```Bash
cd /bin
sudo chmod +x gbd-*
```
The following pictures are the real effects.

![Screenshot 2022-10-15 215358](https://user-images.githubusercontent.com/115911851/196018763-36f466e2-f52f-4819-8f9a-5cfb0d178720.png)

![Screenshot 2022-10-15 215307](https://user-images.githubusercontent.com/115911851/196018754-3aa7b0b6-0db4-41d7-be8c-81b169ff38f4.png)

![Screenshot 2022-10-15 215334](https://user-images.githubusercontent.com/115911851/196018755-8974a5c4-7ecc-4ce1-a50b-0d5e785b49ed.png)


