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
