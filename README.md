# List Capture Devices for Python OpenCV on Windows
**OpenCV** does not have an API for listing capture devices. The sample shows how to create a Python extension to invoke DirectShow C++ APIs for enumerating capture devices.

## Environment
* [Microsoft Windows SDK][0]
* Python 3.x (tested on Python 3.7)
* OpenCV (tested on 4.2.0)

## How to Run 
1. Have VisualStudio 2019 installed.    

2. Add your Windows SDK lib path to **setup.py**:

    ```python
    from distutils.core import setup, Extension

    module_device = Extension('device',
                            sources = ['device.cpp'], 
                            library_dirs=['G:\Program Files\Microsoft SDKs\Windows\v6.1\Lib']
                        )

    setup (name = 'WindowsDevices',
            version = '1.0',
            description = 'Get device list with DirectShow',
            ext_modules = [module_device])
    ```

3. Build the Python extension
    Python 3

    ```
    python3 setup.py build 
    ```
	
	or
	
	```
	python3 setup.py build install
	```
	
	if you want it copied to your python installation directory
	

4. Run the app and select a capture device:

    Python 3
    ```python
    python3 test.py
    ```
    ![camera list in Python](screenshot/python-list-device.PNG)

## Blog
[0]:https://en.wikipedia.org/wiki/Microsoft_Windows_SDK
Originally forked from yushulx/python-capture-device-list
