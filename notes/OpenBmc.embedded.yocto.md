---
id: vwhv555f54cvwxj7cpob0zj
title: Yocto elements
desc: ''
updated: 1698895807215
created: 1698887426299
---

## Linux Embedded Necessaries

### Toolchain
- Compiler and otehr tools needed to create code for your target devices.

### Bootloader
- The program that initializes the board and loads Linux Kernel.

### Kernel
- This is the heart of system, managing system resources and interfacing eith hardware.

### Root filesystem
- Contains the libraries and program that run once the kernel has completed its initialization.

---

## Yocto Project

- Ycoto provides open source, high quality infrastructure and tools to help developers create their own custom Linux distributions for any hardware architecture.

## Advantages of Yocto Project

- Widely Adopted Across the Industry
	 - Semiconductor, operating system, software, and service vendors exist whose products and services adopt and support the Yocto Project.
	Eg. Intel, Facebook, arm, Juniper Networks, LG, AMD, NXP, DELL


- Architecture Agnostic
	- supports Intel, ARM, MIPS, AMD, PPC and other architectures
	chip vendors create and supply BSPs that support their hardware
	if you have custom silicon, you can create a BSP that supports that architecture
	the Yocto Project fully supports a wide range of device emulation through the Quick EMUlator (QEMU)


- Images and Code Transfer Easily
	- Yocto Project output can easily move between architectures without moving to new development environments.


- Flexibility
	- Through customization and layering, a project group can leverage the base Linux distribution to create a distribution that works for their product needs.


- Ideal for Constrained Embedded and IoT devices
	- Unlike a full Linux distribution, you can use the Yocto Project to create exactly what you need for embedded devices
	You only add the feature support or packages that you absolutely need for the device


- Uses a Layer Model
	- The Yocto Project layer infrastructure groups related functionality into separate bundles.
	You can incrementally add these grouped functionalities to your project as needed
	Allows you to easily extend the system, make customizations, and keep functionality organized.

## Metadata

Metadata refers to the build instructions
Commands and data used to indicate waht versions of software are used


---

## Pocky
- Pocky is a reference distribution of Yocto Project. The word "reference" is used to mean "example" in this context.

- Yocto project use Poky to build image (Kernel, system, and application software) for targeted hardware.

- At the technical level it is combined repository of its component
 	- Bitlake
 	- OpenEmbedded Core
 	- meta-yocto-bsp
 	- Documentation

> Note: Poky does not contain binary files,it is a working example of how to build your own custom Linux distribution from source.

### What is difference between poky and Yocto

- The exact difference between Yocto and Poky is Yocto refers to the organization ( like one would refer to 'canonical', the company behind Ubuntu ), and Poky refers to the actual bits downloaded ( analogous to 'Ubuntu' )