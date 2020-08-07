**Relational Database Service**

Search for RDS in AWS Console and create database, we can also restore
from S3 if we have one saved.

<img src="./media/image1.png" style="width:6.5in;height:1.53611in" />

We create MySQL database:

<img src="./media/image2.png" style="width:6.5in;height:5.53125in" />

Give a name to this instance and provide a password:

<img src="./media/image3.png" style="width:6.5in;height:6.07292in" />

Choose a suitable CPU and RAM configuration depending on the database
use
case:<img src="./media/image4.png" style="width:6.5in;height:2.16667in" />

Configure the storage – depends on database, we can also enable storage
autoscaling depending on use case.

<img src="./media/image5.png" style="width:6.5in;height:4.74792in" />

Creates a backup instance to ensure availability and durability.

<img src="./media/image6.png" style="width:6.5in;height:2.08889in" />

Configure the connectivity for this instance:

<img src="./media/image7.png" style="width:5.34127in;height:4.45238in" />

<img src="./media/image8.png" style="width:6.31721in;height:2.60856in" />

Port 3306 is default MySQL port.

Give database a name and we can also enable automatic backups from here:

<img src="./media/image9.png" style="width:6.5in;height:5.02014in" />

We cannot create the database yet, it is a requirement of AWS RDS to
have subnets at at least 2 availability zones.

<img src="./media/image10.png" style="width:6.5in;height:2.32153in" />

**Create another subnet at a different AZ:**

We have one in us-east-1a, we are going to create another one in 1b.

<img src="./media/image11.png" style="width:6.5in;height:2.82014in" />

Now, we have two subnets at different AZ’s :

<img src="./media/image12.png" style="width:6.5in;height:2.40486in" />

Refresh, the connectivity tab on ‘Create database’ page.

We have another error to fix in the VPC:

<img src="./media/image13.png" style="width:6.5in;height:0.875in" />

Go to VPC and check if both are enabled:

<img src="./media/image14.png" style="width:5.66716in;height:3.21695in" />

<img src="./media/image15.png" style="width:6.31338in;height:2.96916in" />

Refresh, the connectivity tab on ‘Create database’ page and create
database.

Now we have the database instance up and running

<img src="./media/image16.png" style="width:6.5in;height:1.20139in" />

We can connect to this database using MySQL Workbench

<img src="./media/image17.png" style="width:6.5in;height:3.08542in" />

<img src="./media/image18.png" style="width:6.5in;height:3.07639in" />

We can use the endpoint instead of hostname to connect to our instance.
Use the username and password created earlier.

<img src="./media/image19.png" style="width:6.5in;height:2.89306in" />

Click ok and wait for it to launch.

If this error pops up, it is ‘connection timed out’, we can fix this in
the security groups.

<img src="./media/image20.png" style="width:3.01191in;height:2.75722in" />

Looking at our security group, we can see there’s no port 3306 enabled,
this is default port for MySQL. We are going to enable it.

<img src="./media/image21.png" style="width:6.49729in;height:2.01191in" />

Click on edit inbound rules, Add rule.

<img src="./media/image22.png" style="width:6.5in;height:1.76389in" />

Save rules and try to connect again in Work bench.

If the error still pops up, we might need to look at the subnets.

<img src="./media/image23.png" style="width:6.49936in;height:2.73809in" />

Check if all subnets are having igw if not add rules to access internet
gateway.

The connection to database is active on AWS via workbench:

<img src="./media/image24.png" style="width:6.5in;height:2.56458in" />
