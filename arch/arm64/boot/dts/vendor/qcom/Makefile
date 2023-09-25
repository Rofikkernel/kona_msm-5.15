# add-overlay defines the target with following naming convention:
# <base>-<board>-dtbs = base.dtb board.dtbo
#
# Combined dtb target is also generated using the fdt_overlay tool.
# dtb-y += <base>-<board>.dtb

add-overlays = $(foreach o,$1,$(foreach b,$2,$(eval $(basename $b)-$(basename $o)-dtbs = $b $o) $(basename $b)-$(basename $o).dtb))

# kalama-dtb-y is list of DTBs to install when doing non-overlay build
# kalama-overlays-dtb-y is list of DTBs and DTBOs to install when doing overlay-supported build
# see DTB_TYPES from scripts/Makefile.dtbinst and install_dtbs from build.config.msm.common
# RofikKernel add Kona device tree for 5.15, is implementation is different from 4.19
# copy kalama implementation
ifneq ($(CONFIG_ARCH_QTI_VM), y)

KONA_BASE_DTB += kona.dtb kona-v2.dtb kona-v2.1.dtb

KONA_BOARDS += \
		 		kona-cdp-overlay.dtbo \
                kona-cdp-lcd-overlay.dtbo \
                kona-mtp-overlay.dtbo \
                kona-mtp-ws-overlay.dtbo \
				kona-sa-mtp-overlay.dtbo \
                kona-xr-overlay.dtbo \
                apollo-sm8250-overlay.dtbo \
                alioth-sm8250-overlay.dtbo \
                kona-rumi-overlay.dtbo \
                kona-qrd-overlay.dtbo \
				kona-xrfusion-overlay.dtbo \
				kona-xrfusion-ult-overlay.dtbo \
                kona-hdk-overlay.dtbo

kona-dtb-$(CONFIG_ARCH_KONA) += \
	$(call add-overlays, $(KONA_BOARDS),$(KONA_BASE_DTB))
kona-overlays-dtb-$(CONFIG_ARCH_KONA) += $(KONA_BOARDS) $(KONA_BASE_DTB)
dtb-y += $(kona-dtb-y)

endif

always-y        := $(dtb-y)
subdir-y        := $(dts-dirs)
clean-files     := *.dtb *.dtbo
