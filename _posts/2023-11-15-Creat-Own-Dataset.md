---
layout: post
title: Create Custom Dataset for YOLO by Google Image Crawling
date: 2023-11-15 20:10:20 +0900
description: Create Custom Dataset  # Add post description (optional)
img: how-to-start.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Python, ML, Crawling, Dataset]
use_math: true
---

To create your own dataset for YOLO (You Only Look Once) in Google Colab and save images through Google image crawling, you can use a combination of web scraping tools and Python code. Additionally, you can use VSCode for writing and executing your Python scripts. Here's a step-by-step guide:

### Step 1: Install necessary libraries

In your Colab notebook, install the required libraries for web scraping:

```python
!pip install beautifulsoup4
!pip install requests
```

### Step 2: Create a script for image crawling

Create a Python script (e.g., `image_crawler.py`) in VSCode and write a script using Beautiful Soup and Requests libraries for web scraping. The script might look like this:

```python
import os
import requests
from bs4 import BeautifulSoup
from urllib.parse import urlparse, urljoin

def download_image(url, folder):
    try:
        response = requests.get(url, stream=True)
        file_extension = url.split('.')[-1]
        file_name = os.path.join(folder, f"{hash(url)}.png")

        with open(file_name, 'wb') as file:
            for chunk in response.iter_content(chunk_size=128):
                file.write(chunk)
        
        print(f"Downloaded: {url}")
        return file_name
    except Exception as e:
        print(f"Error downloading {url}: {e}")
        return None

def crawl_images(search_query, num_images, save_folder):
    search_url = f"https://www.google.com/search?q={search_query}&tbm=isch"
    headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36'}

    response = requests.get(search_url, headers=headers)
    soup = BeautifulSoup(response.text, 'html.parser')

    image_urls = []
    for img in soup.find_all('img', class_='t0fcAb'):
        image_url = img.get('src')
        if image_url:
            image_urls.append(image_url)

    if not os.path.exists(save_folder):
        os.makedirs(save_folder)

    count = 0
    for url in image_urls[:num_images]:
        download_image(url, save_folder)
        count += 1

        if count == num_images:
            break

if __name__ == "__main__":
    search_query = "your_search_query"  # Replace with your desired search query
    num_images = 100  # Adjust the number of images you want
    save_folder = "images"  # Replace with your desired save folder

    crawl_images(search_query, num_images, save_folder)
```

### Step 3: Run the script

In VSCode, open a terminal and run the script:

```bash
python image_crawler.py
```

This script will download images from Google Image search based on the specified query and save them in the specified folder.

### Step 4: Annotate images

After downloading images, you need to annotate them for YOLO. You can use annotation tools like LabelImg for this purpose.

### Step 5: Organize your dataset

Organize your dataset into the YOLO format. Each image should have a corresponding text file with the same name containing the bounding box annotations.

Now, you can use this dataset for training your YOLO model.

Note: Ensure that you have permission to use and download images from the internet, and comply with the terms of service of the websites you scrape. Additionally, web scraping may be subject to legal and ethical considerations. Always respect copyright and intellectual property rights.