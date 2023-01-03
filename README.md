# hpe8k
Tailored Linux kernel configuration for ![HP Compaq 8000 Elite Ultra-slim PC](https://support.hp.com/us-en/product/hp-compaq-8000-elite-ultra-slim-pc/4065899).

![A computer](https://user-images.githubusercontent.com/55889780/210447060-09092437-6cbc-4435-9737-c1404719b1e2.gif)

The main goal of this repository is to get a kernel without too much cruft.

## Some snippets from dmesg:
`
DMI: Hewlett-Packard HP Compaq 8000 Elite USDT PC/3648h, BIOS 786G7 v01.02 10/22/2009

smpboot: CPU0: Intel(R) Core(TM)2 Duo CPU     E8500  @ 3.16GHz (family: 0x6, model: 0x17, stepping: 0xa)

pci 0000:00:00.0: Intel Q45/Q43 Chipset

pci 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable

pci 0000:00:00.0: detected 32768K stolen memory

i915 0000:00:02.0: [drm] fb0: i915drmfb frame buffer device

tpm_tis 00:03: 1.2 TPM (device-id 0xB, rev-id 16)

e1000e: Intel(R) PRO/1000 Network Driver
`
## Some dmesg entries that look troubling or that can use some kernel config changes:
`

ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Address but zero Length: 0x0000000000000050/0x0 (20220331/tbfadt-615)

ACPI BIOS Warning (bug): Invalid length for FADT/Pm2ControlBlock: 0, using default 8 (20220331/tbfadt-669)

Unknown kernel command line parameters "BOOT_IMAGE=../vmlinuz-linux-hpe8k spec_store_bypass_disable=on spectre_v2=on slub_debug=FZP", will be passed to user space.

Memory: 3912404K/4087036K available (10241K kernel code, 963K rwdata, 2512K rodata, 1088K init, 1108K bss, 174372K reserved, 0K cma-reserved)

MDS: Vulnerable: Clear CPU buffers attempted, no microcode

MMIO Stale Data: Unknown: No mitigations

pmd_set_huge: Cannot satisfy [mem 0xf4000000-0xf4200000] with a huge-page mapping due to MTRR override.

acpi LNXCPU:00: Invalid PBLK length [7]

acpi LNXCPU:01: Invalid PBLK length [7]

acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]

ACPI BIOS Error (bug): \_SB.PCI0._OSC: Excess arguments - ASL declared 5, ACPI requires 4 (20220331/nsarguments-162)

ACPI BIOS Error (bug): Failure creating named object [\_SB.PCI0._OSC.CAPD], AE_ALREADY_EXISTS (20220331/dsfield-184)

ACPI Error: AE_ALREADY_EXISTS, CreateBufferField failure (20220331/dswload2-477)

ACPI Error: Aborting method \_SB.PCI0._OSC due to previous error (AE_ALREADY_EXISTS) (20220331/psparse-529)

acpi PNP0A08:00: _OSC: OS requested [PME PCIeCapability LTR]

acpi PNP0A08:00: _OSC: platform willing to grant [PME PCIeCapability LTR]

acpi PNP0A08:00: _OSC: platform retains control of PCIe features (AE_ALREADY_EXISTS)

acpi PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge

pci_bus 0000:10: extended config space not accessible

pnp 00:07: disabling [mem 0x000cc600-0x000e3fff] because it overlaps 0000:00:02.0 BAR 6 [mem 0x000c0000-0x000dffff]

intel_pstate: CPU model not supported

ledtrig-cpu: registered to indicate activity on CPUs

iTCO_wdt iTCO_wdt.1.auto: unable to reset NO_REBOOT flag, device disabled by hardware/BIOS
`