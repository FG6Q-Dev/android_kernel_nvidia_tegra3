# bcm43241
DHDCFLAGS = -Wall -Wstrict-prototypes -Dlinux -DBCMDRIVER                 \
	-DBCMDONGLEHOST -DUNRELEASEDCHIP -DBCMDMA32 -DBCMFILEIMAGE            \
	-DDHDTHREAD -DDHD_DEBUG -DSDTEST -DBDC -DTOE                          \
	-DDHD_BCMEVENTS -DSHOW_EVENTS -DPROP_TXSTATUS -DBCMDBG                \
	-DCUSTOMER_HW2 -DUSE_KTHREAD_API                                      \
	-DMMC_SDIO_ABORT -DBCMSDIO -DBCMLXSDMMC -DBCMPLATFORM_BUS -DWLP2P     \
	-DWIFI_ACT_FRAME -DARP_OFFLOAD_SUPPORT                                \
	-DKEEP_ALIVE -DGET_CUSTOM_MAC_ENABLE -DPKT_FILTER_SUPPORT             \
	-DEMBEDDED_PLATFORM -DPNO_SUPPORT                                     \
	-DDHD_USE_IDLECOUNT -DSET_RANDOM_MAC_SOFTAP -DROAM_ENABLE -DVSDB      \
	-DWL_CFG80211_VSDB_PRIORITIZE_SCAN_REQUEST                            \
	-DESCAN_RESULT_PATCH -DHT40_GO -DPASS_ARP_PACKET -DSDIO_CRC_ERROR_FIX \
	-DDHD_DONOT_FORWARD_BCMEVENT_AS_NETWORK_PKT                           \
	-Idrivers/net/wireless/bcm43241 -Idrivers/net/wireless/bcm43241/include

DHDCFLAGS += -DCONFIG_WIFI_CONTROL_FUNC

# bcm43241 specific
DHDCFLAGS += -DCUSTOM_SDIO_F2_BLKSIZE=128 -DSUPPORT_PM2_ONLY
DHDCFLAGS += -DAMPDU_HOSTREORDER
DHDCFLAGS += -DCUSTOM_ROAM_TRIGGER_SETTING=-65
DHDCFLAGS += -DCUSTOM_ROAM_DELTA_SETTING=15
DHDCFLAGS += -DCUSTOM_KEEP_ALIVE_SETTING=28000
#DHDCFLAGS += -DCUSTOM_PNO_EVENT_LOCK_xTIME=7
DHDCFLAGS += -DQUEUE_BW
#DHDCFLAGS += -DVSDB_BW_ALLOCATE_ENABLE
DHDCFLAGS += -DP2P_DISCOVERY_WAR

## Set dhd_dpd_thread priority to MAX to avoid starvation
DHDCFLAGS += -DCUSTOM_DPC_PRIO_SETTING=99

DHDCFLAGS += -DHW_OOB -DOOB_INTR_ONLY
DHDCFLAGS += -DENABLE_INSMOD_NO_FW_LOAD
DHDCFLAGS += -DWIFIEDP

DHDOFILES = aiutils.o bcmsdh_sdmmc_linux.o dhd_linux.o siutils.o bcmutils.o   \
	dhd_linux_sched.o dhd_sdio.o bcmwifi_channels.o bcmevent.o hndpmu.o   \
	bcmsdh.o dhd_cdc.o bcmsdh_linux.o dhd_common.o linux_osl.o            \
	bcmsdh_sdmmc.o dhd_custom_gpio.o sbutils.o wldev_common.o wl_android.o

obj-$(CONFIG_BCM43241) += bcm43241.o
bcm43241-objs += $(DHDOFILES)

bcm43241-objs += wl_cfg80211.o wl_cfgp2p.o wl_linux_mon.o dhd_cfg80211.o
DHDCFLAGS += -DWL_CFG80211 -DWL_CFG80211_STA_EVENT -DWL_ENABLE_P2P_IF

EXTRA_CFLAGS = $(DHDCFLAGS)
ifeq ($(CONFIG_BCM43241),m)
EXTRA_LDFLAGS += --strip-debug
endif
