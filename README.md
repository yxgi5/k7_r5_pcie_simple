# block design

[doc/system.pdf](doc/system.pdf)

# 需要先给板子上电再给PC上电

也不可以PC运行中复位板子

```
01:00.0 Serial controller: Xilinx Corporation Device 7024 (prog-if 01 [16450])
	Subsystem: Xilinx Corporation Device 0007
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d1300000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [60] Express Endpoint, MSI 00
	Capabilities: [100] Device Serial Number 00-00-00-00-00-00-00-00
	Kernel driver in use: xdma

复位板子
01:00.0 Serial controller: Xilinx Corporation Device 7024 (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel driver in use: xdma


su
lspci -vxd 10ee:*
setpci -d 10ee:7024 COMMAND
setpci -s 01:00.0 COMMAND=0x7
echo 1 > /sys/bus/pci/rescan
echo 1 > /sys/bus/pci/devices/0000\:01\:00.0/rescan
无效

echo 1 > /sys/bus/pci/devices/0000\:01\:00.0/remove
lspci 没有这张卡了

```

# linux kernel

5.4.0-107-generic



