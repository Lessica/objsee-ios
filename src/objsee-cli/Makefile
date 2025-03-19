ARCHS := arm64
TARGET := iphone:clang:latest:16.1

include $(THEOS)/makefiles/common.mk

INCLUDE_DIRS := $(shell find . ../libobjsee -type d)
INCLUDE_FLAGS := $(INCLUDE_DIRS:%=-I%)

TOOL_NAME = objsee-cli
objsee-cli_INSTALL_PATH = /usr/local/bin
objsee-cli_FILES += $(shell find . -type f \( -name '*.c' -o -name '*.m' \)) $(shell find ../libobjsee -type f \( -name '*.c' -o -name '*.m' \)) $(wildcard ../../dependencies/kat/*.c)
objsee-cli_CFLAGS += -fobjc-arc
objsee-cli_CFLAGS += $(INCLUDE_FLAGS)
objsee-cli_CFLAGS += -I./../../dependencies/include
objsee-cli_CFLAGS += -I./../../dependencies/kat
objsee-cli_CFLAGS += -Wno-unused-but-set-variable
objsee-cli_CFLAGS += -DOBJSEE_CLI_VERSION=\"$(PACKAGE_VERSION)\"
objsee-cli_CFLAGS += -DOBJSEE_LIB_VERSION=\"$(PACKAGE_VERSION)\"
objsee-cli_LDFLAGS += -L../../dependencies/libs/
objsee-cli_LDFLAGS += -ljson-c-ios
objsee-cli_LDFLAGS += -lncursesw-ios
objsee-cli_LDFLAGS += -lcapstone-ios
objsee-cli_CODESIGN_FLAGS += -S./objsee-entitlements.xml
include $(THEOS_MAKE_PATH)/tool.mk