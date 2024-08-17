### Minimal Makefile

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

### Imitating tuple in Golang

```
import tuple2

func main() {
	a := []any{"abc", 123, 3.14}
	b := []any{"abc", 123, 3.14}
	c, ok := tuple2.Compare(a, b)
	fmt.Println(c, ok)
}
```

```
package tuple2

import (
	"cmp"
	"reflect"
)

func Compare(a, b []any) (int, bool) {
	if len(a) != len(b) {
		return 0, false
	}

	for i := range a {
		if a[i] == nil || b[i] == nil {
			return 0, false
		}

		if _, boolean := a[i].(bool); boolean {
			return 0, false
		}
		if _, boolean := b[i].(bool); boolean {
			return 0, false
		}

		if a, b := reflect.TypeOf(a[i]), reflect.TypeOf(b[i]); a != b {
			return 0, false
		}

		if a, aOk := a[i].(string); aOk {
			if b, bOk := b[i].(string); bOk {
				if c := cmp.Compare(a, b); c != 0 {
					return c, true
				}
			}
		}

		if a, aOk := a[i].(int); aOk {
			if b, bOk := b[i].(int); bOk {
				if c := cmp.Compare(a, b); c != 0 {
					return c, true
				}
			}
		}

		if a, aOk := a[i].(float64); aOk {
			if b, bOk := b[i].(float64); bOk {
				if c := cmp.Compare(a, b); c != 0 {
					return c, true
				}
			}
		}

		if a, aOk := a[i].([]any); aOk {
			if b, bOk := b[i].([]any); bOk {
				if c, ok := Compare(a, b); ok && c != 0 {
					return c, true
				} else if !ok {
					return 0, false
				}
			}
		}
	}
	return 0, true
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
