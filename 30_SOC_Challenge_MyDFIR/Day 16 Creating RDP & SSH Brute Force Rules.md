# Day 16: Creating RDP & SSH Brute Force Rules
## 1. Introduction

**Goal**: Review authentication logs from the Windows server and create a Brute Force alert.

## 2. Query Logs for RDP Brute Force Activity

**Steps**:

1. Log into Elasticsearch and click on the hamburger icon > **Discover**.
2. Set the time frame to "Today".
3. Filter for the Windows server by clicking on the agent name (e.g., `MyDFIR-WIN-wahab`).

## 3. Identify Key Fields

**Fields to Track**:

4. **Failed Attempts**: Look for failed authentication attempts (Event ID 4625)
5. **User**: Identify the user attempting to log in.
6. **Source IP**: Determine the source IP of the authentication attempts.

## 4. Filter for Failed Attempts

**Steps**:

7. Search for Event ID 4625 in the logs.
8. Confirm the field name is `event.code`.
9. Add `source.ip` and `user.name` fields to the table.
10. Verify the data by expanding the first event and checking the message.

## 5. Save the Query

**Steps**:

Save the query as `RDP failed activity`.

## 6. Create Alert

**Steps**:

11. Click on the **Alerts** tab and select **Create Search Threshold Rule**.
12. Name the alert (e.g., `Failed RDP alert`).
13. Set the threshold (e.g., greater than 5 failed attempts within 5 minutes).
14. Test the query to ensure it matches documents.
15. Save the rule.

## 7. Create Detailed Detection Rule for RDP

**Steps**:

16. Click on **Rules** and select **Create New Rule**.
17. Choose **Threshold** as the rule type.
18. Use the custom query from the saved search

```
event.code:4625 AND agent.name:"Challenge-WIN-Haji" and user.name:"Administrator" 
```

19. In the `Group by` add `user.name` and `source.ip` fields.
20. For the required field also add these two `user.name` and `source.ip`.
21. Name the rule (e.g., `MyDFIR-RDP-Brute-Force-Attempt-Wahab`).
22. Set the severity to medium and configure advanced settings if needed.
23. Schedule the rule to run every 5 minutes.
24. Create and enable the rule.

## 8. Create Detailed Detection Rule for RDP

**Steps**:

25. Click on **Rules** and select **Create New Rule**.
26. Choose **Threshold** as the rule type.
27. Use the custom query from the saved search

```
system.auth.ssh.event : * and agent.name:"MyDFIR-Linux-Wahab" and system.auth.ssh.event : "Failed" AND user.name:"root" 
```

28. In the `Group by` add `user.name` and `source.ip` fields.
29. For the required field also add these two `user.name` and `source.ip`.
30. Name the rule (e.g., `MyDFIR-SSH-Brute-Force-Attempt-Steve`).
31. Set the severity to medium and configure advanced settings if needed.
32. Schedule the rule to run every 5 minutes.
33. Create and enable the rule.

## 8. Test the Rule

**Steps**:

34. Perform a brute force attack to generate alerts.
35. Check the alerts for detailed information such as username and source IP.

[Day 17 Creating a Dashboard for RDP Activity](Day%2017%20Creating%20a%20Dashboard%20for%20RDP%20Activity.md)