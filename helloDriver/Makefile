obj-m := hello.o
#当前路径
CURRENT_PATH := $(shell pwd)
#内核版本
LINUX_KERNEL := $(shell uname -r)
#内核版本路径
CURRENT_KERNEL_PATH := /usr/src/linux-headers-$(LINUX_KERNEL)

all:
	make -C $(CURRENT_KERNEL_PATH) M=$(CURRENT_PATH) modules
clean:
	make -C $(CURRENT_KERNEL_PATH) M=$(CURRENT_PATH) clean

# If KERNELRELEASE is defined, we've been invoked from the 
# # kernel build system and can use its language. 
ifneq ($(KERNELRELEASE),)
        obj-m := hello.o 
#  # Otherwise we were called directly from the command 
# line; invoke the kernel build system. 
# 17 
# bbs.theithome.com
# LINUX DEVICE DRIVERS，3RD EDITION
else
        KERNELDIR ?= /lib/modules/$(shell uname -r)/build
        PWD := $(shell pwd)
        default:
        $(MAKE) -C $(KERNELDIR) M=$(PWD) modules
endif
