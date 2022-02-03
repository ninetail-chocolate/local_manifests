# local_manifests files for albus with Android11
<br>
##For ArrowOS S (Android-12)
You must be installing with OrangeFox recovery
# TAB
Need edits 
	vendor/xaiomi/sdm845-common/Android.bp
		delete code
			cc_prebuilt_library_shared {
			name: "libplatformconfig",
			owner: "xiaomi",
			strip: {
			none: true,
			},
			target: {
			android_arm: {
				srcs: ["proprietary/vendor/lib/libplatformconfig.so"],
			},
			android_arm64: {
				srcs: ["proprietary/vendor/lib64/libplatformconfig.so"],
			},
			},
			compile_multilib: "both",
			check_elf_files: false,
			prefer: true,
			soc_specific: true,
			}
	vendor/arrow/build/tasks/kernel.mk
		reason
			for build etude kernel with prelude-clang
		replace code
			define internal-make-kernel-target
			$(PATH_OVERRIDE) $(KERNEL_MAKE_CMD) $(KERNEL_MAKE_FLAGS) -C $(KERNEL_SRC) O=$(KERNEL_BUILD_OUT_PREFIX)$(1) ARCH=$(KERNEL_ARCH) $(KERNEL_CROSS_COMPILE) $(KERNEL_CLANG_TRIPLE) $(KERNEL_CC) $(KERNEL_LD) $(KERNEL_AR) $(KERNEL_NM) $(KERNEL_OBJCOPY) $(KERNEL_OBJDUMP) $(2)
			endef
---
