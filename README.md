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
## Step 4: Set Google API Token (GOOGLE_API_TOKEN) and NGROK Token (NGROK_AUTH_TOKEN) in your Colab
You can create them follow this link:

Google API Token: https://aistudio.google.com/app/apikey

NGROK Token: https://dashboard.ngrok.com/get-started/your-authtoken

Then pass them to GOOGLE_API_TOKEN and NGROK_AUTH_TOKEN you create in Colab

## Step 5: Set NGROK Domain
You can create NGROK Domain follow this link:

NGROK Domain: https://dashboard.ngrok.com/domains

Then in cell Run, pass your domain to this line:
```sh
public_url = ngrok.connect(addr=8000, domain="your-domain")
print("Public URL:", public_url)
```

## Step 6: Run all cells

## Connect to Backend
In qms_backend project, on ChatbotService.cs:
Pass your API URL to this line:
```sh
public ChatbotService(QmsDbContext dbContext, HttpClient httpClient, IDocumentManagement documentManagement)
{
    _dbContext = dbContext;
    _httpClient = httpClient;
    _chatbotApiUrl = "https://{your-domain}/";
    _documentManagement = documentManagement;
}
```
