# JAMFSoftwareServer.log Messages
This repo contains a list of messages which can appear in the JAMFSoftwareServer.log, with a note as to what to do with them (if any action is requied).

The messages have an assigned status, as per:

| Status | Description |
|:---:|---|
| :ok: | No issue, maybe an informative message |
| :warning: | A message that can either be ignored, or can be indicative of an issue |
| :no_entry_sign: | A message which indicates an issue which needs attention | 

| Log Message Snippets | Status | PI | Detail |
|:---|:---:|:---:|---|
|`APNs Certificate is expired.`|:no_entry_sign:||Renew the APNS certificate.|
|`[ERROR] [duledPool-8] [ntInstanceSyncCommService] - com.jamfsoftware.jss.objects.streamlinedenrollment.service.DeviceEnrollmentProgramException: The DEP service reported an error.`|:no_entry_sign:||Download a new token from ABM/ASM & upload into the JPS.|
|`[ntInstanceSyncCommService] - com.jamfsoftware.jss.objects.streamlinedenrollment.service.DeviceEnrollmentProgramException: An error occurred during oauth token refresh`|:no_entry_sign:||Either renew DEP token or login to ABM/ASM to accept the new terms & conditions. https://datajar.zendesk.com/agent/tickets/27232|
|`[llmentProgramDeviceHelper] - 403 The organization has not accepted latest Terms and Conditions of the program`|:no_entry_sign:||Login to ABM/ASM to accept the new terms & conditions. https://datajar.zendesk.com/agent/tickets/27232|
|`[llmentProgramDeviceHelper] - 403: token_expiredForbidden`|:warning:||Remove or renew the offending token.|
|`[llmentProgramDeviceHelper] - 403: token_rejectedForbidden`|:warning:||Remove or renew the offending token.|
|`[llmentProgramDeviceHelper] - 400 response from Device Enrollment Program indicating one of the following:`||:warning:||DEP token has been downloaded from ABM/ASM but not uploaded to JPS. Remove or renew the offending token.|
|`[VppAccountCreator        ] - Failed to register user com.jamfsoftware.vpp.User@6f7dd030[id=xxx,managedAppleId=some@appleid] to VPP invitation`|:warning:||The some@appleid needs to login to ABM/ASM & accept the Terms & Conditions for their account |
|`[llmentProgramDeviceHelper] - 403: SERVER_INACTIVE` |:warning:|There is a DEP PreStage with a token in use which no longer has a location in ABM/ASM. Remove the offending PreStage|
|`[llmentProfileSynchronizer] - com.jamfsoftware.jss.objects.streamlinedenrollment.service.DeviceEnrollmentProgramException: The DEP service reported that invalid options were submitted.`|:warning:||A ABM DEP token has been assigned to a DEP PreStage for Shared iPad, correct the DEP token in use by the PreStage or remove the Shared iPad settings.|
|`Error parsing iTunes ID: String index out of range`|:warning:|PI-000867|This is due to self hosted iBooks being added to Jamf Pro. To stop getting these messages: Disable Populate Purchased VPP Content from Settings > Global > VPP > Content, for each token in use.|
