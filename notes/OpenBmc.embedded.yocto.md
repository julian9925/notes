---
id: vwhv555f54cvwxj7cpob0zj
title: Yocto Receipe elements
desc: ''
updated: 1700036094501
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


## Pocky


- Pocky is a reference distribution of Yocto Project. The word "reference" is used to mean "example" in this context.

- Yocto project use Poky to build image (Kernel, system, and application software) for targeted hardware.

- At the technical level it is combined repository of its component
 	- Bitlake
 	- OpenEmbedded Core
 	- meta-yocto-bsp
 	- Documentation

> Note: Poky = Bitbake + Metadata

> Note: Poky does not contain binary files,it is a working example of how to build your own custom Linux distribution from source.

### What is difference between poky and Yocto

- The exact difference between Yocto and Poky is Yocto refers to the organization ( like one would refer to 'canonical', the company behind Ubuntu ), and Poky refers to the actual bits downloaded ( analogous to 'Ubuntu' )


## Metadata

- Metadata is collection of
  - Configuration files (.conf)
  - Recipes (.bb and .bbappend)
  - Classes (.bbclass)
  - Include files (.inc)

## Recipes

- Non-Yocto: A receipe is a set of instructions that describe how to prepare or make something, especially a culinary dish.
- Yocto: A recipe is a set of instructions that is read and processed by the bitbake.

- Extension od receipe: .bb

- A Receipe describes:
	- Where to find the source code
	- Which patches to apply
	- Configuration options (Library dependencies, compiler flags, etc)
	- Install
	- License

- Example of a recipe:
	- `dhcp_4.4.1.bb`
	- `gstreamer1.0_1.16.1.bb`

## Configuration Files

- Files which hold global definitions of varaiables and hardware configuration information.
- They tell bitbake how to build the software and put into the image to support a specific hardware platform.
- Extension of configuration files: .conf

- Types:
  - Machine configuration files
	- Distribution configuration options
	- Compiler tuning options
	- General Common Configuration Options
	- USer Configuration Optiopns (local.conf)

## Classes

- Class files are used to abstract common functionality and share it among multiple recipes (.bb) files
- To use a class, you simply make sure the receipe inherits the class.

- Extension of class files: .bbclass

- They are usually placed in classes directory inside the meta* directory.

- Example of a classes:
	- `cmake.bbclass` - Handles cmake in receipes
	- `kernel.bbclass` - Handles buliding kernel. Contains code to build all kernel tree.
	- `module.bbclass` - Provide support for building out-of-tree Linux Kernel Modules.

## Layers

- A layer is a collection of recipes.
- A layer is a directory containing recipes, configuration files, classes, etc. (receipe containers)

- Typical naming convention for layers: meta-<layer_name>

- Poky has the following layers: 
	- meta, meta-poky, meta-yocto-bsp, meta-selftest, meta-skeleton

- Why Layers:
  -  Layers provide a mechanism to isolate meta data according to functionality, for instance BSPs, distribution configuration, etc.

	- For instance, you should have a BSP layer, a GUI layer, a distro configuration layer, middleware layer, or an application layer.
	- Putting you entire build into one layer limits and complicates fureture customization and maintenance.

	- Example:
		- meta-yocto-bsp   -- BSP metadata
		- meta-pocky			 -- Distro metadata

	- Layers allow you to easily add entire set of meta data and/or replace sets with other sets.

	- meta-pocky, is itself a layer applied on top of the QE-Core metadata layer.

## Which layers are used by Pocky build system?

  BBLAYERS varaible in `build/conf/bblayers.conf` file lists the layers Bitbake tries to find.

  If bblayers.conf file is not present when you start the build, the OpenEmbedded build system will create a default bblayers.conf.sample when you source the oe-init-build-env script.

- command to find out whick layers are present in the build system:
	- go to pocky directory
	- `source ./oe-init-build-env`
	- `bitbake-layers show-layers`

## Image

An image is the top level receipe, it has a description, a license and inherits from the core-image class.

It is used alongside the machine definition, machine describes the hardware used and its capabilities

Image is archecture agnostic and defines how the root filesystem is built, with the packages to include and the configuration to apply.

 - Command to check the list of available images:
	 - `ls meta*/recipes*/images/*.bb`

## Package

- A package is a software component that can be installed on a system. Such as file with name `*.rpm` ,`*.ipk` or `*.deb`

- A single recipe can produce multiple packages. All pacakges that a receipe generated are listed in the receipe varaiable.

- Example:
	- `dhcp_4.4.1.bb` - dhcp, dhcp-client, dhcp-dev, dhcp-doc, dhcp-server