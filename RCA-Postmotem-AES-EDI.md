# RCA/Postmortem for AES-EDI | Jira issue (AESEDI-53447)
## Date
2019-12-19

##V Authors
*Tufayl Ahmed*
*Ops Team*

## Status
Complete, resolved

## Summary
Customer data not sent for AES-EDI. Upon investigation it was found that the data was sent but did not get processed due to an issue with the AES-EDI service issue.

## Impact
About 486,000 records were affected, AES-EDI monitoring service was impacted as well.

## Root Causes
Issue with the AES CIS service (Jira Issue No: AESCIS-38263)

## Trigger
Customer data records not processed in bulk.

## Resolution
Refresh/Reload of the AES CIS monitoring service allowed us to spot the missed records that were not discovered automatically. Following this the data file was resent leading to the resolution.

## Detection
A ticket was created by the customer, which lead to the detection of the issue. JIRA Issue: (AESEDI-53447)

## Action Items
| Action Item | Type | Owner | Bug |
| ----------- | ---- | ----- | --- |
|Investigate if bulk record import processing caused any spike in the utilization| prevent| Tufayl Ahmed| **TODO** |
|New policy creation to detect the missing records during processing|	|prevent|	|Tufayl Ahmed|	|**DONE**|
|Investigate the problem with the AESCIS service that could lead to early detection of the issue|	|prevent|	|Tufayl Ahmed|**TODO**|
##Learned Lessons
Issue could be detected easily if the monitoring service had not broken at the same time of data processing issue. As a contingency, an extra monitoring plugin could resolve the issue. Also, if the utilization of services is impacted due to bulk record update. More resources could be added.

##Timeline
2019-12-19 
| Time  | Description |
| ----- | ----------- |
|11:56|	|Missing files discovered|
|13:00|	|Records were processed|