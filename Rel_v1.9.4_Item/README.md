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
