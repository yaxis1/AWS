**SERVERLESS WEBPAGE WITH API GATEWAY AND LAMBDA**

Configuring a server less webpage that calls a lambda function through
API gateway and lambda in turn responds with the custom function
provided to it.

**Creating lambda service:**

<img src="media\image1.png" style="width:5.0057in;height:2.84059in" />

We can either create a function from scratch or use pre-built functions
from AWS.

**Defining function code:**

<img src="media\image2.png" style="width:6.26806in;height:3.275in" />

When the API calls this lambda function, it returns the text in “head”
and “body”.

On the same page, we can allot IAM role, turn on monitoring, debug and
error handle and other features. Under **basic settings** – memory and
timeout of this function can be specified.

<img src="media\image3.png" style="width:6.26806in;height:2.125in" />

**Triggers:**

Every lambda function needs a trigger to activate it, in our case it is
**API Gateway.**

Create a new **REST API,** that is going to take

<img src="media\image4.png" style="width:6.26806in;height:2.91389in" />

Now, delete any default methods and create a new **GET** method that
works along lambda function:

<img src="media\image5.png" style="width:6.26806in;height:2.46667in" />

After deploying the API, click on **stages&gt;GET** and we should see
**invoke url** – this is the lambda function at work. If the page just
says hello from lambda, it means the function itself is working but
there is something wrong with the code we put in.

<img src="media\image6.png" style="width:3.54216in;height:0.92513in" />

**Fixing lambda function:**

<img src="media\image7.png" style="width:5.15697in;height:2.83373in" />

We see there is an error in the LAMBDA function, after fixing it – we
have:

<img src="media\image8.png" style="width:2.92752in;height:0.78345in" />

We have the API ready, now need a **S3 bucket** to host the webpage that
redirects the content served by **LAMBDA function.**

**Provisioning S3 bucket:**

<img src="media\image9.png" style="width:6.26806in;height:2.125in" />

Since this bucket will be hosting a website, we need to uncheck this
button.

<img src="media\image10.png" style="width:6.26806in;height:0.52917in" />

Under bucket properties, enable **Static website hosting**, make sure
the html page has the same name as the one mentioned in the bucket.

<img src="media\image11.png" style="width:6.26806in;height:4.72917in" />

**INDEX.html**

Now, we need to put the lambda integrated API GATEWAY link in the
**index**.html that will be hosted on S3 bucket. The below code gets the
content from API gateway which is in turn served by LAMBDA function. It
also contains link to another object that will be uploaded in the same
bucket- an awesome picture of **starman**.
<img src="media\image12.png" style="width:6.26806in;height:2.21597in" />

We need to upload this index.html along with the error.html and the
image making sure they are made public.

<img src="media\image13.png" style="width:2.97725in;height:2.28778in" />

When we click on the **object url** from **index.html** this is the html
page:

<img src="media\image14.png" style="width:6.26806in;height:1.96111in" />

When we say “**CLICK HERE” –** this triggers the lambda function through
**API GATEWAY** and the lambda in turn responds with the custom text
that we put in the **LAMBDA FUNCTION**

<img src="media\image15.png" style="width:6.26806in;height:2.47083in" />
