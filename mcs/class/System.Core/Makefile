thisdir = class/System.Core
SUBDIRS = 
include ../../build/rules.make

LIBRARY = System.Core.dll

LIB_MCS_FLAGS = -d:LIBC /r:$(corlib) /r:System

ifneq (2.1, $(FRAMEWORK_VERSION))
LIB_MCS_FLAGS += -d:NET_3_5 -nowarn:1720
endif

ifeq (4.0, $(FRAMEWORK_VERSION))
LIB_MCS_FLAGS += -d:CODEPLEX_40
endif

ifeq (net_4_0, $(PROFILE))
USE_BOOT_COMBILE = yes
LIBRARY_COMPILE = $(BOOT_COMPILE)
endif

CLR_PROFILE := $(filter 2.0 4.0, $(FRAMEWORK_VERSION))
ifdef CLR_PROFILE
LIB_MCS_FLAGS += -r:Mono.Posix -unsafe
endif

TEST_MCS_FLAGS = $(LIB_MCS_FLAGS)

# This is a .NET 2.0+ only assembly
VALID_PROFILE := $(filter 2.0 2.1 4.0, $(FRAMEWORK_VERSION))
ifndef VALID_PROFILE
LIBRARY_NAME = dummy-System.Core.dll
NO_INSTALL = yes
NO_SIGN_ASSEMBLY = yes
NO_TEST = yes
NO_BUILD = yes
endif

include ../../build/library.make

