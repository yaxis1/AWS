> **AWS REKOGNITION**

<img src="./media/image1.png" style="width:6.5in;height:1.69653in" />

We use two instances (ubuntu) with:

1.  Apache – for front end

2.  Conda – for back end

**Create instances:**

Choose the ubuntu server:

<img src="./media/image2.png" style="width:6.5in;height:0.43403in" />

We are going to use the same AMI for both instances

<img src="./media/image3.png" style="width:6.5in;height:3.27222in" />

Create a new security group, we are going to edit the rules for
individual servers later:

<img src="./media/image4.png" style="width:6.5in;height:1.36319in" />

Confirm the keypair and launch instances.

Now we have the instances up and running, rename the instances:

<img src="./media/image5.png" style="width:6.5in;height:1.06389in" />

**Connecting via PuTTY:**

Use the public IP of ‘front end’ instance and select the .pem file in
SSH – Auth.

Save this login information and open.

<img src="./media/image6.png" style="width:4.975in;height:3.875in" />

**Install APACHE on this instance:**

On the front-end instance, update the package manager and install
Apache.

<img src="./media/image7.png" style="width:6.40055in;height:0.90008in" />

<img src="./media/image8.png" style="width:4.6254in;height:0.75006in" />

To check if it’s working, paste the public IP of this instance in a
browser and Apache’s default page should load up.

But, for our instance we didn’t configure the security group yet. We
need to enable “http” in the inbound rules of our SG.

<img src="./media/image9.png" style="width:6.5in;height:2.01458in" />

Save the rules and It works!

<img src="./media/image10.png" style="width:6.5in;height:1.84375in" />

**Move the front-end files to default location:**

<img src="./media/image11.png" style="width:6.5in;height:1.30347in" />

Clone the code repository to out instance:

<img src="./media/image12.png" style="width:6.5in;height:0.34097in" />

Navigate to the index.html in repo to move it to the default Apache
location mention mentioned on their page.

<img src="./media/image13.png" style="width:6.5in;height:3.25in" />

Now, when we reload our browser, we have the front-end page loaded up,
but the buttons don’t have any functionality.

<img src="./media/image14.png" style="width:6.5in;height:1.54167in" />

Moving the other file from repo to default Apache location:

<img src="./media/image15.png" style="width:6.5in;height:0.99306in" />

Now, we have the files from repo into the default apache location:

<img src="./media/image16.png" style="width:6.5in;height:0.73819in" />

Normally, when we reload the browser page, the front end should work.
But in our case we need to do some checking inside the code.

We see in the script, it uses ‘static’ not “Static”:

<img src="./media/image17.png" style="width:6.5in;height:3.79306in" />

To fix this, we can move rename the folder name on our instance:

<img src="./media/image18.png" style="width:5.0171in;height:0.7584in" />

Now, when we reload the page, we have the functionalities working:

<img src="./media/image19.png" style="width:6.5in;height:2.77778in" />

This is a webcam access level error; we are going to fix later.

Front end is up and running on our EC2 Instance.

**Install conda on the other Instance:**

**Connect to other instance using PuTTY:**

<img src="./media/image20.png" style="width:6.5in;height:2.92847in" />

Select the .pem file inside Auth and open the connection and update the
package manager.

Clone the repo on ‘back end instance’:

<img src="./media/image21.png" style="width:6.5in;height:1.60556in" />

<img src="./media/image22.png" style="width:5.52548in;height:1.28344in" />

We moved the files from Frontend\_machine to the other instance, now we
are working on backend\_machine. We can see it is a .py file.

On this machine we need:

-   Conda

-   Virtual environment with Python 3.6

-   Packages – “Flask”, “flask\_cors” and “boto3”.

**Installing conda on backend instance:**

wget – to download from internet.

<img src="./media/image23.png" style="width:6.5in;height:1.52431in" />

The installation file is now downloaded.

**Install Anaconda using bash:**

<img src="./media/image24.png" style="width:6.5in;height:1.27708in" />

**Activating conda in current terminal:**

source \~/.bashrc

<img src="./media/image25.png" style="width:5.85884in;height:2.51688in" />

Conda is installed on ‘backend instance’

Create an environment with python 3.6.

<img src="./media/image26.png" style="width:6.5in;height:0.81944in" />

<img src="./media/image27.png" style="width:6.5in;height:0.52361in" />

Now, we are in virtual environment ‘flask\_env’

Install required packages:

-   conda install Flask

-   conda install -c anaconda flask-cors

-   conda install boto3

> pip freeze displays all the installed packages with their versions:

<img src="./media/image28.png" style="width:6.5in;height:3.60417in" />

Now, we can run that .py file and it seems to run on port 5000.

<img src="./media/image29.png" style="width:6.5in;height:1.26389in" />

This port is used to make a connection with front end. We need to enable
port 5000 on backend instance.

<img src="./media/image30.png" style="width:6.5in;height:2.64514in" />

To test if the port is working, we can write a function in .py file to
display text.

<img src="./media/image31.png" style="width:6.5in;height:1.93472in" />

Now we have backend and frontend up and running, we need to make a
connection between them so that they communicate with each other and the
Rekognition works.

**Creating IAM :  
**Looking at the code, we see that the the code requires IAM roles to
S3(to store pictures) and Rekognition API.

On the AWS console, go to IAM roles and enable access:

<img src="./media/image32.png" style="width:6.5in;height:2.34167in" />

<img src="./media/image33.png" style="width:6.5in;height:1.95in" />

Review the roles and create:

<img src="./media/image34.png" style="width:6.5in;height:4.10972in" />

**Attaching these roles to backend instance:**

<img src="./media/image35.png" style="width:6.5in;height:1.98333in" />

Select the role that we created and apply:

<img src="./media/image36.png" style="width:6.5in;height:1.52569in" />

Now, when we look at the .py code, we see that we also need a S3 bucket.

<img src="./media/image37.png" style="width:6.5in;height:2.33333in" />

**Creating bucket to store captured images:**

Make sure the bucket name and location match with the one’s in the code.

<img src="./media/image38.png" style="width:6.5in;height:4.29097in" />

Now, we have all the functions from .py working and AWS Rekognition
running.
