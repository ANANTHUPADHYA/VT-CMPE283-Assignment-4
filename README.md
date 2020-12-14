# VT-CMPE283-Assignment-4
Nested Paging vs. Shadow Paging

#### CMPE-283-Assignment-4
#### Group -
#### Deesha Desai - 015135536
#### Ananth Upadhya - 015234726

#### Your assignment is as follows:

 

Run your assignment 3 code and boot a test VM using that code.
Once the VM has booted, record total exit count information (total count for each type of exit handled by KVM). You should do this via a sequence of queries of CPUID leaf function 0x4FFFFFFE.
Shutdown your test (inner) VM.
Remove the ‘kvm-intel’ module from your running kernel:
rmmod kvm-intel
Reload the kvm-intel module with the parameter ept=0 (this will disable nested paging and force KVM to use shadow paging instead)
The module you want is usually found in /lib/modules/XXX/kernel/arch/x86/kvm , where XXX is the version of the kernel you build for assignment 3 – don’t make a mistake and use the one that came with the stock Linux installation.
insmod /lib/modules/XXX/kernel/arch/x86/kvm/kvm-intel.ko ept=0
Boot the same test VM again, and capture the same output as you did in step 2.



Permformed the above steps and was successfully able to boot the VM by enabling Shadow paging

####  Questions
##### For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched. (You may skip this question if you are doing the lab by yourself).

As this assignment had no code changes and involved only enabling the Shadow paging we enabled the shadow paging and then then ran the scritps which we had for Assignment 3

* Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”.


* What did you learn from the count of exits? Was the count what you expected? If not, why not?

In shadow paging, the number of exits increases when compared to nested paging. This is expected because during nested paging VM exit occurs when an EPT violation occurs. But in the case of shadow paging, it could exit if VM attempts to execute CR0, CR3, CR4 or any exits which are related to paging such as a page fault.

* What changed between the two runs (ept vs no-ept)?

EPT Mode:
In this mode we have two-layers of page tables which are used to translate from Guest VA to Guest PA and then to Host PA, and more page accesses are required, the guest VM should own page table and hence all the operations on CR3 is done in the same environment, i.e. no need to exit
No EPT Mode:
Guest VM does not own the page table in shadow paging mode. The VMM must simulate CR3.


