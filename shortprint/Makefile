# Comment/uncomment the following line to disable/enable debugging
#DEBUG = y

EXTRA_CFLAGS += -O2 -I..

ifneq ($(KERNELRELEASE),)
# call from kernel build system

obj-m	:= shortprint.o

else

KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD       := $(shell pwd)

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) modules

endif


clean:
	rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions *.mod modules.order *.symvers

depend .depend dep:
	$(CC) $(EXTRA_CFLAGS) -M *.c > .depend


ifeq (.depend,$(wildcard .depend))
include .depend
endif
