# Terminate an Environment<a name="using-features.terminating"></a>

You can terminate a running environment using the AWS Management Console to avoid incurring charges for unused AWS resources\. For more information about terminating an environment using the AWS Toolkit for Eclipse, see [Terminating an Environment](create_deploy_Java.terminating.md)\.

**Note**  
 You can always launch a new environment using the same version later\. If you have data from an environment that you would like to preserve, create a snapshot of your current database instance before you terminate the environment\. You can later use it as the basis for new DB instance when you create a new environment\. For more information, see [Creating a DB Snapshot](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_CreateSnapshot.html) in the [Amazon Relational Database Service User Guide](http://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Welcome.html)\.

## AWS Management Console<a name="using-features.terminating.CON"></a>

**To terminate an environment**

1. Open the [Elastic Beanstalk console](https://console.aws.amazon.com/elasticbeanstalk)\.

1. From the region list, select the region that includes the environment that want to terminate\.

1. From the Elastic Beanstalk console applications page, click the name of the environment that you want to terminate\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/aeb-app-page-env.png)

1. Click **Actions** and the select **Terminate Environment**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/images/aeb-env-dashboard-action.png)

1. Confirm that you are terminating the correct environment and then click **Terminate**\.
**Note**  
When you terminate your environment, the CNAME associated with the terminated environment becomes available for anyone to use\. 

   It will take a few minutes for Elastic Beanstalk to terminate the AWS resources running in the environment\. 

## CLI<a name="using-features.terminating.CLI"></a>

**To terminate an environment**

+ 

  ```
  $ aws elasticbeanstalk terminate-environment --environment-name my-env
  ```

## API<a name="using-features.terminating.API"></a>

**To terminate an environment**

+ Call `TerminateEnvironment` with the following parameter:

  + `EnvironmentName` = `SampleAppEnv`  
**Example**  

  ```
  1. https://elasticbeanstalk.us-west-2.amazon.com/?EnvironmentName=SampleAppEnv
  2. &Operation=TerminateEnvironment
  3. &AuthParams
  ```