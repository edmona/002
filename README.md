# 002003
A PCI Express Port can provide up to four distinct functions,
referred to in this document as services, depending on its port type.
PCI Express Port's services include native hotplug support (HP),
power management event support (PME), advanced error reporting
support (AER), and virtual channel support (VC). These services may
be handled by a single complex driver or be individually distributed
In existing Linux kernels, the Linux Device Driver Model allows a
physical device to be handled by only a single driver. The PCI
Express Port is a PCI-PCI Bridge device with multiple distinct
services. To maintain a clean and simple solution each service
may have its own software service driver. In this case several
service drivers will compete for a single PCI-PCI Bridge device.
For example, if the PCI Express Root Port native hotplug service
driver is loaded first, it claims a PCI-PCI Bridge Root Port. The
kernel therefore does not load other service drivers for that Root
Port. In other words, it is impossible to have multiple service
drivers load and run on a PCI-PCI Bridge device simultaneously
using the current driver model.112
