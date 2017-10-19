# Overview

This is all of the parts for deploying monitoring for tripplite SNMPWEBCARD devices.  Currently, this is only complete for a PDUMH20ATNET, but can be easily expanded/updated to include items for many (all?) PDU and UPS models from Tripp Lite.

This is tested against firmware: 12.06.0069.

## Install Steps

### Copy MIBs to Zabbix Server

If your zabbix server installation has SNMP support, there's usually a location in the filesystem for MIBs that are part of the SNMP installation.  In the repo it's suggested as: share/snmp/mibs.  In a SmartOS zone, this ends up being: /opt/local/share/snmp/mibs.  Other platforms/distros will vary.  If you want a platform/distro location added here, send me a PR :)

Also of note, this may require a restart of the zabbix server daemon.

### Install Value Maps

Upload the following value maps to your Administration --> General --> Value mapping section of your Zabbix UI:

ups_output_source_valuemaps.xml
ups_input_voltage_type_valuemaps.xml
ups_outlet_state_valuemaps.xml
ups_outlet_type_valuemaps.xml
ups_outlet_ramp_action_valuemaps.xml
ups_outlet_ramp_data_type_valuemaps.xml
ups_outlet_shed_action_valuemaps.xml
ups_outlet_shed_data_type.xml

### Install Template

Upload the template via Zabbix UI

## Notes

Everything is in the "UPS" application in the template.  This is mostly because Tripp Lite is particularly opinionated in the supplied MIBs. Basically, all of the PDU OIDs are encompassed in UPS sections, in other words, there are no PDU specific sections.

## TODO

1. Add a UPS-MIB::Alarms discovery
2. Get an updated list of Outlet Types (PDU is returning 2, which isn't in the MIB)
3. Add outlet group discovery
4. Update for a UPS model
5. Add EnviroSense