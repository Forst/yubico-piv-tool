# Copyright (c) 2015-2016 Yubico AB
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are
# met:
#
#     * Redistributions of source code must retain the above copyright
#       notice, this list of conditions and the following disclaimer.
#
#     * Redistributions in binary form must reproduce the above
#       copyright notice, this list of conditions and the following
#       disclaimer in the documentation and/or other materials provided
#       with the distribution.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
# SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
# LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
# DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
# THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
# (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

#TESTS_ENVIRONMENT = export VERSION=$(PACKAGE_VERSION); export EXEEXT=$(EXEEXT);

#LOG_COMPILER = $(VALGRIND)

AM_CFLAGS = $(WARN_CFLAGS) @CHECK_CFLAGS@
AM_CPPFLAGS = -I$(top_srcdir)/lib -I$(top_builddir)/lib
AM_CPPFLAGS += -I$(top_srcdir)/ykcs11 -I$(top_builddir)/ykcs11
AM_CPPFLAGS += $(OPENSSL_CFLAGS)

AM_LDFLAGS = @CHECK_LIBS@

if COMPILER_CLANG
AM_LDFLAGS += -no-fast-install
else
AM_LDFLAGS += -no-install
endif

ykcs11_tests_LDADD = ../libykcs11.la $(OPENSSL_LIBS) ../../tool/libpiv_util.la
ykcs11_tests_SOURCES = ykcs11_tests.c ykcs11_tests_util.c ykcs11_tests_util.h
check_PROGRAMS = ykcs11_tests
TESTS = reset.sh $(check_PROGRAMS)

if ENABLE_COV
AM_LDFLAGS += --coverage
endif
