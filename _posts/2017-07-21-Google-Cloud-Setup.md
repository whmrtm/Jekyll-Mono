---
layout: post
title: Google Cloud Setup - VPS
author: Author Heming
---

Happen to hear this $300 free quota Google Cloud for 1 year, just need to register with a credit card.

Link: [Google Cloud](https://cloud.google.com/)

So I registered and found that there are many functions here. A good thing of course, but it really confused me when I try to do what I need to do. Wrote this note to record the basic setup steps. 

## Setup VPS for Google Cloud

Once you have the account, go into console. Then create a project in the "Compute Engine", and it is actually a virtual mathine that we need. Choose a valid zone that is appropriate for you( you can check the speed with ping or other tools)

Then choose the Machine Type, pick GPU if you need to do Parallel Computing or Bitcoin mining. Not sure if bitcoin minining violates the rules of Google Cloud, but you can find it out yourself.
For a "GFW"-purposed vps, only need 1 shared CPU, and approxiametly 20 GB hard disk. Note that GPU price is more expersive than AWS. And if you need to do Deep learning onling, TPU of Google might be a better choice.

System type can be anything you like, and Ubuntu 16.04 LTS might be the most familiar one. (Also just a suggestion, centOS can be a good choice for cloud server).

After all the setup, the cost of the vps can be checked at the "Price" in the hamburger menu. 

Check 
[Connect to remote instance](https://cloud.google.com/compute/docs/instances/connecting-to-instance)
for more information.

At the point you have your vps, and you can log in the server using ssh. Under windows, putty is a good tool for that. And if you are using Linux, you know what to do.

## Remote Database

+ Remain to be Done