## This repository shows how to create a static library and a dynamic library with GCC and Makefile.The repository contains two project.

'helloA' shows you how to create a static library and a dynamic library with source code.

While 'helloAplus' shows you how to create a dynamic library with a static library.

what is more, i found that u can still use function in the static library though it has been packaged to a dynamic library.

In addition, when u run the test demo, such as demoso. 'demoso' means it generated by using a dynamic library. It will warn that the library can not be found.

To solve this, u shall set LD_LIBRARY_PAHT to the path where the lib is stored.

### export LD_LIBRARY_PATH=$(YOUR_PATH)/lib

