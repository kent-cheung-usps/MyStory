# Release v1.9.4 - Manual Test Log
## User Story
[B-907187: Manage Location Enhancement](https://versionone.usps.gov/v1/story.mvc/Summary?oidToken=Story%3A8592052)<br>
[B-915075: EasyPost - Add MID functionality](https://versionone.usps.gov/v1/story.mvc/Summary?oidToken=Story%3A8654572)
Scenario | Current MIDs | Current EPA | ship enrollment API response | Expected actions on Manage Locations
-- | -- | -- | -- | -- 
User starts API enrollment and clicks on My account | 2 outbound + 1 return | no | no | Enable Enroll SHIP/APIs button on My account and Manage Location and continue the wf=api or wf=ship where they left off
User enrolls in SHIP and wants to add an outbound MID | 2 outbound + 1 return | yes | outbound-yes, returns-yes | Enable the Add Mailer ID button on My account and Manage Location and navigate to Request new MID screen - add mid via programreg(no need to call SHIP as its automatically enrolled)
User enrolls in SHIP and wants to add an returns MID | 2 outbound + 1 return | yes | outbound-yes, returns-yes | Enable the Add Mailer ID button on My account and Manage Location and navigate to Request new MID screen - add 6900 token mid via MID API(call SHIP to enroll in returns)
User has enrolled in SHIP outbound and wants to add an EXISTING returns MID(the mid is not enrolled in ship) | 5 outbound + 1 return | yes | outbound-yes, returns-no | On Manage Location screen, enable "Enroll" button on returns MID row to enroll into SHIP returns,  and navigate to Add MID screen, select EPA and call SHIP to enroll in returns
User has enrolled in SHIP returns ONLY and wants to enroll in outbound | 1 return | yes | outbound-no, returns-yes | On My Account Page, enable Enroll SHIP/APIs Outbound button. On Manage location screen, enable "Enroll SHIP/APIs Outbound" button

-------------
## Test Cases From Radha
2025-01-10 - https://github.usps.gov/vxqqk0/MyStory/blob/main/Rel_v1.9.4_Item/EIR-9075-My%20Locations.xlsb
## Defects
[D-98396 : Failed to enroll Mailer ID in Happy Path](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8747273)<br>
[D-98391 : UI Enhancement - Replace "Select Company" Text to more meaningful instruction message](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8746951)<br>
[D-98287 : Minor Cosmetic Alignment Issue When Resizing the Browser](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8742698)<br>
[D-98290 : Requested host "cop-sit.usps.comcop-navigator" could not be resolved by DNS](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8742775)<br>
[D-98411 : Minor Cosmetic Issues in Request New Mailer ID Page](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8747522)<br>
[D-98410 : Under Construction Popup](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8747518)<br>
[D-98474 : "Eroll" button should not display for RETURNS MID](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8751029)<br>
[D-98477 : Fail to enroll a user with RETURN MID only to SHIP](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8751220)<br>
[D-98602 : 500 Error when Continue & Add New Location](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8759656) - Happen again in build 38<br>
[D-98774 : Fail to enroll a user with RETURN MID only to SHIP](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8771864)<br>
[D-98786 : Error when navigate to EPS account from "Active Payment Acct" Link](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8773640)<br>
[D-98793 : Failed to add business location for "user by crid"](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8774346)<br>
[D-98957 : Failed to add location for this test case](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8781421)<br>
[D-98967 : Quick Action "Request New Mailer Id" go to incorrect page.](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8781679)<br>
[D-99030 : Fail to add International address](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8784146)

-----------------
## Notes:
1. Beside manual test, I am also pinpoint the issue from code level. Example: [D-98793 : Failed to add business location for "user by crid"](https://versionone.usps.gov/v1/defect.mvc/Summary?oidToken=Defect%3A8774346)<br>
The stack trace indicated an issue with `PPCService.requestService`. I traced the code and pinpointed the potential problem with `epsAccount` and notified the code owner. The defect was successfully resolved in less than 20 minutes.<br>
![image](https://github.usps.gov/vxqqk0/MyStory/assets/3011/2d34d3a3-41ae-4b32-9068-b64c6d98f343)
