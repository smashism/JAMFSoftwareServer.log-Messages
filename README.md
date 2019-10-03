# JAMFSoftwareServer.log Messages
This repo contains a list of messages which can appear in the JAMFSoftwareServer.log, with a note as to what to do with them

The messages have an assigned status, as per:

| Status | Description |
|---|---|
| :ok: | No issue, maybe an informative message |
| :warning: | A message that can either be ignored, or indicative pf an issue |
| :no_entry_sign: | A message which indicates an issue which needs attention | 

| Log Message | Status | PI | Detail |
|---|---|---|
|`Error parsing iTunes ID: String index out of range`| :ok: | PI-000867 | This is due to self hosted iBooks being added to Jamf Pro. So stop getting these messages: Disable Populate Purchased VPP Content from Settings > Global > VPP > Content, for each token in use. |
