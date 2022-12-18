### Minimal Makefile ⚡
_Automatic Makefile for C and C++_
```
# build shared library with -fPIC, -shared
CFLAGS   = -g # -O3 -fPIC # CXXFLAGS for .cpp
LDFLAGS  = # -L../bar -Wl,-rpath,/foo/bar # -shared
LDLIBS   = # -lbar
CPPFLAGS = -MMD -MP # -I../bar
#CC      = $(CXX) # link with CXX for .cpp

# target name is basename of one of the source files
main : $(patsubst %.c,%.o,$(wildcard *.c)) # .cpp
-include *.d
clean : ; -rm -fr *.o *.d
.PHONY : clean
```

<!--
**ljhm/ljhm** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.
 
Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
