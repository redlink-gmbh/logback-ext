Logback Extensions
==================

[![Build Status](https://img.shields.io/travis/redlink-gmbh/logback-ext.svg?style=flat-square)](https://travis-ci.org/redlink-gmbh/logback-ext)
[![Maven Central](https://img.shields.io/maven-central/v/io.redlink.ext.logback/logback-ext.svg)](http://search.maven.org/#search%7Cga%7C1%7Cg%3A%22io.redlink.ext.logback%22)
[![Sonatype (Snapshots)](https://img.shields.io/nexus/s/https/oss.sonatype.org/io.redlink.ext.logback/logback-ext.svg)](https://oss.sonatype.org/#nexus-search;gav~io.redlink.ext.logback~logback-ext~~~)
[![Javadocs](https://www.javadoc.io/badge/io.redlink.ext.logback/logback-ext.svg)](https://www.javadoc.io/doc/io.redlink.ext.logback/logback-ext)
![License](https://img.shields.io/github/license/redlink-gmbh/logback-ext.svg?style=flat-square)

Extensions for Logback logging library mainly for appenders aimed for Amazon Web Services,
including CloudWatch Logs, DynamoDB, Kinesis, SNS and SQS appenders. Contains also high
performance asynchronous appender based on LMAX disrupotr and some utilities like Jackson JSON
encoder.

This project was forked and repackaged from [trautonen/logback-ext](https://github.com/trautonen/logback-ext).
The `groupId` has been renamed, but `artifactId` and source-packages are left intact.

## Using Logback Extensions

Logback Extensions requires Java 7 or newer. Include desired modules in your project's
dependency management and configure the appenders or encoders using Logback's XML configuration
or Java API.


### Modules

All modules belong to group `io.redlink.ext.logback`. See each module for specific documentation.

* Extensions core module: [logback-ext-core](logback-ext-core/)
* AWS core module: [logback-ext-aws-core](logback-ext-aws-core/)
* Jackson JSON encoder: [logback-ext-jackson](logback-ext-jackson/)
* LMAX Disruptor appender: [logback-ext-lmax-appender](logback-ext-lmax-appender/)
* CloudWatch appender: [logback-ext-cloudwatch-appender](logback-ext-cloudwatch-appender/)
* DynamoDB appender: [logback-ext-dynamodb-appender](logback-ext-dynamodb-appender/)
* Kinesis appender: [logback-ext-kinesis-appender](logback-ext-kinesis-appender/)
* SNS appender: [logback-ext-sns-appender](logback-ext-sns-appender/)
* SQS appender: [logback-ext-sqs-appender](logback-ext-sqs-appender/)


### AWS Authentication

All AWS based appenders require IAM authentication. The default credentials provider from
`org.eluder.logback.ext.aws.core.AwsSupport` creates a credential chain in the following order.

1. Environment variables `AWS_ACCESS_KEY_ID` and `AWS_SECRET_KEY`
2. System properties `aws.accessKeyId` and `aws.secretKey`
3. Appender configuration properties `accessKey` and `secretKey`
4. AWS profile configuration file `~/.aws/credentials`
5. EC2 instance role

Best practice for EC2 instances is to use instance role only. With instance role no access keys or
secret keys are exposed if the server is compromised.


### Continuous Integration

TravisCI builds the project with Oracle JDK 7 and 8. Builds created with Oracle JDK 7 are deployed
to Sonatype OSSRH.
