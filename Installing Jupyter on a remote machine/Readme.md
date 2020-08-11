**Installing Jupyter on a remote machine.**

Launch an instance with the public subnet and enable “Auto-assign Public
IP”

<img src="./media/image1.png" style="width:6.5in;height:1.99444in" />

Create a new security group to have complete control over the instance:

<img src="./media/image2.png" style="width:6.5in;height:1.75069in" />

Confirm the key and launch instance from PuTTY.

Inside PuTTY: Go to Auth and select the path that directs to the key
used to launch instance.

<img src="./media/image3.png" style="width:4.15694in;height:2.53333in" />

Login using the public IP of our instance:

<img src="./media/image4.png" style="width:4.93333in;height:3.85833in" />

Now, we are connected to our instance:

<img src="./media/image5.png" style="width:6.5in;height:2.13611in" />

**Installing Anaconda on our instance:**

Update the package manager:

sudo apt-get update

Install curl to be able to download from internet:

sudo apt-get install curl

Switch to the /tmp directory and use curl to download the installer
using your command terminal:

cd /tmp

curl –O
https://repo.anaconda.com/archive/Anaconda3-2020.07-Linux-x86\_64.sh

Anaconda is being installed:

<img src="./media/image6.png" style="width:6.5in;height:0.8625in" />

<img src="./media/image7.png" style="width:4.72983in;height:0.4584in" />

Verify the download checksum:

sha256sum Anaconda3–2020.07–Linux–x86\_64.sh

<img src="./media/image8.png" style="width:6.5in;height:0.49167in" />

Install Anaconda using bash:

bash Anaconda3-2020.07-Linux-x86\_64.sh.sh

Accept terms and conditions saying ‘yes’

<img src="./media/image9.png" style="width:6.40714in;height:2.04195in" />

Press Enter to install in same location or define a location.

Before accessing conda, we need to activate the installation using:

source \~/.bashrc

Test the installation:

conda info

<img src="./media/image10.png" style="width:6.5in;height:2.24167in" />

We can update conda and anaconda using:

conda update conda

conda update anaconda

Now we can create Python environments:

conda create ––name myenv python=3

To activate this environment:

conda activate myenv

Now we’re in our environment:

<img src="./media/image11.png" style="width:5.50077in;height:0.47923in" />

To deactivate the environment:

conda deactivate myenv

To access jupyter notebook, back in the base environment:

<img src="./media/image12.png" style="width:5.27083in;height:0.20833in" />

To access this notebook in the browser, we use any of the following
links.

<img src="./media/image13.png" style="width:6.5in;height:1.16667in" />

But this only works on local machine and since jupyter is not on local
machine, we need to change this:

Use “ jupyter notebook --ip=0.0.0.0” to make the notebook listen on
private IP.

Jupyter is now binding using private IP of our instance on gate 8888.

<img src="./media/image14.png" style="width:6.5in;height:3.14028in" />

But, when we look at the security group of our instance, we only have
tcp enabled and we need port 8888 for notebook to connect.

<img src="./media/image15.png" style="width:6.5in;height:2.66111in" />

**Update the security group to enable 8888 port:**

<img src="./media/image16.png" style="width:6.5in;height:1.89583in" />

Save and copy the url from cmd. Note that it is bound with private IP
and we need to replace this with public IP of our instance.

<img src="./media/image17.png" style="width:6.5in;height:0.7625in" />

After inserting Public IP:

<img src="./media/image18.png" style="width:6.5in;height:0.19236in" />

When we run this on a browser, we have the notebook up and running:

<img src="./media/image19.png" style="width:6.5in;height:1.32361in" />

<img src="./media/image20.png" style="width:6.5in;height:0.83403in" />

If we want to run this even after the command prompt is closed, we can
use “nohup”

This command saves the token(that is need to be put in the url for
notebook) into a new file.

<img src="./media/image21.png" style="width:6.5in;height:0.81667in" />

Now we have an additional file apart from anaconda3. Inside nohup.out we
have token saved.

<img src="./media/image22.png" style="width:6.10502in;height:0.54174in" />

The command prompt is closed, and we still have the notebook running:

<img src="./media/image23.png" style="width:6.5in;height:1.38333in" />We
need to get into our environment ‘myenv’ and install ‘ipykernel’

<img src="./media/image24.png" style="width:6.5in;height:1.19167in" />

Now, linking the environments.

<img src="./media/image25.png" style="width:6.5in;height:0.39306in" />We
have our second environment ready on the browser.

<img src="./media/image26.png" style="width:6.5in;height:1.78333in" />
