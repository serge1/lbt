# Copyright (c) 2004,  Theodore A. Roth
# Copyright (c) 2005, 2008  Anatoly Sokolov
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
# * Redistributions of source code must retain the above copyright
#   notice, this list of conditions and the following disclaimer.
# * Redistributions in binary form must reproduce the above copyright
#   notice, this list of conditions and the following disclaimer in
#   the documentation and/or other materials provided with the
#   distribution.
# * Neither the name of the copyright holders nor the names of
#   contributors may be used to endorse or promote products derived
#   from this software without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
# ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE
# LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR
# CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF
# SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
# INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN
# CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE)
# ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
# POSSIBILITY OF SUCH DAMAGE.
#

AVR_TARGET          = at90s4434
AVR_TARGET_CRT      = crts4434.o
AVR_TARGET_DEFS     = 
AVR_TARGET_CFLAGS   = -mcall-prologues -Os
AVR_TARGET_ASFLAGS  = 
AVR_INSTALL_DIR     = 

VPATH = $(top_srcdir)/crt1

if HAS_at90s4434

AM_CPPFLAGS = -I$(top_srcdir)/common -I$(top_srcdir)/include -I$(top_builddir)/include

AVRLIB_CFLAGS = @CDEBUG@ -Wall -W -Wstrict-prototypes -mmcu=$(AVR_TARGET) $(AVR_TARGET_DEFS) $(AVR_TARGET_CFLAGS)

AVRLIB_ASFLAGS = -x assembler-with-cpp @ASDEBUG@ -mmcu=$(AVR_TARGET) $(AVR_TARGET_DEFS) -DIOSYMFILE=\"iosym/$(AVR_TARGET).S\" $(AVR_TARGET_ASFLAGS)

AM_CFLAGS = $(AVRLIB_CFLAGS)
AM_CCASFLAGS = $(AM_CPPFLAGS) $(AVRLIB_ASFLAGS)


__install_dir = $(prefix)/avr/lib/$(AVR_INSTALL_DIR)

avrdir = $(__install_dir)
avrlibdir = $(__install_dir)

noinst_LIBRARIES = libcrt.a
nodist_libcrt_a_SOURCES = gcrt1.S

avr_DATA = $(AVR_TARGET_CRT)

$(AVR_TARGET_CRT): gcrt1.o
	rm -f $@
	ln $< $@ || cp $< $@

else

echo all distdir install installdirs clean distclean uninstall check:

endif
