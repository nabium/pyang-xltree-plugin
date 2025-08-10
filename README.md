XLTree output plugin for pyang
============================================================

Overview
------------------------------------------------------------

XLTree is a plugin for [pyang](https://github.com/mbj4668/pyang)
to output various aspects of YANG models to an Excel(xlsx) file.

- tree representation of data, rpc and notification
- list of enums for enum-like enumeration and identityref typedefs
- inheritance tree of identities
- relationship of modules


Requirements
------------------------------------------------------------

Aside form pyang this plugin depends on following libraries.

- [openpyxl](https://foss.heptapod.net/openpyxl/openpyxl)


How to use
------------------------------------------------------------

### 1) clone repository

```
> git clone https://github.com/nabium/pyang-xltree-plugin.git
> cd pyang-xltree-plugin
```

### 2) (optional) create venv

```
> python -m venv --prompt xltree venv
> venv\Scripts\activate
(xltree) > python --version
Python 3.12.2
(xltree) > python -m pip install --upgrade pip
```

### 3) install pyang and openpyxl

```
(xltree) > pip install pyang setuptools openpyxl
(xltree) > pip list
Package    Version
---------- -------
et-xmlfile 1.1.0
lxml       5.1.0
openpyxl   3.1.2
pip        24.0
pyang      2.6.0
setuptools 69.1.1
```

### 4) run pyang with xltree output

```
(xltree) > python -m pyang --plugindir=. -f xltree --xltree-out=xltree.xlsx YANG_FILES...
```

Run `python -m pyang --plugindir=. --help` for other options.


Options
------------------------------------------------------------

- --plugindir=DIR

  Directory where plugin file `xltree.py` is located.

- -f xltree

  Use xltree output plugin.

- --xltree-out=FILE

  Excel file for output.
  Default is `xltree.xlsx`.
  This plugin cannot output contents to `stdout` or to the file specified by `-o`
  as they are opend in text mode.

- --xltree-font=FONT

  Name of the font to use.
  ex.) Calibri, "Yu Gothic Medium"


Examples
------------------------------------------------------------

### TAPI 2.4.1

If you have [TAPI 2.4.1](https://github.com/Open-Network-Models-and-Interfaces-ONMI/TAPI/tree/v2.4.1/YANG) YANG files under `C:\data\yang\tapi-2.4.1`:

```
python -m pyang C:\data\yang\tapi-2.4.1\tapi-common.yang C:\data\yang\tapi-2.4.1\tapi-connectivity.yang C:\data\yang\tapi-2.4.1\tapi-digital-otn.yang C:\data\yang\tapi-2.4.1\tapi-dsr.yang C:\data\yang\tapi-2.4.1\tapi-equipment.yang C:\data\yang\tapi-2.4.1\tapi-eth.yang C:\data\yang\tapi-2.4.1\tapi-fm.yang C:\data\yang\tapi-2.4.1\tapi-notification.yang C:\data\yang\tapi-2.4.1\tapi-oam.yang C:\data\yang\tapi-2.4.1\tapi-path-computation.yang C:\data\yang\tapi-2.4.1\tapi-photonic-media.yang C:\data\yang\tapi-2.4.1\tapi-streaming.yang C:\data\yang\tapi-2.4.1\tapi-topology.yang C:\data\yang\tapi-2.4.1\tapi-virtual-network.yang --plugindir=. -f xltree --xltree-out tapi-2.4.1.xlsx --xltree-font=Calibri
```


### TAPI 2.5.0

If you have [TAPI 2.5.0](https://github.com/Open-Network-Models-and-Interfaces-ONMI/TAPI/tree/v2.5.0/YANG) YANG files under `C:\data\yang\tapi-2.5.0`:

```
python -m pyang C:\data\yang\tapi-2.5.0\tapi-common.yang C:\data\yang\tapi-2.5.0\tapi-connectivity.yang C:\data\yang\tapi-2.5.0\tapi-digital-otn.yang C:\data\yang\tapi-2.5.0\tapi-dsr.yang C:\data\yang\tapi-2.5.0\tapi-equipment.yang C:\data\yang\tapi-2.5.0\tapi-eth.yang C:\data\yang\tapi-2.5.0\tapi-fm.yang C:\data\yang\tapi-2.5.0\tapi-gnmi-streaming.yang C:\data\yang\tapi-2.5.0\tapi-notification.yang C:\data\yang\tapi-2.5.0\tapi-oam.yang C:\data\yang\tapi-2.5.0\tapi-path-computation.yang C:\data\yang\tapi-2.5.0\tapi-photonic-media.yang C:\data\yang\tapi-2.5.0\tapi-streaming.yang C:\data\yang\tapi-2.5.0\tapi-topology.yang C:\data\yang\tapi-2.5.0\tapi-virtual-network.yang --plugindir=. -f xltree --xltree-out tapi-2.5.0.xlsx --xltree-font=Calibri
```


### TAPI 2.6.0

If you have [TAPI 2.6.0](https://github.com/Open-Network-Models-and-Interfaces-ONMI/TAPI/tree/v2.6.0/YANG) YANG files under `C:\data\yang\tapi-2.6.0`:

```
python -m pyang C:\data\yang\tapi-2.6.0\tapi-common.yang C:\data\yang\tapi-2.6.0\tapi-connectivity.yang C:\data\yang\tapi-2.6.0\tapi-digital-otn.yang C:\data\yang\tapi-2.6.0\tapi-dsr.yang C:\data\yang\tapi-2.6.0\tapi-equipment.yang C:\data\yang\tapi-2.6.0\tapi-eth.yang C:\data\yang\tapi-2.6.0\tapi-fm.yang C:\data\yang\tapi-2.6.0\tapi-gnmi-streaming.yang C:\data\yang\tapi-2.6.0\tapi-notification.yang C:\data\yang\tapi-2.6.0\tapi-oam.yang C:\data\yang\tapi-2.6.0\tapi-path-computation.yang C:\data\yang\tapi-2.6.0\tapi-photonic-media.yang C:\data\yang\tapi-2.6.0\tapi-streaming.yang C:\data\yang\tapi-2.6.0\tapi-topology.yang C:\data\yang\tapi-2.6.0\tapi-virtual-network.yang --plugindir=. -f xltree --xltree-out tapi-2.6.0.xlsx --xltree-font=Calibri
```


### OpenROADM 7.1

If you have [OpenROADM 7.1](https://github.com/OpenROADM/OpenROADM_MSA_Public/tree/7.1.0/model) YANG files under `C:\data\yang\openroadm-7.1.0` and dependents under `C:\data\yang\{iana,ietf}`:

```
python -m pyang -p C:\data\yang\iana;C:\data\yang\ietf C:\data\yang\ietf\ietf-network@2018-02-26.yang C:\data\yang\ietf\ietf-network-topology@2018-02-26.yang C:\data\yang\ietf\ietf-network-state@2018-02-26.yang C:\data\yang\ietf\ietf-network-topology-state@2018-02-26.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-alarm.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-alarm-pm-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-amplifier-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-attributes.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-equipment-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-link-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-node-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-optical-channel-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-state-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-common-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-equipment-states-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-interfaces.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-layerRate.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-manifest-file.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-network-resource.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-otn-common-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-pm-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-pm.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-port-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-probable-cause.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-resource-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-resource.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-service-format.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-switching-pool-types.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-tca.yang C:\data\yang\openroadm-7.1.0\Common\org-openroadm-user-mgmt.yang C:\data\yang\openroadm-7.1.0\Device\openconfig-extensions.yang C:\data\yang\openroadm-7.1.0\Device\openconfig-inet-types.yang C:\data\yang\openroadm-7.1.0\Device\openconfig-telemetry-types.yang C:\data\yang\openroadm-7.1.0\Device\openconfig-telemetry.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-database.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-de-operations.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-device-types.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-device.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-dhcp.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-ethernet-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-file-transfer.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-fwdl.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-gcc-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-gnmi.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-ip.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-ipv4-unicast-routing.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-ipv6-unicast-routing.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-key-chain.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-lldp.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-maintenance-loopback.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-maintenance-testsignal.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-media-channel-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-network-media-channel-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-optical-channel-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-optical-operational-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-optical-transport-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-optical-tributary-signal-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-ospf.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-otn-common.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-otn-odu-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-otn-otu-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-otsi-group-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-physical-types.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-pluggable-optics-holder-capability.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-port-capability.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-ppp-interfaces.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-prot-otn-linear-aps.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-routing.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-rstp.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-security.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-swdl.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-syslog.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-telemetry-types.yang C:\data\yang\openroadm-7.1.0\Device\org-openroadm-wavelength-map.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-amplifier.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-clli-network.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-common-network.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-degree.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-external-pluggable.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-link.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-network-topology-types.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-network-topology.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-network-types.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-network.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-otn-network-topology.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-roadm.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-srg.yang C:\data\yang\openroadm-7.1.0\Network\org-openroadm-xponder.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-ber-test.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-common-ber-test.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-common-service-types.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-controller-customization.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-routing-constraints.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-service.yang C:\data\yang\openroadm-7.1.0\Service\org-openroadm-topology.yang --plugindir=. -f xltree --xltree-out oroadm-all-7.1.0.xlsx --xltree-font=Calibri
```


### OpenROADM 13.1.1

If you have [OpenROADM 13.1.1](https://github.com/OpenROADM/OpenROADM_MSA_Public/tree/13.1.1/model) YANG files under `C:\data\yang\openroadm-13.1.1` and dependents under `C:\data\yang\{iana,ietf}`:


#### all

```
python -m pyang -p C:\data\yang\iana;C:\data\yang\ietf C:\data\yang\ietf\ietf-network@2018-02-26.yang C:\data\yang\ietf\ietf-network-topology@2018-02-26.yang C:\data\yang\ietf\ietf-network-state@2018-02-26.yang C:\data\yang\ietf\ietf-network-topology-state@2018-02-26.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-alarm.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-alarm-pm-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-amplifier-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-attributes.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-equipment-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-link-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-node-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-optical-channel-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-phy-codes.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-state-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-equipment-states-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-interfaces.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-layerRate.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-ltp-template.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-manifest-file.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-network-resource.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-otn-common-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-pm-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-pm.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-port-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-probable-cause.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-resource-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-resource.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-service-format.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-switching-pool-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-tca.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-user-mgmt.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-extensions.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-inet-types.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-telemetry-types.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-telemetry.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-database.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-de-operations.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-device-types.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-device.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-dhcp.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ethernet-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-fcc-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-file-transfer.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-fwdl.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-gcc-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-gnmi.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ip.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ipv4-unicast-routing.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ipv6-unicast-routing.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-key-chain.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-lldp.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-maintenance-loopback.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-maintenance-testsignal.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-media-channel-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-network-media-channel-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-channel-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-operational-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-transport-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-tributary-signal-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ospf.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otn-common.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otn-odu-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otn-otu-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otsi-group-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-physical-types.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-pluggable-optics-holder-capability.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-port-capability.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-prot-equipment-aps.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-prot-otn-linear-aps.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-routing.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-rstp.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-security.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-swdl.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-syslog.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-telemetry-types.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-wavelength-map.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-amplifier.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-clli-network.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-common-network.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-degree.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-external-pluggable.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-link.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network-topology-types.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network-topology.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network-types.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-otn-network-topology.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-roadm.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-srg.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-xponder.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-ber-test.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-common-ber-test.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-common-service-types.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-controller-customization.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-operational-mode-catalog.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-routing-constraints.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-service.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-topology.yang --plugindir=. -f xltree --xltree-out oroadm-all-13.1.1.xlsx --xltree-font=Calibri
```


#### Device Model

```
python -m pyang -p C:\data\yang\iana C:\data\yang\openroadm-13.1.1\Device\openconfig-extensions.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-inet-types.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-telemetry-types.yang C:\data\yang\openroadm-13.1.1\Device\openconfig-telemetry.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-database.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-de-operations.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-device-types.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-device.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-dhcp.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ethernet-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-fcc-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-file-transfer.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-fwdl.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-gcc-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-gnmi.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ip.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ipv4-unicast-routing.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ipv6-unicast-routing.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-key-chain.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-lldp.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-maintenance-loopback.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-maintenance-testsignal.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-media-channel-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-network-media-channel-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-channel-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-operational-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-transport-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-optical-tributary-signal-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-ospf.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otn-common.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otn-odu-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otn-otu-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-otsi-group-interfaces.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-physical-types.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-pluggable-optics-holder-capability.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-port-capability.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-prot-equipment-aps.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-prot-otn-linear-aps.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-routing.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-rstp.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-security.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-swdl.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-syslog.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-telemetry-types.yang C:\data\yang\openroadm-13.1.1\Device\org-openroadm-wavelength-map.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-alarm.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-alarm-pm-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-amplifier-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-attributes.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-equipment-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-link-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-node-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-optical-channel-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-phy-codes.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-state-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-common-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-equipment-states-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-interfaces.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-layerRate.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-ltp-template.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-manifest-file.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-network-resource.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-otn-common-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-pm-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-pm.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-port-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-probable-cause.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-resource-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-resource.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-service-format.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-switching-pool-types.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-tca.yang C:\data\yang\openroadm-13.1.1\Common\org-openroadm-user-mgmt.yang --plugindir=. -f xltree --xltree-out oroadm-device-13.1.1.xlsx --xltree-font=Calibri
```


#### Network Model

```
python -m pyang -p C:\data\yang\iana;C:\data\yang\ietf;C:\data\yang\openroadm-13.1.1\Common C:\data\yang\ietf\ietf-network@2018-02-26.yang C:\data\yang\ietf\ietf-network-topology@2018-02-26.yang C:\data\yang\ietf\ietf-network-state@2018-02-26.yang C:\data\yang\ietf\ietf-network-topology-state@2018-02-26.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-amplifier.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-clli-network.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-common-network.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-degree.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-external-pluggable.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-link.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network-topology-types.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network-topology.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network-types.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-network.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-otn-network-topology.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-roadm.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-srg.yang C:\data\yang\openroadm-13.1.1\Network\org-openroadm-xponder.yang --plugindir=. -f xltree --xltree-out oroadm-network-13.1.1.xlsx --xltree-font=Calibri
```


#### Service Model

```
python -m pyang -p C:\data\yang\iana;C:\data\yang\ietf;C:\data\yang\openroadm-13.1.1\Common C:\data\yang\openroadm-13.1.1\Service\org-openroadm-ber-test.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-common-ber-test.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-common-service-types.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-controller-customization.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-operational-mode-catalog.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-routing-constraints.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-service.yang C:\data\yang\openroadm-13.1.1\Service\org-openroadm-topology.yang --plugindir=. -f xltree --xltree-out oroadm-service-13.1.1.xlsx --xltree-font=Calibri
```
