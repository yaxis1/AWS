**APACHE SERVER USING USER SCRIPTS**

**Create a new instance with public subnet.**

<img src="./media/image1.png" style="width:6.5in;height:1.23056in" />

We use the security group created earlier; it can be configured later if
required.

Confirm the key and launch instance.

<img src="./media/image2.png" style="width:6.5in;height:2.2in" />

**Connect to this instance using “PuTTY”**
<img src="./media/image3.png" style="width:3.91667in;height:2.90833in" />

Put the username and ip address in hostname.

We need to provide PuTTY with the key to access this instance, but PuTTY
does not support ‘.pem’ provided by AWS. We need to install PuTTY gen to
convert .pem to .ppk.

<img src="./media/image4.png" style="width:5.0171in;height:4.48372in" />

Select the .ppk file in Auth and open. We can save this session in
“session” configuration.

Now, we are on our instance via PuTTY.

<img src="./media/image5.png" style="width:6.5in;height:2.79444in" />

**Install http and php on this instance:**

<img src="./media/image6.png" style="width:4.9671in;height:1.10843in" />

Start the service:

<img src="./media/image7.png" style="width:5.85884in;height:0.72506in" />

However, we cannot connect to this as our security group doesn’t have
http enabled. It only has tcp and icmp.

**Update inbound rules to add http:**

<img src="./media/image8.png" style="width:6.5in;height:2.45139in" />

Now, when we try to connect using the Public IP of our instance, we can
see the default apache page loaded.

<img src="./media/image9.png" style="width:6.5in;height:1.49167in" />

We can now add content to the directory /var/www/html/ to customize our
http page. But we will do this using user script so that the process is
done automatically every time an instance is launched. We will try this
on multiple instances at once.

\#!/bin/bash

**Update the linux OS:**

*sudo yum update -y*

**Install http:**

*sudo yum install -y httpd php*

**Start http:**

*sudo service httpd start*

**Create a php file to display IP address of current instance:**

*sudo echo "&lt;?php \\$ip = \\$\_SERVER\['REMOTE\_ADDR'\]; echo \\$ip;
?&gt;" &gt; phpinfo.php*

**Move this file to default apache location:**

*sudo mv phpinfo.php /var/www/html/*

**Create 3 instances:**

<img src="./media/image10.png" style="width:6.5in;height:2.71806in" />

Pasting the user script in *advanced details*.

<img src="./media/image11.png" style="width:6.5in;height:1.96667in" />

We use the security group that has http enabled.

<img src="./media/image12.png" style="width:6.5in;height:1.64514in" />

Now, we have 3 instances with same user script - the process of creating
a php file and moving it to source directory is automatically done at
launch.

<img src="./media/image13.png" style="width:6.5in;height:2.04653in" />

We use the IP address of any one instance and check if the user script
is working:

<img src="./media/image14.png" style="width:6.5in;height:2.71528in" />

The instances are running, and script has been automatically implemented
at launch for all our instances.
