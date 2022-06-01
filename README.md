# AzBluMon
Automate the deployment of Azure Monitor Diagnostic Settings for the integration with Blumira SIEM.

## Pre-requisites
This script assumes the following:
1. You have an Azure subscription
2. Most or all of the resources you wish to monitor are contained inside of said subscription
3. You know or can set up an Azure CLI cloud shell or have a local machine that is using `BASH` and not `ZSH`

## Setting Up Azure Cloud Shell
Before running the script it is recommended that you set up or configure Azure Cloud Shell. You can use the defaults without issue, but when prompted for **Location** within the script, please use the region ID where you have most of your other resources in your subscription. Azure by default may place the storage account in a separate region. When starting make sure to run Azure Cloud Shell in `BASH` and not Powershell. Use this video below for help in getting started with Azure Cloud Shell (Skip to 0:58s from Cloud Guru).
[![IMAGE ALT TEXT HERE](http://img.youtube.com/vi/2pQr-w8ZiYU/0.jpg)](http://www.youtube.com/watch?v=2pQr-w8ZiYU)

## Cloning the Repo and Running the Script
To get started copy and paste the following into your Azure Cloud Shell terminal window. The following commands clone the repo, place you in the directory, set the script to have the proper permissions to run, and finally run the script.

```Bash
cd ./AzBluMon
chmod +x ./AzBluMon.azcli
./AzBluMon.azcli
```
Once the script has started to run, you will be presented with the first prompt for Subscription ID. This can be found by navigating to https://portal.azure.com/#view/Microsoft_Azure_Billing/SubscriptionsBlade from this screen you'll be able to copy the Subscription ID and paste it into the terminal. Don't be afraid about changing screens the terminal window will not disappear.

After typing in or copying and pasting the Subscription ID, the script will ask you for a location or region ID. These are single simple strings that designate where the Event Hub and Namespace will be deployed. I'd recommend setting this to whereever the bulk of your resources are located. A list can be found of these but for example some are `eastus`,`eastus2`,`centralus`,`westus`, and many more. The list for these region codes can be found at this link (the name column are the compatible codes) https://azuretracks.com/2021/04/current-azure-region-names-reference/.

The next input required is a unique name for the Event Hub Namespace. This must be unique across all Azure instances, if the creation of this resource fails the rest of the script will continue to error out and you'll need to restart the script by running the code block above once more. Before restarting the script run it is required to delete the newly created Blumira resource group. To do so run `az group delete --name blu-eventhub-rg`, when prompted type in `Y` and click `Enter`.

## Closing Out
This script is still being worked on, in the future I hope to have a subscription selector further reducing the the need for manual input and I need to account for more resources that do not support the `Log` category in Azure Monitor Diagnostic Settings.
