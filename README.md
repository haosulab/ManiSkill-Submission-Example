# ManiSkill Challenge Submission Example

## Submission Structure 

### Overview
At least two files need to be included in your submission:
1. `environment.yml`: specify the python packages needed by your policy
2. `user_solution.py`:  participants need to implement a `UserPolicy` class in this file.

**Both files must be in the root directory of your submission.** This directory will
also be added to the `PYTHONPATH` environment variable. So if you are including
your own python module, you need to put it the same level as `environment.yml`.

Participants are free to include other files in your submission, e.g., the
checkpoint of your model.

**Note: please do not include `.git` and PartNet-Mobility dataset in your submission, since they can be very large.**

### Environment
You are required to export your conda environment by running this command.
```
conda env export --name ENVNAME > environment.yml
```

### User Policy
Participants need to implement a `UserPolicy` class in `user_solution.py`.
Specifically, the following member functions need to be implemented:
1. `__init__(self, env_name, opts=None)`
In this function, participants should initialize the policy (e.g., load the checkpoint).
Remember to set `self.obs_mode` to the appropriate one (`rgbd` or `pointcloud`, `state` is not available during evaluation), which will affect the observations received by this policy.

2. `act(self, observation)`
This function receives raw observations from environment. 
The content of the observation is determined by `self.obs_mode` set in the `__init__` function.
This function should return an action, and this action will be passed to the environment.

3. `reset(self)` (optional)
This function will be called at the beginning of each episode.
Participants can use this function to reset their policy (e.g, an RNN-based policy probably should be reset).

### Check your submission
If you want to check your submission before submitting to your websites, 
you can follow the steps described [here](https://github.com/haosulab/ManiSkill#evaluation) 
to evaluate your submission locally for one episode.

## How to submit
Solutions need to be submitted to the challenge website
[https://sapien.ucsd.edu/challenges/maniskill2021/](https://sapien.ucsd.edu/challenges/maniskill2021/).

First make sure you are logged into our authenticator by click on the login
button at the top right corner. You will be asked to sign into the SULab
authenticator. You need your email account (.edu preferred) to complete the sign
in process. If your email is not accepted, please contact us.

Now you should be able to authorize the challenge site to use your SULab
authenticator account to log in. After the first time logging in, you will be
asked to provide a username (a nickname), which will be your name displayed on
all the leaderboards.

Now click on the `Submission` tab on the challenge website, you should be able
to see all the challenges available. Click any challenge will reveal the current
rankings for this challenge. Click `Create Submission` button to start creating
your own submission.

In the submission form, you need to fill in its name and optionally a
description. Next, pick the challenge track you are submitting to. Then, you
need to upload **a single zip file containing all your submission files**. You may
include files directly at the root level of the zip or provide a folder in the
zip. (We accept zip with file structure of both `/enviornment.yml` and
`/xxx/environment.yml` so you do not need worry about how the zip is created).
Finally, click the submit button and wait for the upload to finish.
