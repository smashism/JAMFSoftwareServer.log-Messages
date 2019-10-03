# JAMFSoftwareServer.log Messages
This repo contains a list of messages which can appear in the JAMFSoftwareServer.log, with a note as to what to do with them (if any action is requied).

The messages have an assigned status, as per:

| Status | Description |
|:---:|---|
| :ok: | No issue, maybe an informative message |
| :warning: | A message that can either be ignored, or can be indicative of an issue |
| :no_entry_sign: | A message which indicates an issue which needs attention | 

| Log Message Snippets | Status | PI | Detail |
|---|:---:|:---:|---|
| `APNs Certificate is expired.` | :no_entry_sign: | | Renew the APNS certificate.|
| `[VppAccountCreator        ] - Failed to register user com.jamfsoftware.vpp.User@6f7dd030[id=xxx,managedAppleId=some@appleid] to VPP invitation` | :warning: | | The some@appleid needs to login to ABM/ASM & accept the Terms & Conditions for their account |
|`Error parsing iTunes ID: String index out of range`| :warning: | PI-000867 | This is due to self hosted iBooks being added to Jamf Pro. To stop getting these messages: Disable Populate Purchased VPP Content from Settings > Global > VPP > Content, for each token in use.|
