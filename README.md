# gnu-screen

In order to get this package compiled on rhel5:

1. ./configure --enable-colors256

2. Edit line 253 in the file "os.h":

  from:
    
    # if defined(SVR4) && !defined(DGUX) && !defined(__hpux)
    
  to:
   
    # if defined(SVR4) && !defined(DGUX) && !defined(__hpux) && !defined(linux)
    
3. make

4. make install

*******************************************************************************
# 256 colors for hardstatus line

This version includes patch from https://github.com/shawncplus/patches which enables 256
colors for the hardstatus line. It's important to set the end of the
statusline to terminals background and foreground colors. Usually it's
black and white or dark and bright.

From the doc:
256-color (foreground) token. %1G is basic red, %197G would be a bright
magenta. The number corresponds to the cterm index. %xxB is for
background.

Example: Hostname in black on orange:

  hardstatus alwayslastline "%202B%16G %H %0G"

How to get the color table:

  for i in {0..255} ; do
    printf "\x1b[38;5;${i}mcolour${i}\n"
  done
