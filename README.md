# JAMFSoftwareServer.log Messages
This repo contains a list of messages which can appear in the JAMFSoftwareServer.log, with a note as to what to do with them (if any action is requied).

The messages have an assigned status, as per:

| Status | Description |
|:---:|---|
|:no_entry_sign:|Severe event which needs immediate attention.|
|:warning:|An event that needs attention, but is not service affecting.|
|:ok:| Non-issue, an informative event.|


| Log Message Snippets | Status | PI | Detail |
|:---|:---:|:---:|---|
|`Fatal error logged during server initialization`|:no_entry_sign:||JPS failed to startup, further investigation needed as to why.|
|`APNs Certificate is expired.`|:no_entry_sign:||Renew the APNS certificate.|
|`[llmentProgramDeviceHelper] - 403 The organization has not accepted latest Terms and Conditions of the program`|:warning:||Login to ABM/ASM to accept the new terms & conditions. https://datajar.zendesk.com/agent/tickets/27232|
|`[ERROR] [duledPool-8] [ntInstanceSyncCommService] - com.jamfsoftware.jss.objects.streamlinedenrollment.service.DeviceEnrollmentProgramException: The DEP service reported an error.`|:warning:||Download a new token from ABM/ASM & upload into the JPS.|
|`[ntInstanceSyncCommService] - com.jamfsoftware.jss.objects.streamlinedenrollment.service.DeviceEnrollmentProgramException: An error occurred during oauth token refresh`|:warning:||Either renew DEP token or login to ABM/ASM to accept the new terms & conditions. https://datajar.zendesk.com/agent/tickets/27232|
|`[llmentProgramDeviceHelper] - 403: token_expiredForbidden`|:warning:||Remove or renew the offending token.|
|`[llmentProgramDeviceHelper] - 403: token_rejectedForbidden`|:warning:||Remove or renew the offending token.|
|`[llmentProgramDeviceHelper] - 400 response from Device Enrollment Program indicating one of the following:`|:warning:||DEP token has been downloaded from ABM/ASM but not uploaded to JPS. Remove or renew the offending token.|
|`[VppAccountCreator        ] - Failed to register user com.jamfsoftware.vpp.User@6f7dd030[id=xxx,managedAppleId=some@appleid] to VPP invitation`|:warning:||The some@appleid needs to login to ABM/ASM & accept the Terms & Conditions for their account |
|`[llmentProgramDeviceHelper] - 403: SERVER_INACTIVE` |:warning:||There is a DEP PreStage with a token in use which no longer has a location in ABM/ASM. Remove the offending PreStage|
|`[llmentProfileSynchronizer] - com.jamfsoftware.jss.objects.streamlinedenrollment.service.DeviceEnrollmentProgramException: The DEP service reported that invalid options were submitted.`|:warning:||An ABM DEP token has been assigned to a DEP PreStage for Shared iPad, correct the DEP token in use by the PreStage or remove the Shared iPad settings.|
|`Error parsing iTunes ID: String index out of range`|:warning:|PI-000867|This is due to self hosted iBooks being added to Jamf Pro. To stop getting these messages: Disable Populate Purchased VPP Content from Settings > Global > VPP > Content, for each token in use.|
|`[Root exception is javax.net.ssl.SSLHandshakeException: PKIX path validation failed: java.security.cert.CertPathValidatorException: validity check failed]`|:warning:||LDAPS certificate validity check failed. Check certificate presented to JPS|
|`javax.naming.CommunicationException: <ldap.server:port> [Root exception is java.net.SocketTimeoutException: connect timed out]`|:warning:||Connection to LDAP <ldap.server:port> timed out. Up LDAP time out time & investigate if persists.|
|`javax.naming.CommunicationException: <ldap.server:port> [Root exception is java.net.SocketTimeoutException: Read timed out]`|:warning:||Connection to LDAP <ldap.server:port> timed out. Up LDAP time out time & investigate if persists.|
|`[Root exception is java.net.SocketException: Connection reset]`|:warning:||Connectivity issue with to LDAP(s), investigation neded.|
|`[Root exception is javax.net.ssl.SSLHandshakeException: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target]`|:warning:||LDAP SSL certificate not trusted by JPS|
|`javax.naming.CommunicationException: <ldap server fqdn>:<ldap server port> [Root exception is javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: javax.net.ssl.SSLException: hostname in certificate didn't match: <ldap server fqdn> != <ldap server fqdn> OR <ldap server fqdn>]`|:warning:||Check FQDN for LDAPS does not match FQDN entries within cert.|


