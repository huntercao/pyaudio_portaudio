# _Precompiled & Extended_ | PyAudio with PortAudio for Windows | x86 DLL

#### Extensions:<br>&middot; Support of Windows sound loopback: Record the output of your soundcard

---
It is a fork of project:
- https://github.com/intxcc/pyaudio_portaudio

In our case, we have a Win32 Python application that need record audio stream from 
the loopback pin of default render device. Here we update the Intxcc's project.

For all the build steps and usages of the project for x64, please take reference to the original project.

# The build environment: 
1. Windows x64 PC, Visual Studio 2017.
2. Installed x64 version of Python: 
    C:\Python27\python.exe
3. Local independent-running Win32 version of Python. 
    .\WinPython-32bit-2.7.5.3\python-2.7.5\python.exe
# Build steps:
### 1. 
Specify the win32 python libraries path "[library_dirs]" in setup_x86.py. 
We have copied the win32 python libraries to "C:\Python27\libs_x86" and specify this path as "[library_dirs]". 
### 2.
Create 32bit portaudio library with VS2017 with the below solution file:
```bash
./pyaudio_portaudio/pyaudio/portaudio-v19/build/msvc/portaudio.sln
```
### 3.
Run setup_x86.py to create x86 version of pyaudio dll. 
```bash
$python.exe .\setup_x86.py build --static-link --plat-name=win32
```
The setup_x86.py is updated from original setup.py. 
The python.exe here is installed x64 version.
### 4.
Register the x86 extension dll with win32 python.
```bash
$.\WinPython-32bit-2.7.5.3\python-2.7.5\python.exe .\setup_x86.py install --static-link
```
The python.exe here is win32 version.

# Here are 2 new examples to use the loopback pin
```bash
./example/echo_default.py
./example/record_loopback.py
```
