## hhelp
how to find help in bash

```bash
function hhelp() {
  help $1    > /dev/null 2>&1 && echo "yes, help $1"    || echo "no, help $1" ;
  man $1     > /dev/null 2>&1 && echo "yes, man $1"     || echo "no, man $1";
  $1 --help  > /dev/null 2>&1 && echo "yes, $1 --help"  || echo "no, $1 --help";
  $1 -h      > /dev/null 2>&1 && echo "yes, $1 -h"      || echo "no, $1 -h";
  apropos $1 > /dev/null 2>&1 && echo "yes, apropos $1" || echo "no, apropos $1";
  whatis $1  > /dev/null 2>&1 && echo "yes, whatis $1"  || echo "no, whatis $1";
  which $1   > /dev/null 2>&1 && echo "yes, which $1"   || echo "no, which $1";
  declare -f $1 > /dev/null 2>&1 && echo "yes, declare -f $1" || echo "no, declare -f $1"
  # info, not supported on mac so i am not putting in my script.
  # let me know if I am missing any others!
}
```

## Because... sometimes it is hard to find the correct help function on command line.
I was learning about chroot jails and running command lines in docker instances for a next step iteration on the tool!
https://www.baeldung.com/linux/sandboxing-process

## Current Feature requests:
1. **run hhelp in isolation**  
That's pretty neat!  I do not use anything like this but I could see it being useful.  
My only concern is with tools which ignore flags completely and just run. You might end up executing the tool twice (--help and -h) by accident. Most any basic shell script based tool which doesn't include argument parsing will simply run and ignore arguments/flags. It's the default behavior. Not common among established tools, but it's not unheard of.  <br/><br/>
The best way to keep that from happening would be to spin up a small docker image and run it in isolation
