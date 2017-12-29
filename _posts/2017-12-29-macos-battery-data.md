---
title: Find out battery health by inspecting  macOS battery data
author: Shu
layout: post
categories:
  - Computer
tags:
  - apple
  - macos
  - battery
---

In light of the controversy of iPhone's battery and performance, Apple says
it's rolling out an iOS update that

> with new features that give users more visibility into the health of their iPhone’s battery

It turns out that the information is readily available on macOS as pointed out
by [Jonathan
Levin](https://twitter.com/Morpheus______/status/946762733873258496).

Here is the command to show the battery data:

    $ ioreg -b -w 0 -f -r -c AppleSmartBattery
    +-o AppleSmartBattery  <class AppleSmartBattery, id 0x100000260, registered, matched, active, busy 0 (0 ms), retain 6>
        {
          "ExternalConnected" = No
          "TimeRemaining" = 271
          "InstantTimeToEmpty" = 243
          "ExternalChargeCapable" = No
          "FullPathUpdated" = 1514570836
          "CellVoltage" = (3994,4003,3978,0)
          "Voltage" = 11974
          "BatteryInvalidWakeSeconds" = 30
          "AdapterInfo" = 0
          "MaxCapacity" = 5889
          "DesignCycleCount70" = 65535
          "PermanentFailureStatus" = 0
          "Manufacturer" = "SMP"
          "Location" = 0
          "CurrentCapacity" = 4761
          "LegacyBatteryInfo" = {"Amperage"=18446744073709550563,"Flags"=4,"Capacity"=5889,"Current"=4761,"Voltage"=11974,"Cycle Count"=155}
          "FirmwareSerialNumber" = 1
          "BatteryInstalled" = Yes
          "PackReserve" = 200
          "CycleCount" = 155
          "DesignCapacity" = 6559
          "OperationStatus" = 58435
          "ManufactureDate" = 17988
          "AvgTimeToFull" = 65535
          "BatterySerialNumber" = "REDACTED"
          "BootPathUpdated" = 1513018674
          "PostDischargeWaitSeconds" = 120
          "Temperature" = 2991
          "UserVisiblePathUpdated" = 1514571196
          "InstantAmperage" = 18446744073709550524
          "ManufacturerData" = REDACTED
          "FullyCharged" = No
          "MaxErr" = 1
          "DeviceName" = "bq20z451"
          "IOGeneralInterest" = "IOCommand is not serializable"
          "Amperage" = 18446744073709550563
          "IsCharging" = No
          "DesignCycleCount9C" = 1000
          "PostChargeWaitSeconds" = 120
          "AvgTimeToEmpty" = 271
        }

The interesting fields are:

      "DesignCapacity" = 6559
      "MaxCapacity" = 5889
      "CycleCount" = 155

`MaxCapacity` indicates the capacity that the battery can hold currently,
comparing to the `DesignCapacity` when the battery is new. `CycleCount` shows
the number of cycles the battery has been charged and drained. The above data
shows my battery now has about 10% degradation of it's capability to hold
charge after nearly 3 years of use or 155 cycles.
