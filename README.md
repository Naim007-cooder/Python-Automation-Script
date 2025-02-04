# Python Automation and Web Scraping Scripts

This repository contains Python scripts to automate common tasks such as file handling, email automation, and Excel reports, as well as web scraping techniques to extract data from websites.

## 🔹 Automation Scripts

These scripts automate common tasks like file handling, email automation, and Excel reports.

### 1️⃣ Automate File Renaming

Rename all files in a folder based on a pattern.

```python
import os

folder_path = "path/to/your/folder"

for count, filename in enumerate(os.listdir(folder_path)):
    ext = filename.split(".")[-1]  # Get file extension
    new_name = f"file_{count+1}.{ext}"  
    os.rename(os.path.join(folder_path, filename), os.path.join(folder_path, new_name))

print("Files renamed successfully!")
```



### 2️⃣ Automate Excel Report Generation
Create an Excel file with a summary of data.

```python
import pandas as pd

# Sample data
data = {'Name': ["Naim", "Mohaymin", "Samio"],
        'Sales': [500, 700, 600]}

df = pd.DataFrame(data)

# Save to Excel
df.to_excel("sales_report.xlsx", index=False)

print("Excel report generated!")
```
### 3️⃣ Automate Email Sending (Gmail SMTP)
Send automated emails using Python.
```python
import smtplib
from email.mime.text import MIMEText

sender_email = "your_email@gmail.com"
receiver_email = "recipient_email@gmail.com"
password = "your_password"

message = MIMEText("Hello, this is an automated email!")
message["Subject"] = "Automated Email"
message["From"] = sender_email
message["To"] = receiver_email

with smtplib.SMTP("smtp.gmail.com", 587) as server:
    server.starttls()
    server.login(sender_email, password)
    server.sendmail(sender_email, receiver_email, message.as_string())

print("Email sent successfully!")
```
#### 💡 Tip: Use "App Passwords" instead of your Gmail password for security.

🔹 Web Scraping Scripts
These scripts help extract data from websites.

### 4️⃣ Scrape a Website with BeautifulSoup
Extract titles from a news website.

```python
import requests
from bs4 import BeautifulSoup

url = "https://news.ycombinator.com/"
response = requests.get(url)

soup = BeautifulSoup(response.text, "html.parser")

titles = soup.find_all("a", class_="storylink")

for idx, title in enumerate(titles[:5]):
    print(f"{idx+1}. {title.text}")
```


### 5️⃣ Scrape Dynamic Websites Using Selenium
Extract job listings from LinkedIn.

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

driver = webdriver.Chrome()  # Ensure you have chromedriver installed
driver.get("https://www.linkedin.com/jobs/search/?keywords=data%20analyst")

time.sleep(3)  # Wait for page to load

jobs = driver.find_elements(By.CLASS_NAME, "job-card-container")

for idx, job in enumerate(jobs[:5]):
    print(f"{idx+1}. {job.text}")

driver.quit()
```


### 6️⃣ Scrape E-commerce Product Prices (Amazon Example)
Scrape product price from Amazon.

```python
import requests
from bs4 import BeautifulSoup

headers = {"User-Agent": "Mozilla/5.0"}

url = "https://www.amazon.com/dp/B09G3HRP7H"
response = requests.get(url, headers=headers)

soup = BeautifulSoup(response.text, "html.parser")
price = soup.find("span", class_="a-offscreen").text
print(f"Product Price: {price}")
 ```
💡 Tip: Amazon has anti-scraping protections. You may need proxies and rotating headers.

### 7️⃣ Automate Data Scraping & Save to CSV
Save scraped data into a CSV file.

```python
import pandas as pd

data = {"Name": ["Naim", "Mohaymin", "Samio"], "Score": [90, 85, 88]}

df = pd.DataFrame(data)
df.to_csv("scraped_data.csv", index=False)

print("Data saved successfully!")
```
### *8.* What's app automation
``` python
import pywhatkit as kit

# Send a WhatsApp message at 10:30 AM to the given phone number
phone_number = '+1234567890'  # Include the country code
message = 'Hello, this is an automated message!'
kit.sendwhatmsg(phone_number, message, 10, 30)  # Time in 24-hour format (10:30 AM)
```
## 📬 Contact

For questions or feedback, feel free to contact:

- **Author:** Naim
- **Email:** naimurrashid1105@gmail.com ✉️
- **GitHub:** [Naim007-cooder](https://github.com/Naim007-cooder)

Thank you for exploring this project! Happy analyzing! 🎉
