# How to run

## Step 1: Download finetuned model from this link and upload it to your drive:
https://drive.google.com/file/d/1DMYc8w1xx3JSLorXSBAHD7Q1zUhdPNOJ/view?usp=drive_link

## Step 2: Open fastapi_chatbot.ipynb in Google Colab.


## Step 3: Go to this cell and change zip_path to your finetuned model upload place
```sh
import os
import zipfile

zip_path = '/content/drive/My Drive/iso9001-fine-tuned-model.zip'
extract_dir = '/content/iso9001-fine-tuned-model'

if not os.path.exists(extract_dir):
    print(f"Extracting zip file to: {extract_dir}")
    with zipfile.ZipFile(zip_path, 'r') as zip_ref:
        zip_ref.extractall(extract_dir)
    print("Extraction completed.")
else:
    print(f"Directory already exists: {extract_dir}. Skipping extraction.")
```
## Step 4: Set Huggingface Token (HF_TOKEN) and NGROK Token (NGROK_AUTH_TOKEN) in your Colab
You can create them follow this link:

Huggingface Token: https://huggingface.co/docs/hub/en/security-tokens

NGROK Token: https://dashboard.ngrok.com/get-started/your-authtoken

Then pass them to HF_TOKEN and NGROK_AUTH_TOKEN you create in Colab

## Step 5: Run all cells
