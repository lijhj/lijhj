### [Minimal Makefile](https://github.com/lijh8/Minimal-Makefile)

```
# build dynamic library with -fPIC -shared
CFLAGS   = -g # -O3 -fPIC # CXXFLAGS for .cpp
CPPFLAGS = -MMD -MP # -I../foo -DNDEBUG
LDFLAGS  = # -L../foo -shared
LDLIBS   = # -lfoo
#CC      = $(CXX) # link with CXX for .cpp

# target name is basename of one of the source files
main : $(patsubst %.c,%.o,$(wildcard *.c)) # .cpp
-include *.d
clean : ; -rm -fr *.o *.d main
.PHONY : clean
```

---

### [Imitating tuple in Golang](https://github.com/lijh8/go2work/blob/main/tuple2/tuple2.go)

```
import tuple2

func main() {
	a := []any{"abc", 123, 3.14}
	b := []any{"abc", 123, 3.14}
	c, ok := tuple2.Compare(a, b)
	fmt.Println(c, ok)
}
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
