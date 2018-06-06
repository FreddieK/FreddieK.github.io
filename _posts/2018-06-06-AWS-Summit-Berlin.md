---
layout: post
title: AWS Summit Berlin 2018
excerpt_separator:  <!--more-->
comments: true
tags: ['AWS Summit Berlin']
---

A few quick notes from AWS Summit Berlin of things that I found interesting.

<!--more-->

### Software Development Process at Amazon - Jonathan Weiss
> "It's impossible to detect all problems in staging."

- **Pessimistic deployment** - assumption that every change in production might have unforeseen bad consequences. Thus; ensure a problem gets limited spread by only deploying to a subset of full production initially. Monitor metrics on that subset before scaling up deployment gradually.

- **Multistep Deployment Pipelines** - Run tests in various steps, start with the faster ones like build and unit tests to give quick feedback upon failure. Run smoke tests, integrations tests and load tests as a later step only if initial steps passes.

- **Monitor Everything** - Keep track of all relevant metrics, and make sure you understand the cause of all changes. The teams are expected to present and explain the metrics regularly.

- **Business Metrics** - Team keeps track of adoption rates of features, conversion funnels, costs etc... Presents regularly to stakeholders.

- **Listen to your customers** - Get feedback on what you build and correct your course if needed.

### Working Backwards - Experience First
- Based on this [blog post](https://www.allthingsdistributed.com/2006/11/working_backwards.html) by Werner Vogels, CTO at Amazon.

> "It's a common problem to mistake a feature for a customer need. Instead of asking 'What problem can I solve with this solution', do it the other way around."

For a new idea; start with writing a press release for how it would be launched. Test if this is something that clients would excited about to know if this answers an actual customer need.

> "Before this product exists, clients had these problems [...]. Now with this product, the problems are solved. Continue with writing FAQs, user manuals, create mockups etc... _Experience first_. Only at the very very end do we think about what is actually technically feasible.""

Doing this work ensures the team gets a _shared mental model_, which is deeply valuable to ensure cohesion and understanding for when work actually starts.

## Serverless Predictions at Scale - Thomas Reske
Blueprints for Serverless Predictions using MXNet.

* API Gateway -> Lambda function -> S3 (Model Archive)
 * [Serverless predictions at Scale](https://aws.amazon.com/blogs/compute/seamlessly-scale-predictions-with-aws-lambda-and-mxnet/)
* ELB + Fargate (Model Server for Apache MXNet -> Docker)
* SageMaker (Docker)

...more advanced versions of the two latter options might be to put the actual models outside the Docker images, and adding API Gateway and Lambda functions before to transform the API requests.
