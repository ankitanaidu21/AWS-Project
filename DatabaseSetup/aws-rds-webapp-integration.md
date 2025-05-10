Connect RDS with Web App Server 

1. Verify RDS Endpoint
	• Confirm RDS Endpoint URL before using it on EC2 web server.

Store RDS Credentials in AWS Secrets Manager
	1. Go to AWS Secrets Manager → click Store a new secret.
	2. Select Credentials for Amazon RDS database.
	3. Enter DB username, password, and select your database → click Next.
	4. Name the secret → keep default settings → click Next → then Store.
	5. Click your secret → go to Secret value tab → click Retrieve.
	6. Click Edit, make sure dbname and immersionday keys exist → add/save if missing.

Allow the web server to access the secret
	1. Go to IAM Console → Policies → click Create Policy.
	2. Choose Secrets Manager as the service.
	3. Under Read access, enable GetSecretValue.
	4. Under Resources, select All resources → click Next.
	For the lab, we're allowing EC2 to access all secrets. With a real workload, you should consider allowing access to specific secrets.
	5. Name it ReadSecrets → click Create policy.
	6. Go to Roles → search SSMInstanceProfile → click it.
	7. Click Attach policies → select ReadSecrets → attach it.
	8. Under Permissions policies, verify that AmazonSSMManagedInstanceCore and ReadSecrets are both listed.
