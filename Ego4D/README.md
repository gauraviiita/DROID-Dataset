# Ego4D dataset

## Step 1: Install Ego4D library
```
pip install ego4d
```

# Step 2: Install the AWS Command Line Interface (AWS CLI) on Ubuntu 22.04

## Step 2.1: Download the AWS CLI Installer
```
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
```
## Step 2.2: Unzip the downloaded file
```
unzip awscliv2.zip
```

## Step 2.3: Run the Installer
```
sudo ./aws/install
```
## Step 2.4: Verify
```
aws --version
```
## Step 2.5: Add to PATH
```
echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bashrc
source ~/.bashrc
```

# Step 3: Configure aws CLI
```
aws configure
```
You’ll be prompted to enter:
```
Access Key ID
Secret Access Key
Default Region (e.g., eu-central-1) for Germany
Output Format (e.g., json)
```
# Step 4: Download the dataset

## Step 4.1: Download downsampled videos (dataset=video_540ss)
```
ego4d --output_directory="/home/dr/Desktop/Gaurav/Ego4d/" --datasets video_540ss
```
## Step 4.2: A single video
```
ego4d --output_directory="/home/dr/Desktop/Gaurav/Ego4d/" --video_uids 2e509e19-90ec-40f0-904e-2f5d0057ed6a --verbose
```

## Step 4.3: Features (e.g slow-fast)
```
ego4d --output_directory="/home/dr/Desktop/Gaurav/Ego4d/" --datasets slowfast8x8_r101_k400
```

## Step 4.4: A list of video uids from a file
```
ego4d --output_directory="/home/dr/Desktop/Gaurav/Ego4d/" --video_uid_file <filename>
```
## Step 4.5: A single benchmark set
```
ego4d --output_directory="/home/dr/Desktop/Gaurav/Ego4d/" --benchmarks vq
```
