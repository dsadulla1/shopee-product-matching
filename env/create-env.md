## Create ssh keys
ssh-keygen -t rsa -b 2048 -C "Ubuntu-GPU-DS3"

## Setup the conda environment
```bash
conda create -n shopee-kaggle python=3.8
conda activate shopee-kaggle
pip install numpy pandas scikit-learn h5py jupyter tensorflow-gpu tensorflow-addons tensorboard transformers tokenizers kaggle matplotlib
```

## Prepare folder structure
```bash
mkdir ./config
mkdir ./data
mkdir ./env
mkdir ./logs
mkdir ./misc
mkdir ./models
mkdir ./references
mkdir ./results
mkdir ./submissions
```

## To replicate the environment exactly
```bash
$ENV_NAME = shopee-kaggle
conda create -n $ENV_NAME python=3.8
conda activate $ENV_NAME
pip install -r requirements.txt
conda deactivate $ENV_NAME
```

Add `conda activate $ENV_NAME` to your ~/.bashrc

## How was requirements.txt created
`pip freeze > ./requirements.txt`

## How to download competition data from Kaggle
Download the `kaggle.json` file from Kaggle Account and put it in the .kaggle directory in home.
```bash
pip install kaggle
kaggle competitions download -c shopee-product-matching
chmod 600 /home/deepak_sadulla/.kaggle/kaggle.json
```

## Transfer files bertween two servers
```bash
nohup scp -qr deepak_sadulla@13.66.245.127:~/notebooks/Kaggle/jigsaw-multilingual-toxic-comment-classification . > log1.log 2> error1.log
# Hit Ctrl+z
bg # check the number of the job you pushed to background
disown -h %1 # use that number instead
```

```bash
nohup scp -qr deepak_sadulla@13.66.245.127:~/notebooks/Kaggle/m5-forecasting-challenge . > log2.log 2> error2.log
# Hit Ctrl+z
bg # check the number of the job you pushed to background
disown -h %1 # use that number instead
```

```bash
scp -qr deepak_sadulla@13.66.245.127:~/notebooks/Kaggle/shopee-product-matching .
```

```bash
# check status of jobs with
jobs -l
```

```bash
# to check if the size is similar, try
du -h
```

## Git setup
```bash
git init
git config --global user.email "YOUR-EMAIL-ID"
git config --global user.name "YOUR-USER-NAME"
git add .
git commit -m "Initial Commit"
git remote add origin git@github.com:dsadulla1/shopee-product-matching.git
git push -u origin master
git push --set-upstream shopee-product-matching master
```