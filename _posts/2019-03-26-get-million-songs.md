---
layout: post
title:  Getting the Million Songs dataset from AWS hosted S3 bucket
date:   2019-03-26 00:00:00
description: Getting the Million Songs dataset into a csv file.
tags: python, aws, jupyter, ec2
categories: AWS
---

This post is related to my project at UVA, that is, classifying songs into one of thirteen genres using song features and lyrical data. Normally, most Music Genre classification projects use the GTZAN dataset which consists of 1000 songs, with 100 songs each for the 10 genres. 

However, we are ambitious people. We found the [Million Songs Dataset](https://labrosa.ee.columbia.edu/millionsong/) published by [LabROSA](https://labrosa.ee.columbia.edu/) group at Columbia. It was freely available on a [AWS mounted snapshot](https://aws.amazon.com/datasets/million-song-dataset/).

So, I knew how to connect to AWS EC2 and run a Jupyter notebook on it. For more details check out my post [here](/blog/2019/aws-putty-post/). 

The other part was figuring out how to connect to the snapshot. It turned out to be kind of easy.

Here are the steps:

*  Choose the Amazon Machine Image of your choice. I chose the most basic one, since I knew I could install Anaconda anytime. It is time consuming though. You can go for one of the Deep Learning AMIs also.

* Go to Add Storage. Attach the Million Songs Dataset to your EC2 instance by clicking on Add New Volume and searching for the million songs snapshot. Make note of the **device name**. Its **/dev/sdb/** as shown here.

{% include figure.html path="assets/img/aws_ms_2.png" class="img-fluid rounded z-depth-1" zoomable=true %}


* Then enter the following commands one after the another.

```bash
sudo mkdir /mnt/snap

sudo mount -t ext4 /dev/xvdb /mnt/snap
```

If all goes well it should look something like this:

{% include figure.html path="assets/img/aws_ms_3.png" class="img-fluid rounded z-depth-1" zoomable=true %}

Et voila, you are done.

Now, see [this Jupyter notebook](https://github.com/ssen7/sys6018-final-project/blob/master/data_gathering_scripts/data_exploration_script.ipynb) for getting the data into a csv file.