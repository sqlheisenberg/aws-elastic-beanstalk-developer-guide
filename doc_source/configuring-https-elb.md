# Configuring Your Elastic Beanstalk Environment's Load Balancer to Terminate HTTPS<a name="configuring-https-elb"></a>

To update your Elastic Beanstalk environment to use HTTPS, you need to configure an HTTPS listener for the load balancer in your environment\.

You can use the Elastic Beanstalk Management Console to configure a secure listener and assign the certificate\.

**To assign a certificate to your environment's load balancer \(AWS Management Console\)**

1. Open the [Elastic Beanstalk console](https://console.aws.amazon.com/elasticbeanstalk)\.

1. Navigate to the management page for your environment\.

1. Choose **Configuration**\.

1. In the **Network Tier** section, choose the gear icon next to **Load Balancing**\.
**Note**  
If the **Network Tier** section is not shown, your environment does not have a load balancer\.

1. In the **Load Balancer** section, choose your certificate from the **SSL certificate ID** drop down menu\.

## Configuring a Secure Listener with a Configuration File<a name="https-loadbalancer-configurationfile"></a>

You can configure a secure listener on your load balancer with a configuration file like the following:

**Example \.ebextensions/securelistener\.config**  

```
option_settings:
  aws:elb:listener:443:
    SSLCertificateId: arn:aws:acm:us-east-2:1234567890123:certificate/####################################
    ListenerProtocol: HTTPS
    InstancePort: 80
```

Replace the highlighted text with the ARN of your certificate\. The certificate can be one that you created in ACM or one that you uploaded to IAM with the AWS CLI\.

The above example uses options in the `aws:elb:listener` namespace to configure an HTTPS listener on port 443 with the specified certificate, and forward the decrypted traffic to the instances in your environment on port 80\.

For more information on load balancer configuration options, see \.

## Security Group Configuration<a name="https-update-security-group"></a>

If you configure your load balancer to forward traffic to an instance port other than port 80, you must add a rule to your security group that allows inbound traffic over the instance port from your load balancer\. If you create your environment in a custom VPC, Elastic Beanstalk adds this rule for you\.

You add this rule by adding a `Resources` key to a configuration file in the `.ebextensions` directory for your application\.

The following example configuration file adds an ingress rule to the `AWSEBSecurityGroup` security group allows traffic on port 1000 from the load balancer's security group\.

**Example \.ebextensions/sg\-ingressfromlb\.config**  

```
Resources:
  sslSecurityGroupIngress:
    Type: AWS::EC2::SecurityGroupIngress
    Properties:
      GroupId: {"Fn::GetAtt" : ["AWSEBSecurityGroup", "GroupId"]}
      IpProtocol: tcp
      ToPort: 1000
      FromPort: 1000
      SourceSecurityGroupName: {"Fn::GetAtt" : ["AWSEBLoadBalancer" , "SourceSecurityGroup.GroupName"]}
```