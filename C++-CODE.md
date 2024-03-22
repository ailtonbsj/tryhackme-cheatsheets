# C++ Snippets Utils

```cpp
#include<unistd.h>
void main(){
    setuid(0);
    setgid(0);
    system("/bin/bash");
}
```