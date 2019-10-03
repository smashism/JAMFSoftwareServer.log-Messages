# JAMFSoftwareServer.log Messages
This repo contains a list of messages which can appear in the JAMFSoftwareServer.log, with a note as to what to do with them (if any action is requied).

The messages have an assigned status, as per:

| Status | Description |
|:---:|---|
| :ok: | No issue, maybe an informative message |
| :warning: | A message that can either be ignored, or can be indicative of an issue |
| :no_entry_sign: | A message which indicates an issue which needs attention | 

| Log Message Body | Status | PI | Detail |
|---|:---:|:---:|---|
| `APNs Certificate is expired.` | :no_entry_sign: | | Renew the APNS certificate.|
|`[VppAccountCreator        ] - Failed to register user com.jamfsoftware.vpp.User@6f7dd030[id=xxx,managedAppleId=some@appleid] to VPP invitation com.jamfsoftware.vpp.invitation.VppInvitation@ef3b577[id=0,vppAdminAccountID=0,vppAdminAccount=<null>,message=<null>,method=AUTO_REGISTER,name=<null>,loginRequired=false,autoRegisterManagedUsersToVPP=true,subject=<null>,sendFrom=<null>,sendFromDisplay=<null>]
com.jamfsoftware.vpp.invitation.RegisterUserException: Apple ID passed cannot be used at this time because it's a VPP manager and the iTunes Store account not yet created and such creation requires user to agree to Terms.
    at com.jamfsoftware.vpp.comm.VppCommService.registerNewUser(VppCommService.java:318)` | :warning: | |The user needs to login to ABM/ASM to accept the Terms & Conditions for their account |
|`Error parsing iTunes ID: String index out of range`| :warning: | PI-000867 | This is due to self hosted iBooks being added to Jamf Pro. To stop getting these messages: Disable Populate Purchased VPP Content from Settings > Global > VPP > Content, for each token in use.|
