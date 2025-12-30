# AWS Certified Developer Associate Udemy Course

Documentation of my learnings on [Udemy's AWS Certified Developer Associate course](https://www.udemy.com/course/aws-certified-developer-associate-dva-c01/). There are additional [practice exams](https://www.udemy.com/course/aws-certified-developer-associate-practice-tests-dva-c01/?_gl=1*153z2mj*_ga*Nzc4MDgxNDIyLjE3NjcwMzI2ODg.*_ga_6GZZTGGX7H*czE3NjcwMzI2ODckbzEkZzAkdDE3NjcwMzI2ODckajYwJGwwJGgw&couponCode=DEC_25_GET_STARTED) outside of the one utilized in this course that I can use to prep for my certificate.

## AWS Cloud History

* 2002: Internally launced
* 2003: Amazon infrastrucutre is one of their core stengths, idea to market
* 2004: Launhed publicly with SQS
* 2006: Re-launched publicly with SQS, S3, and EC2
* 2007: Launched in Europe
* Used by Dropbox, AirBnb, NetFlix, NASA, and more

## AWS Cloud Facts

* In 2023, AWS had $90 billion in annual revenue
* AWS accounts for 31% of the market in Q1 2024 (Microsoft is 2nd with 25%)
* Pioneer and Leader of the AWS Cloud Market for the 13th consecutive year
* Over 1,000,000 active users

## AWS Cloud Use Cases

* AWS enables you to build sophisticated, scalable applications
* Applicable to a diverse set of industries
* Use cases include:
  * Enterprise IT, Backup & Storage, Big Data analytics
  * Website hosting, Mobile & Social Apps
  * Gaming

## AWS Global Infrastructure

* AWS Regions
  * Regions all around the world: `us-east-1`, `eu-west-3`, etc
  * Most AWS services are region scoped
* AWS Availability Zones
  * Each region has many availability zones (usually 3, minis 3 max is 6)
    * ap-southeast-2a
    * ap-southeast-2b
  * Each AZ is one or more discrete data centers with redundant power, networking, connectivity
  * They're separate from each other, so that they're isolated from disasters
  * They're connected with high bandwidth, ultra-low latency networking
* AWS Data Centers
  * A region is a cluster of data centers
* AWS Edge Locations / Points of Presence
* [Interactive Infrastructure Map](https://infrastructure.aws/)

## How to choose an AWS Region?

* **Compliance** with data governance and legal requirements: data never leaves a region without your explicit permission
* **Proximity** to customers: reduced latency
* **Available services** within a Region: new services and new features aren’t available in every Region
* **Pricing**: pricing varies region to region and is transparent in the service pricing page

## AWS Points of Presence (Edge Locations)

* Amazon has 400+ Points of Presence (400+ Edge Locations & 10+ Regional Caches) in 90+ cities across 40+ countries
* Content is delivered to end users with lower latency

## Product Services

* AWS has Global Services:
  * Identity and Access Management (IAM)
  * Route 53 (DNS service)
  * CloudFront (Content Delivery Network)
  * WAF (Web Application Firewall)
* Most AWS services are Region-scoped:
  * Amazon EC2 (Infrastructure as a Service)
  * Elastic Beanstalk (Platform as a Service)
  * Lambda (Function as a Service)
  * Rekognition (Software as a Service)
* [Region Table](https://aws.amazon.com/about-aws/global-infrastructure/regional-product-services)

## Deeper Dive Notes:
  * [IAM & AWS CLI](./notes/iam-and-aws-cli.md)