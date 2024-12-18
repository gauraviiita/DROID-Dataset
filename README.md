# [DROID-Dataset](https://droid-dataset.github.io/)

A large-scale in wild robot manipulation dataset

## Steps to download the dataset

Step 1: Colab link to download is [here](https://colab.research.google.com/drive/1b4PPH4XGht4Jve2xPKMCh-AXXAQziNQa?usp=sharing)

Step 2:  **Install Required Libraries:**
```
$ pip install tensorflow

$ pip install tensorflow-datasets

$ sudo snap install google-cloud-cli --classic

$ pip install gcsfs

```
Step 3: Download the dataset using the following command.

There are three types of the dataset.

3.1:  Example dataset version with 100 episodes first (2GB). You can download it by the following command
```
$ gsutil -m cp -r gs://gresearch/robotics/droid_100 /home/dr/Desktop/Gaurav/Research/BU/EgoCentricKitchenData

```

In place of **/home/dr/Desktop/Gaurav/Research/BU/EgoCentricKitchenData** You have to place the path of the output folder where you want to save the dataset.

3.2: You can download the full dataset (1.7TB) using

```
$ gsutil -m cp -r gs://gresearch/robotics/droid <your_local_path>
```

Here, in place of <your_local_path>, you can put the path you want to save the dataset.

3.3 Raw DROID Data: this one will require around 7.1 TB of space to download.

```
gsutil -m cp -r gs://gresearch/robotics/droid_raw <your_local_path>
```
