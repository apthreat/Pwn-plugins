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

## 2. peda installation
