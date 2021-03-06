# The Create New Environment Wizard<a name="environments-create-wizard"></a>

This topic provides more information about pages in the **Create New Environment** wizard\. For basic instructions, see \.


+ [Create a new environment](#environments-create-wizard-newenvironment)
+ [Configuration presets](#environments-create-wizard-presets)
+ [Environment settings](#environments-create-wizard-environment)
+ [Software settings](#environments-create-wizard-software)
+ [Instances](#environments-create-wizard-instances)
+ [Capacity](#environments-create-wizard-capacity)
+ [Load Balancer](#environments-create-wizard-loadbalancer)
+ [Deployment Settings](#environments-create-wizard-deployment-settings)
+ [Security](#environments-create-wizard-security)
+ [Monitoring](#environments-create-wizard-monitoring)
+ [Notifications](#environments-create-wizard-notifications)
+ [Network](#environments-create-wizard-network)
+ [Database](#environments-create-wizard-database)
+ [Worker Details](#environments-create-wizard-worker)
+ [The Old New Environment Wizard](environments-create-wizard-old.md)

## Create a new environment<a name="environments-create-wizard-newenvironment"></a>

You can use the sample application, upload your own application, or specify the URL for the Amazon S3 bucket that contains your application code\.

Choose **Create environment** to launch an environment right away with a default environment name, automatically generated domain, and recommended settings\. To configure more options before you launch, choose **Configure more options**\. You can also launch a new environment based on a custom platform by selecting **Custom platform**, as shown in the following screenshot\. If there are no custom platforms available, this option is greyed out\.

You can create a new environment from two types of platforms:

+ Supported platforms

+ Custom platforms

### Create new environment from supported platform<a name="environments-create-wizard-new-standard-env"></a>

In most cases you will use an Elastic Beanstalk supported platform for your new environment\. When the new environment wizard starts, it selects the **Preconfigured platform** option by default, as shown in the following screenshot\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-defaultenvironment.png)

Scroll through the list, select the supported platform to base your environment on, and select **Create environment**\.

### Create new environment from a custom platform<a name="environments-create-wizard-new-custom-env"></a>

If an off\-the\-shelf platform does not suit your needs, you can create a new environment from a custom platform\. When the new environment wizard starts, select the **Custom platform** option, as shown in the following screenshot\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-createenvironment.png)

**Note**  
Depending on the platform configuration you selected, you can upload your application in a ZIP source bundle, a WAR file, or a plaintext Docker configuration\. The file size limit is 512 MB\. If you select **Custom platform**, the console pops up a window like the following in which you can specify the custom platform setting\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-selectcustomenvironment.png)

Once you've selected the platform from which the new environment is created, you can also change the platform version\. Select **Configure more options** and then **Change platform configuration**\. When the **Change a platform version** window appears, select the version to use for your new environment and select **Save**\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-selectnewversion.png)

Now that you have selected the platform to use, the next step is to load your application code\. If you already have code deployed to Elastic Beanstalk, select **Existing version** and your application in the **Application code** section\.

If you want to upload new code, select **Upload your code**, **Upload** and follow the on\-screen instructions\.

Once you've loaded your application code into the environment, select **Create environement** to create your new environment\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-newenvironment.png)

## Configuration presets<a name="environments-create-wizard-presets"></a>

Elastic Beanstalk provides configuration presets for low\-cost development and high availability use cases\. Each preset includes a default environment name and recommended values for several configuration options\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-presets.png)

The high availability preset includes a load balancer; the low cost preset does not\. Choose this option if you want a load\-balanced environment that can run multiple instances for high availability and scale in response to load\.

The third preset, **Custom configuration**, removes all recommended values except role settings and uses the API defaults\. Choose this option if you are deploying a source bundle with configuration files that set configuration options\. **Custom configuration** is also selected automatically if you modify either the low cost or high availability configuration presets\.

## Environment settings<a name="environments-create-wizard-environment"></a>

Set the name and subdomain, and create a description for your environment\. Be aware that once you specify the environment settings, you cannot change them later\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-environmentsettings.png)

+ **Name** – Enter a name for the environment\.

+ **Domain** – \(web server environments\) Enter a unique URL for your environment\. Although the environment URL is populated with the environment name, you can enter a different name for the URL\. Elastic Beanstalk uses this name to create a unique CNAME for the environment\. To check whether the URL you want is available, click **Check Availability**\.

+ **Description** – Enter a description for this environment\.

+ **Tags** – Add [tags](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) to the resources in your environment\. Restrictions on tag keys and tag values include the following: 

  + Keys and values can contain any alphabetic character in any language, any numeric character, white space, invisible separator, and the following symbols: \_ \. : / = \+ \\ \- @

  + Keys and values are case\-sensitive

  + Values cannot match the environment name

  + Values cannot include **aws:** or **elasticbeanstalk:**

   For more information about using tags, see [Tagging Your Amazon EC2 Resources](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html) in the *Amazon EC2 User Guide for Linux Instances*\.

## Software settings<a name="environments-create-wizard-software"></a>

Configure the instances in your environment to upload rotated logs to Amazon S3, run the AWS X\-Ray daemon for debugging, and set environment properties to pass information to your application\. More platform\-specific settings are available on the **Configuration** page after you create your environment\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-software.png)

+ **X\-Ray Daemon** – Run the AWS X\-Ray daemon for debugging\.

+ **Application logs** – Enable **Log storage** to upload rotated logs from the instances in your environment to your Elastic Beanstalk storage bucket in Amazon S3\.

+ **Environment variables** – Set environment properties that are passed to the application on\-instance as environment variables\.

The way that properties are passed to applications varies by platform\. In general, properties are *not* visible if you connect to an instance and run `env`\.

## Instances<a name="environments-create-wizard-instances"></a>

Configure the Amazon EC2 instances that serve requests in your environment\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-instances.png)

+ **Instance type** – Select a server with the characteristics \(including memory size and CPU power\) that are most appropriate to your application\. 

  For more information about the Amazon EC2 instance types available for your Elastic Beanstalk environment, see [Instance Families and Types](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html) in the *Amazon EC2 User Guide for Linux Instances*\. 

+ **AMI ID** – If you have created a custom AMI, specify the AMI ID to use on your instances\.

+ **Root volume** – Specify the type, size, and input/output operations per second \(IOPS\) for your root volume\.

  + **Root volume type** – From the list of storage volumes types provided by Amazon EBS, choose the type to attach to the Amazon EC2 instances in your Elastic Beanstalk environment\. Select the volume type that meets your performance and price requirements\. For more information, see [Amazon EBS Volume Types](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSVolumeTypes.html) and [Amazon EBS Product Details](http://aws.amazon.com/ebs/details/)\. 

  + **Size** – Set the size of your storage volume\. The size for magnetic volumes can be between 8 GiB and 1024 GiB; SSD volumes can be between 10 GiB and 16,384 GiB\. If you choose **Provisioned IOPS \(SSD\)** as the root volume type for your instances, you must specify the value you want for root volume size\. For other root volumes, if you do not specify your own value, Elastic Beanstalk uses the default volume size for that storage volume type\.

  + **IOPS** – Specify the input/output operations per second that you want\. If you selected **Provisioned IOPS \(SSD\)** as your root volume type, you must specify the IOPS\. The minimum is 100 and the maximum is 4,000\. The maximum ratio of IOPS to your volume size is 30 to 1\. For example, a volume with 3,000 IOPS must be at least 100 GiB\.

## Capacity<a name="environments-create-wizard-capacity"></a>

Configure the compute capacity of your environment and **Auto Scaling Group** settings to optimize the number of instances you're using\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-capacity.png)

+ **Environment type** – Choose **Load balanced** to run the Amazon EC2 instances in your environment behind a load balancer, or **Single instance** to run one instance without a load balancer\.
**Warning**  
A single\-instance environment isn't production\-ready\. If the instance becomes unstable during deployment, or Elastic Beanstalk terminates and restarts the instance during a configuration update, your application may be unavailable for a period of time\. Use single\-instance environments for development, testing, or staging\. Use load\-balanced environments for production\.

+ **Availability Zones** – Restrict the number of Availability Zones to use for instances\.

+ **Instances** – Set the minimum and maximum number of instances to run\.

+ **Placement** – Choose AZs that must have instances at all times\. If you assign Availability Zones here, the minimum number of instances must be at least the number of Availability Zones that you choose\.

A load balanced environment can run multiple instances for high availability and prevent downtime during configuration updates and deployments\. In a load balanced environment, the domain name maps to the load balancer\. In a single instance environment, it maps to an elastic IP address on the instance\.

A **scaling trigger** is an Amazon CloudWatch alarm that lets Auto Scaling know when to scale the number of instances in your environment\. Your environment includes two triggers by default, a high trigger to scale up, and a low trigger to scale down\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-capacity-triggers.png)

+ **Metric** – Choose the metric that the alarm monitors to identify times when you have too few or too many running instances for the amount of traffic that your application receives\.

+ **Statistic** – Choose how to interpret the metric\. Metrics can be measured as an average across all instances, the maximum or minimum value seen, or a sum value from the numbers submitted by all instances\.

+ **Unit** – Specify the unit of measurement for the values of upper and lower thresholds\.

+ **Period** – Specify the amount of time between each metric evaluation\.

+ **Breach duration** – Specifiy the amount of time that a metric can meet or exceed a threshold before triggering the alarm\. This value must be a multiple of the value for **Period**\. For example, with a period of 1 minute and a breach duration of 10 minutes, the threshold must be exceeded on 10 consecutive evaluations to trigger a scaling operation

+ **Upper threshold** – Specify the minimum value that a statistic can match to be considered in breach\.

+ **Lower threshold** – Specify the maximum value that a statistic can match to be considered in breach\.

For more information on CloudWatch metrics and alarms, see [Amazon CloudWatch Concepts](http://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html) in the *Amazon CloudWatch User Guide*\.

## Load Balancer<a name="environments-create-wizard-loadbalancer"></a>

Your environment's load balancer is the entry point for all traffic headed for your application\. Elastic Beanstalk supports several types of load balancer\. When you create an environment using the Elastic Beanstalk console, a Classic Load Balancer is created for your environment\. For more details about load balancer types, see \.

By default, the load balancer serves HTTP traffic on port 80\. You can also configure a secure listener to accept secure connections using HTTPS\. If you use HTTPS to provide secure connections on port 443, you can disable the default listener to require users to connect securely\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-loadbalancer.png)

+ **ELB listener** – The default listener on the load balancer serves HTTP traffic from the Internet or, for an internal application, networks connected to your VPC\.

+ **Secure ELB listener** – The secure listener terminates HTTPS connections using a TLS/SSL certificate and passes the decrypted traffic to your instances\. You can upload certificates with IAM, or [create a new certificate with AWS Certificate Manager](http://docs.aws.amazon.com/acm/latest/userguide/gs-acm-request.html)for a domain that you own\.

Use the remaining options to enable cross\-zone load balancing and connection draining\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-loadbalancer-etc.png)

+ **Cross\-zone load balancing** – Ensures traffic is balanced correctly when the number of instances in each availability zone is not uniform, and prevents issues due to DNS caching on clients\.

+ **Connection draining** – Allows time for active connections to complete before deregistering an instance from the load balancer during scaling operations, updates, and deployments\.

You can use configuration files to configure more load balancer options, including advanced listener configuration, TCP passthrough, application load balancing, and backend authentication\. See  and  for more information\.

## Deployment Settings<a name="environments-create-wizard-deployment-settings"></a>

 For single\-instance environments, choose a **Deployment policy** to configure how to deploy new application versions and changes to the software configuration for instances\. **All at once** completes deployments as quickly as possible, but can result in downtime\. **Immutable** deployments ensure the new instance passes health checks before switching over to the new version; otherwise the old version remains untouched\. See  for more information\.

For load\-balanced environments, choose a **Deployment policy** to configure how to deploy new application versions and changes to the software configuration for instances\. **All at once** completes deployments as quickly as possible, but can result in downtime\. Rolling deployments ensure that some instances remain in service during the entire deployment process\. See  for more information\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-rolling.png)

+ **Deployment policy** – **Rolling** deployments take one batch of instances out of service at a time to deploy a new version\. **Rolling with additional batch** launches a new batch first to ensure that capacity is not affected during the deployment\. **Immutable** performs an immutable update when you deploy\. 

+ **Batch size** – The number or percentage of instances to update in each batch\.

Rolling updates occur when you change instance launch configuration settings or VPC settings, which require terminating and replacing the instances in your environment\. Other configuration changes are made in place without affecting capacity\. For more information, see \.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-rolling-updates.png)

+ **Rolling update type** – Time based, where AWS CloudFormation waits for the specified amount of time after new instances are registered before moving on to the next batch, or health based, where AWS CloudFormation waits for instances to pass health checks\. **Immutable** performs an immutable update when a configuration change would normally trigger a rolling update\.

+ **Batch size** – The number of instances to replace in each batch\.

+ **Minimum capacity** – The minimum number of instances to keep in service at any given time\.

+ **Pause time** – For time\-based rolling updates, the amount of time to wait for new instances to come up to speed after they are registered to the load balancer\.

The remaining options customize health checks and timeouts\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-rolling-deploys.png)

+ **Ignore health check** – Prevents a deployment from rolling back when a batch fails to become healthy within the **Command timeout**\.

+ **Healthy threshold** – Lowers the threshold at which an instance is considered healthy during rolling deployments, rolling updates, and immutable updates\.

+ **Command timeout** – The number of seconds to wait for an instance to become healthy before canceling the deployment or, if **Ignore health check** is set, to continue to the next batch\.

## Security<a name="environments-create-wizard-security"></a>

Choose an Amazon EC2 key pair to enable SSH or RDP access to the instances in your environment\. If you have created a custom service role and instance profile, select them from the drop\-down lists\. If not, use the default roles, `aws-elasticbeanstalk-service-role` and `aws-elasticbeanstalk-ec2-role`\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-security.png)

+ **Service role** – A service role grants Elastic Beanstalk permission to monitor the resources in your environment\.

+ **EC2 key pair** – Assign an SSH key to the instances in your environment to allow you to connect to them remotely for debugging\. For more information about Amazon EC2 key pairs, see [Using Credentials](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-credentials.html) in the *Amazon EC2 User Guide for Linux Instances*\.

+ **IAM instance profile** – An instance profile grants the Amazon EC2 instances in your environment permissions to access AWS resources\. 

The Elastic Beanstalk console looks for an instance profile named `aws-elasticbeanstalk-ec2-role` and a service role named `aws-elasticbeanstalk-service-role`\. If you don't have these roles, the console creates them for you\. For more information, see [Service Roles, Instance Profiles, and User Policies](concepts-roles.md)\.

## Monitoring<a name="environments-create-wizard-monitoring"></a>

For load\-balanced environments, **Health check path** tells the load balancer where to send requests for health checks\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-monitoring.png)

+ **Health check path** – The path to send health check requests to\. If not set, the load balancer attempts to make a TCP connection on port 80 to verify health\. Set to a path starting with `/` to send an HTTP GET request to that path\. You can also include a protocol \(HTTP, HTTPS, TCP, or SSL\) and port before the path to check HTTPS connectivity or use a non\-default port\. For example, `HTTPS:443/health`\.

+ **Health reporting system** – Enhanced health reporting provides additional health information about the resources in your environment at no additional charge\.

## Notifications<a name="environments-create-wizard-notifications"></a>

Specify an email address to receive email notifications for important events from your environment\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-notifications.png)

+ **Email** – An email address for notifications\.

## Network<a name="environments-create-wizard-network"></a>

If you have created a custom VPC, use these settings to configure your environment to use it\. If you do not choose a VPC, Elastic Beanstalk uses the default VPC and subnets\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-network.png)

+ **VPC** – The VPC in which to launch your environment's resources\. 

+ **Load balancer visibility** – Makes your load balancer internal to prevent connections from the Internet\. This option is for applications that serve traffic only from networks connected to the VPC\.

+ **Load balancer subnets** – Choose public subnets for your load balancer if your site serves traffic from the Internet\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-network-instances.png)

+ **Public IP address** – Choose this option if you run your instances and load balancer in the same public subnets\.

+ **Instance subnets** – Choose private subnets for your instances\.

+ **Instance security groups** – Choose security groups to assign to your instances, in addition to standard security groups that Elastic Beanstalk creates\.

For more information about Amazon VPC, see [Amazon Virtual Private Cloud \(Amazon VPC\)](http://aws.amazon.com/vpc/)\.

## Database<a name="environments-create-wizard-database"></a>

Add an Amazon RDS SQL database to your environment for development and testing\. Elastic Beanstalk provides connection information to your instances by setting environment properties for the database hostname, username, password, table name, and port\. When you add a database to your environment, its lifecycle is tied to your environment lifecycle\.

For production environments, you can configure your instances to connect to an external database\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-database.png)

+ **Engine** – Choose the database engine used by your application\.

+ **Engine version** – Choose the version of the database engine\.

+ **Instance class** – Choose a database instance class\. For information about the DB instance classes, see [http://aws\.amazon\.com/rds/](http://aws.amazon.com/rds/)\.

+ **Storage** – Specifiy the amount of storage space, in gigabytes, to allocate for your database\. For information about storage allocation, see [Features](https://aws.amazon.com/rds/#features)\.

+ **Username** – The username for the database administrator\. Username requirements vary per database engine\.

+ **Password** – The password for the database administrator\. Password requirements vary per database engine\.

+ **Retention** – You can use a snapshot to restore data by launching a new DB instance\. Choose **Create snapshot** to save a snapshot of the database automatically when you terminate your environment\.

+ **Availability** – Choose **High \(Multi\-AZ\)** to run a second DB instance in a different Availability Zone for high availability\.

For more information about Amazon RDS, see [Amazon Relational Database Service \(Amazon RDS\)](http://aws.amazon.com/rds/)\.

## Worker Details<a name="environments-create-wizard-worker"></a>

**\(worker environments\)** You can create an Amazon SQS queue for your worker application or pull work items from an existing queue\. The worker daemon on the instances in your environment pulls an item from the queue and relays it in the body of a POST request to a local HTTP path relative to the local host\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/wizard-worker.png)

+ **Worker queue** – Choose the queue from which the worker environment tier reads messages that it will process\. If you do not provide a value, then Elastic Beanstalk automatically creates one for you\.

+ **HTTP path** – Specifiy the relative path on the local host to which messages from the queue are forwarded in the form of HTTP POST requests\.

+ **MIME type** – Choose The MIME type of the message sent in the HTTP POST request\.

+ **HTTP connections** – The maximum number of concurrent connections to the application\. Set this to the number of processes or thread messages that your application can process in parallel\.

+ **Visibility timeout** – The amount of time that an incoming message is locked for processing before being returned to the queue\. Set this to the potentially longest amount of time that might be required to process a message\.