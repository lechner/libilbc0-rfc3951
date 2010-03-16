license = gips_iLBClicense.pdf
license_url = http://www.ilbcfreeware.org/documentation/$(license)
#license_url = http://gipscorp.com/files/english/$(license)

BUILT_SOURCES = $(license)

$(license):
	$(WGET) $(license_url)

DISTCLEANFILES = $(license)
