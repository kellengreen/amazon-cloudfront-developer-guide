# HTTP 503 status code \(Service Unavailable\)<a name="http-503-service-unavailable"></a>

An HTTP 503 status code \(Service Unavailable\) typically indicates a performance issue on the origin server\. In rare cases, it indicates that CloudFront temporarily can’t satisfy a request because of resource constraints at an edge location\.

**Topics**
+ [Origin server does not have enough capacity to support the request rate](#http-503-service-unavailable-not-enough-origin-capacity)
+ [CloudFront caused the error due to resource constraints at the edge location](#http-503-service-unavailable-limited-resources-at-edge-location)

## Origin server does not have enough capacity to support the request rate<a name="http-503-service-unavailable-not-enough-origin-capacity"></a>

CloudFront generates this error when the origin server is overwhelmed with incoming requests\. CloudFront then relays the error back to the user\. To resolve this issue, try the following solutions:
+ If you use Amazon S3 as your origin server, optimize the performance of Amazon S3 by following the best practices for key naming\. For more information, see [Optimizing Amazon S3 performance](https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html) in the *Amazon Simple Storage Service User Guide*\.
+ If you use Elastic Load Balancing as your origin server, see [How do I troubleshoot 503 errors returned while using Classic Load Balancer?](http://aws.amazon.com/premiumsupport/knowledge-center/503-error-classic/)
+ If you use a custom origin, examine the application logs to ensure that your origin has sufficient resources, such as memory, CPU, and disk size\. If you use Amazon EC2 as the backend, make sure that the instance type has the appropriate resources to fulfill the incoming requests\. For more information, see [Instance types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html) in the *Amazon EC2 User Guide for Linux Instances*\.

## CloudFront caused the error due to resource constraints at the edge location<a name="http-503-service-unavailable-limited-resources-at-edge-location"></a>

You will receive this error in the rare situation that CloudFront can’t route requests to the next best available edge location, and so can’t satisfy a request\. This error is common when you perform load testing on your CloudFront distribution\. To help prevent this, follow the [Load testing CloudFront](load-testing.md) guidelines for avoiding 503 \(capacity exceeded\) errors\.

If this happens in your production environment, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.