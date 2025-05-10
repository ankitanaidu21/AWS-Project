
Test RDS Management Features

1. RDS Failover Tests
			○ Go to the RDS Console, select Databases, choose the instance, and click Failover.
			○ Confirm the failover when prompted.
			○ Click Refresh until the rdscluster status changes to Failing-over, then verify Reader and Writer roles have swapped.
	
2. Create RDS Snapshot
			• In the RDS Console, select Databases > your instance > Actions > Take snapshot.
			• Name the snapshot (e.g.,appname-snapshot) and click Take Snapshot.
			• Check snapshot status under Snapshots. Wait until status becomes available.
To restore: Select the snapshot > Actions > Restore Snapshot.
			
3. Change RDS Instance Type
				• In RDS Console, select your instance and click Modify.
				• Change the instance class to db.r6g.large, scroll down, and click Continue.
				• Choose Apply Immediately, then click Modify DB Instance.
				• Wait while the instance status changes to Modifying and eventually to Available.
				• RDS automatically fails over to minimize downtime before resizing.
			
RDS can change the size of the instance at any time. However, the size of the database does not support shrink after scaling up.

