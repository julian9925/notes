
## Redfish spec 驗證參考

OpenBMC UI 中，有使用到的 api call

- AuthenticanStore
	- 
	- logout
	- checkPasswordChangeRequired


- GlobalStore
  - getBmcTime
	- getSystemInfo


- AssemblyStore
  - getAssemblyInfo
	- updateIdentifyLedValue


- BmcStore
  - getBmcInfo
	- updateIdentifyLedValue


- ChassisStore
  - getChassisInfo
	- updateIdentifyLedValue


- FanStore
  - getFanInfo


- MemoryStore
  - getDimms
	- updateIdentifyLedValue


- PowerSupplyStore
  - getChassisCollection
	- getAllPowerSupplies
	- getChassisPower


- ProcessorStore
  - getProcessorsInfo
	- updateIdentifyLedValue


- SensorsStore
  - getAllSensors
	- getChassisCollection
	- getSensors
	- getThermalSensors
	- getPowerSensors


- ServerLedStore
  - getIndicatorLedActiveState
	- saveIndicatorLedActiveState


- SystemStore
  - getSystem
	- changeIdentifyLedState


- DumpsStore
  - getBmcDumpEntries
	- getSystemDumpEntries
	- getAllDumps
	- createBmcDump
	- createSystemDump
	- deleteDumps
	- deleteAllDumps


- EventLogStore
  - getEventLogData
	- deleteAllEventLogs
	- deleteEventLogs
	- resolveEventLogs
	- unresolveEventLogs
	- updateEventLogStatus


- PostCodeLogsStore
  - getPostCodesLogData


- BootSettingsStore
  - getBootSettings
	- saveBootSettings
	- getTpmPolicy
	- saveTpmPolicy
	- saveSettings


- ControlStore
  - getLastPowerOperationTime
	- getLastBmcRebootTime
	- rebootBmc
	- serverPowerChange


- FactoryResetStore
  - resetToDefaults
	- resetBios


- FirmwareStore
  - getActiveBmcFirmware
	- getActiveHostFirmware
	- getFirmwareInventory
	- getUpdateServiceSettings
	- setApplyTimeImmediate
	- uploadFirmware
	- uploadFirmwareTFTP
	- switchBmcFirmwareAndReboot


- KeyClearStore
	- clearEncryptionKeys


- VirtualMediaStore
	- getData
	- mountImage
	- unmountImage


- PowerControlStore
	- getChassisCollection
	- getPowerControl
	- setPowerControl


- CertificatesStore
  - getCertificates
	- addNewCertificate
	- replaceCertificate
	- deleteCertificate
	- generateCsr


- LdapStore
  - getAccountSettings
	- saveLdapSettings
	- saveActiveDirectorySettings
	- addNewRoleGroup
	- saveRoleGroup
	- deleteRoleGroup


- PoliciesStore
  - getNetworkProtocolStatus
	- getBiosStatus
	- saveIpmiProtocolState
	- saveSshProtocolState
	- saveRtadState
	- saveVtpmState


- SessionsStore
	- getSessionsData
	- disconnectSessions


- UserManagementStore
  - getUsers
	- getAccountSettings
	- getAccountRoles
	- createUser
	- updateUser
	- deleteUser
	- deleteUsers
	- enableUsers
	- disableUsers
	- saveAccountSettings


- DateTimeStore
	- getNtpData
	- updateDateTime


- NetworkStore
  - getEthernetData
	- saveDomainNameState
	- saveDnsState
	- saveNtpState
	- saveIpv4Address
	- editIpv4Address
	- saveSettings
	- saveDnsAddress
	- editDnsAddress


- PowerPolicyStore
  - getPowerRestorePolicies
	- getPowerRestoreCurrentPolicy
	- setPowerRestorePolicy