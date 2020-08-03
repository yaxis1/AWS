HOSTING A STATIC WEBPAGE ON S3

**Creating a bucket:**

> In order to store data on S3, we need a storage allocation in one of
> the Regions. S3 bucket is a scalable storage in the cloud.

-   Search for bucket in the aws console

-   Create bucket and enter bucket name

<img src=".//media/image1.png" style="width:6.5in;height:1.85208in" />

-   Region – choose a nearest region for better latency.

<img src=".//media/image2.png" style="width:6.23333in;height:3.82125in" />

> We can also configure to watch few metrics of this bucket by selecting
> CloudWatch under Management:

<img src=".//media/image3.png" style="width:6.5in;height:3.43333in" />

**Enable static website hosting**

-   Enable static website hosting for this bucket in the properties.

-   The **index document** and **error document** display the home page
    and error page on our website. With redirection rules, we can
    automaticall redirect specific requests.

> <img src=".//media/image4.png" style="width:6.5in;height:3.24167in" />

**Enable public access settings:**

> By default, public access is blocked for bucket, this can be unchecked
> from the Permissions tab.

-   Click on save and confirm for the settings to be applied.

> <img src=".//media/image5.png" style="width:6.5in;height:2.70972in" />

**Create a policy to enable public access for contents of bucket.**

> Under Permissions, go to **Bucket Policy** and add the policy here
> with current bucket resource name.

<img src=".//media/image6.png" style="width:6.5in;height:2.41181in" />

> Now that we have public access to our website, we can configure the
> index document to display on website.

**Configuring index document**

For our html page, we give the same name as the one in the bucket
properties.

<img src=".//media/image7.png" style="width:6.5in;height:2.81042in" />

Based on the use case, a storage class can be selected, then click on
upload.

> <img src=".//media/image8.png" style="width:6.5in;height:2.98333in" />
>
> <img src=".//media/image9.png" style="width:6.5in;height:1.55in" />

We can test this from the end point link from the bucket properties:

<img src=".//media/image10.png" style="width:4.93333in;height:1.94167in" />

<img src=".//media/image11.png" style="width:6.5in;height:1.30139in" />
