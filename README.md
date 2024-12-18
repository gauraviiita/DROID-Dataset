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


# Visualize the dataset

Create a file in the same directory where the dataset has already been saved.

```
touch visualize_data.py
gedit visualize_data.py

```
```
import tensorflow_datasets as tfds
import numpy as np
from PIL import Image
from IPython.display import Image as IPImage, display

# Function to create a GIF from a list of images
def as_gif(images, path="temp.gif"):
    """
    Convert a list of PIL images to a GIF.
    
    Args:
        images: List of PIL.Image.Image objects.
        path: Path to save the GIF.
        
    Returns:
        gif_bytes: Bytes of the generated GIF.
    """
    # Save images as a GIF (15Hz control frequency)
    images[0].save(
        path, save_all=True, append_images=images[1:], duration=int(1000 / 15), loop=0
    )
    gif_bytes = open(path, "rb").read()
    return gif_bytes

# Load the droid_100 dataset
print("Loading dataset...")
ds = tfds.load("droid_100", data_dir="gs://gresearch/robotics", split="train")

# Prepare the list of images for visualization
print("Processing dataset...")
images = []
for episode in ds.shuffle(10, seed=0).take(1):  # Randomly shuffle and select one episode
    for i, step in enumerate(episode["steps"]):
        # Concatenate the three images side by side
        combined_image = np.concatenate(
            (
                step["observation"]["exterior_image_1_left"].numpy(),
                step["observation"]["exterior_image_2_left"].numpy(),
                step["observation"]["wrist_image_left"].numpy(),
            ),
            axis=1,
        )
        images.append(Image.fromarray(combined_image))  # Convert to PIL Image

# Create and display the GIF
print("Creating GIF...")
gif_path = "output.gif"
gif_bytes = as_gif(images, path=gif_path)

print("Displaying GIF...")
display(IPImage(data=gif_bytes))

```
