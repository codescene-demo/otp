#
# %CopyrightBegin%
# 
# Copyright Ericsson AB 2001-2020. All Rights Reserved.
# 
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# 
# %CopyrightEnd%
#
#
include $(ERL_TOP)/make/target.mk
include $(ERL_TOP)/make/$(TARGET)/otp.mk

# ----------------------------------------------------
# Application version
# ----------------------------------------------------
include $(ERL_TOP)/erts/vsn.mk
#VSN=$(SYSTEM_VSN)

APPLICATION=otp-system-documentation
XMLDIR := $(XMLDIR)/efficiency_guide
# ----------------------------------------------------
# Release directory specification
# ----------------------------------------------------
RELSYSDIR = $(RELEASE_PATH)/doc/efficiency_guide

# ----------------------------------------------------
# Target Specs
# ----------------------------------------------------
XML_PART_FILES = part.xml

include xmlfiles.mk

XML_CHAPTER_FILES = $(EFF_GUIDE_CHAPTER_FILES)

TOPDOCDIR=..

BOOK_FILES = book.xml

PS_FILES = digger.ps

XML_FILES = \
	$(BOOK_FILES) $(XML_CHAPTER_FILES) \
	$(XML_PART_FILES) 

# ----------------------------------------------------

C_FILES = \

ERL_FILES = all.erl\
	bench.erl\
	call_bm.erl

HRL_FILES = bench.hrl


MISC_FILES = call_result.html\
	README

HTML_FILES = \
	$(XML_PART_FILES:%.xml=%.html)

HTMLDIR = ../html/efficiency_guide

EXTRA_FILES = $(ERL_FILES) \
	$(HRL_FILES) \
	$(MISC_FILES) 

HTML_UG_FILE = $(HTMLDIR)/users_guide.html

# ----------------------------------------------------
# FLAGS 
# ----------------------------------------------------
XML_FLAGS += 
DVIPS_FLAGS += 

# ----------------------------------------------------
# Targets
# ----------------------------------------------------

DOC_TARGETS?=html

docs: $(DOC_TARGETS)

local_docs: PDFDIR=../../pdf

html: $(GIF_FILES) $(HTML_UG_FILE)

debug opt: 

clean clean_docs:
	rm -f $(XMLDIR)/*.xml
	rm -f $(HTMLDIR)/*.gif $(HTMLDIR)/*.html
	rm -f $(TOP_PDF_FILE) $(TOP_PDF_FILE:%.pdf=%.fo)
	rm -f errs core *~ 

# ----------------------------------------------------
# Release Target
# ---------------------------------------------------- 
include $(ERL_TOP)/make/otp_release_targets.mk

release_html_spec: html
	$(INSTALL_DIR) "$(RELSYSDIR)"
	$(INSTALL_DATA) $(GIF_FILES) $(EXTRA_FILES) $(HTMLDIR)/*.html \
		"$(RELSYSDIR)"

release_docs_spec: $(DOC_TARGETS:%=release_%_spec)

release_spec:
