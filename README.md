# VT-CMPE283-Assignment-4
Nested Paging vs. Shadow Paging

#####The Assignment

####Your assignment is as follows:

 

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

