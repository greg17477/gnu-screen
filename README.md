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

