
## poky source tree

- **poky**
	- **bitbake**:

		Holds all Python scripts used by the bitbake command bitbake/bin is placed into the PATH environmental variable so bitbake can be found

	- **documentation**

		All documentation sources for the Yocto Project documentation can be used to generate nice PDF

	- **meta**

	  Contains the oe-core metadata

		- **meta-poky**

		  Holds the configuration for the Poky reference distribution	local.conf.sample, bblayers.conf.sample are present here

		- **meta-yocto-bsp**

		  Maintains several BSPs such as the Beaglebone, EdgeRouter, and generic versions of both 32-bit and 64-bit IA machines.

		- **meta-skeleton**

		  Contains template recipes for BSP and kernel development

	- **scripts**

	  Contains scripts used to set up the environment, development tools, and tools to flash the generated images on the target.

	- **LICENSE**

	  The license under which Poky is distributed (a mix of GPLv2 and MIT)