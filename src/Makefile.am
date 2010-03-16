technical_spec = rfc3951.txt
technical_spec_url = http://www.ietf.org/rfc/$(technical_spec)
extract_script = extract-cfile.awk
extract_script_url = http://www.ilbcfreeware.org/documentation/$(extract_script)

checksum_dir = $(srcdir)/known_checksums
EXTRA_DIST = $(checksum_dir)/$(technical_spec).md5 \
	$(checksum_dir)/$(extract_script).md5 \
	$(checksum_dir)/extracted_sources.md5

extracted_sources = \
anaFilter.c  FrameClassify.c  iCBConstruct.c  LPCencode.c \
anaFilter.h  FrameClassify.h  iCBConstruct.h  LPCencode.h \
constants.c  gainquant.c      iCBSearch.c     lsf.c \
constants.h  gainquant.h      iCBSearch.h     lsf.h \
createCB.c   getCBvec.c       iLBC_decode.c   packing.c \
createCB.h   getCBvec.h       iLBC_decode.h   packing.h \
doCPLC.c     helpfun.c        iLBC_define.h   StateConstructW.c \
doCPLC.h     helpfun.h        iLBC_encode.c   StateConstructW.h \
enhancer.c   hpInput.c        iLBC_encode.h   StateSearchW.c \
enhancer.h   hpInput.h        iLBC_test.c     StateSearchW.h \
filter.c     hpOutput.c       LPCdecode.c     syntFilter.c \
filter.h     hpOutput.h       LPCdecode.h     syntFilter.h

BUILT_SOURCES = iLBC_define.h

$(technical_spec):
	$(WGET) $(technical_spec_url)
	$(MD5SUM) -c $(checksum_dir)/$(technical_spec).md5

$(extract_script):
	$(WGET) $(extract_script_url)
	$(MD5SUM) -c $(checksum_dir)/$(extract_script).md5

iLBC_define.h: $(technical_spec) $(extract_script)
	$(AWK) -f $(extract_script) $(technical_spec) > /dev/null
	$(MD5SUM) -c $(checksum_dir)/extracted_sources.md5

lib_LTLIBRARIES = libilbc.la
nodist_libilbc_la_SOURCES = $(extracted_sources)
nodist_ilbc_include_HEADERS = iLBC_decode.h iLBC_encode.h iLBC_define.h
ilbc_includedir = $(includedir)/ilbc
#libilbc_la_LDFLAGS = -lm

downloaded_files = $(technical_spec) $(extract_script) $(extracted_sources)
DISTCLEANFILES = $(downloaded_files)