
1. To compile as a library the following needs to be adjusted.

For the time being, the configure files are set right. May need to remove the configure call in the main makefile so that the meschach libraries are compiled with the correct flag.
1. In the src/makefile do the last line needs to be included also would be nice if the version number auto populated.
gstat-lib:	$(OBJS)
	ar vru ../lib/libgstat.a $(OBJS)
	cp $(LIBHEADERS) ../gstatinc
	gcc -shared -fPIC -Wl,-soname,libgstat.so.2 -o ../lib/libgstat.so.2.5.2 $(OBJS) $(MESCHACH_OBJS) -lc

3. If the library is to be compiled meschach needs to have --with-sparse set.
4. In src/make file the mfun.o line has to be removed. There is no correspondinc *.c
MESCHACH_OBJS = \
	../meschach/mfunc.$(O) \
5. The configuration option --with-gdal-config semms to break around testing ex12 or ex13

2. Implement Boost
3. Generate libraries and executables (gstatpy, libgstat.so, gstat)
4. Implement CUDA