> **AMAZON MACHINE IMAGE**

Amazon machine images are tailored according to work case and there are
suite of images available to choose from starting from server use case
to deep learning.

**Launching an AMI:**

> Inside EC2, first choose the image for respective work case, we are
> going to work on Linux 8.
>
> <img src="./media/image1.png" style="width:6.5in;height:2.7in" />

Choose the instance type based on requirements:

<img src="./media/image2.png" style="width:6.5in;height:2.17431in" />

> Configure network details for this instance, choose the private cloud
> and subnet settings that were created earlier.
>
> The option to enable ‘auto-assign public IP’ requests and IP address
> from available addresses with Amazon.
>
> <img src="./media/image3.png" style="width:6.5in;height:2.90069in" />Create
> a storage volume to be associated with this instance, this again
> depends on the use case of AMI.
>
> <img src="./media/image4.png" style="width:6.5in;height:1.04375in" />
>
> Configure the security group settings to manage the access to this
> instance. In this case we need SSH to be able to access the machine.
>
> <img src="./media/image5.png" style="width:6.5in;height:1.3875in" />
>
> For a secure connection, AWS provides a private key (stored on user’s
> drive) and a public key (stored with AWS). These keys allow
> confidential access to instances. We already created a key previously,
> so we are going to use the same one.
>
> <img src="./media/image6.png" style="width:6.43389in;height:3.892in" />
>
> Launch instances and click on view instances.

Connect to the instance using any of the three methods available:

<img src="./media/image7.png" style="width:6.5in;height:1.09653in" />

<img src="./media/image8.png" style="width:6.5in;height:1.37778in" />

> In cmd, go to the directory where private key is located and launch
> ssh using the command.

<img src="./media/image9.png" style="width:6.1422in;height:1.27511in" />

Now, we are connected to the Linux 8 instance.

<img src="./media/image10.png" style="width:6.5in;height:2.01736in" />

> An image of current instance can be created so that the user doesn’t
> have to configure default settings again.

<img src="./media/image11.png" style="width:6.5in;height:1.41944in" />

This can be resumed from the resources under “Snapshots”

<img src="./media/image12.png" style="width:6.39222in;height:2.10018in" />

<img src="./media/image13.png" style="width:6.5in;height:1.93611in" />
