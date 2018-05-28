---
layout: post
title: Deploying Scikit-learn model on AWS Lambda using Zappa
excerpt_separator:  <!--more-->
comments: true
tags: ['Zappa', 'AWS Lambda', 'tech-exploration']
---
Mini project; Following [this blog post](https://towardsdatascience.com/how-to-deploy-a-machine-learning-model-on-aws-lambda-24c36dcaed20) step by step to make a XGBoost model created through Scikit-learn available through a Lambda function using [Zappa](https://www.zappa.io/).

<!--more-->

Nice tutorial and easy to follow, though I'm unsure how the ```load_model()``` function could have worked when trying to create the already existing bucket every time it's called, which for me throws an error (...and thus changed to ```conn.get_bucket(BUCKET_NAME)``` instead). Additionally, I changed out the json encoding function to ```return pd.Series(prediction[-1]).to_json(orient='index')``` to get it to work with my model.

Further, the tutorial is almost a year old, and Zappa doesn't work with ```pip 10.0.1``` currently, so I had to downgrade to ```9.0.3```. This is apparently a [known issue](https://github.com/Miserlou/Zappa/issues/1478).

Now, the API and model works beautiful locally and it should just be the ```zappa deploy``` left to go, and how sweet that would be. As the project tarball ends up being closer to 90mbs though, **trying to deploy just ends up with timeouts from the command line though I have quite decent upload speed.** Trying to change the Boto timeout does nothing to help.

After trying for an hour to find a solution, I give up.

**Status: Fail**
