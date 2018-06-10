---
layout: post
title: Downloading Kaggle Datasets to SageMaker
excerpt_separator:  <!--more-->
comments: true
tags: ['tech-exploration', 'Kaggle', 'SageMaker']
---
- Generate API key in Kaggle UI and upload to your root folder via web interface.
- Agree to competition in Kaggle UI if you haven't already.
- Start a notebook. Execute following commands in a notebook cell replacing the competition name with the competition you are interested in;

```python
%%bash
pip install kaggle

# Move API key to where Kaggle expects it
mv /home/ec2-user/SageMaker/kaggle.json /home/ec2-user/.kaggle

# Download datasets, optionally specify destination folder using --path
kaggle competitions download -c planet-understanding-the-amazon-from-space
```

- Realise that the instance you started doesn't have enough space for the datasets. Oh, crap. Anyhow, if you were forward thinking than me then you should be good to go.
