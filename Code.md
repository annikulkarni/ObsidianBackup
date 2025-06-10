#define IFE_MAX_VALUE_KM_L_POWERTYPE_EV                   ((tHmi_OslU8)20) //Macro 
#define IOD_MPG_US                                            0U  
#define IOD_MPG_UK                                            1U 
#define IOD_L_100KM                                           2U
#define IOD_KM_L                                              3U
#define IOD_MPG_US_Hybrid                                     4U 
#define IOD_MPG_UK_Hybrid                                     5U 
#define IOD_L_100KM_Hybrid                                    6U 
#define IOD_KM_L_Hybrid                                       7U 



#define IOD_MAX_AFE_DISPLAY_VALUE      (tHmi_OslU16)9999
#define IOD_MAX_MINUTES_DISPLAY_VALUE  (tHmi_OslU16)9999

<mark class="hltr-boom-bam">#define IOD_MAX_DRIVE_CYCLE_AFE_DISPLAY_VALUE (tHmi_OslU16)999</mark>

*
******************************************************************************
*/
static void sendDriveCycleAvgFuel(const tHmi_OslU16 u16AvgFuelValue, const tHmi_OslU8 u8PowerType, const tHmi_OslU8 afeUnit);

/**
******************************************************************************
*
*  @brief Execute send trap functions for all data releated to the distance in drive cycle.


static void sendDriveCycleAvgFuel(const tHmi_OslU16 u16AvgFuelValue, const tHmi_OslU8 u8PowerType, const tHmi_OslU8 afeUnit)
{
    static tHmi_OslChar afeHmiVal[IOD_TRIP_AVG_FUEL_MAX_LEN] = AFE_HMI_DEFAULT_VALUE;
    tHmi_OslU16 fuelValue = u16AvgFuelValue;
    if (u16AvgFuelValue > IOD_MAX_DRIVE_CYCLE_AFE_DISPLAY_VALUE)
    {
        fuelValue = IOD_MAX_DRIVE_CYCLE_AFE_DISPLAY_VALUE;
    }
    switch(afeUnit)
    {
        case IOD_MPG_US:
        case IOD_MPG_UK:
        case IOD_KM_L:
        case IOD_MPG_US_Hybrid:
        case IOD_MPG_UK_Hybrid:
        case IOD_KM_L_Hybrid:

            (void)HMI_OSL_SNPRINTF(afeHmiVal, sizeof(afeHmiVal), "%.1f", (tHmi_OslFloat)fuelValue / TPMS_RESOLUTION_FACTOR);
        break;
        case IOD_L_100KM:
        case IOD_L_100KM_Hybrid:

            (void)HMI_OSL_SNPRINTF(afeHmiVal, sizeof(afeHmiVal), "%d",(int)((tHmi_OslFloat)fuelValue / TPMS_RESOLUTION_FACTOR));
        break;
        default:
         
            (void)HMI_OSL_SNPRINTF(afeHmiVal, sizeof(afeHmiVal), "%.1f", (tHmi_OslFloat)fuelValue / TPMS_RESOLUTION_FACTOR);
         break;
    }
    if (hal_IOD_SendTrap_DATUM_DRIVE_CYCLE_AVG_FUEL_CONSUMPTION(HMI_INSTANCE_BROADCAST, afeHmiVal ))
    {
        HMI_OSL_LOG_ERROR("Send TRAP failed for Datum : Drive cycle avg fuel");
    }
}

  sendTripDistance(hal_IOD_SendTrap_DATUM_TRIPB_EV_DIST_TRAVELLED, &psIodData->sTripB.sdist, true);
        
        sendDriveCycleAvgFuel(psIodData->sDriveCycle.u16FuelValue, psIodData->u8PowerType, psIodData->u8fuelUnit);
    
        sendDriveCycleDistance(psIodData->sDriveCycle.u32distanceValue);