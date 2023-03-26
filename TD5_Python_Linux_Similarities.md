# TD8/9: Linux, Git and Python

# Exercise 1: Working Directory

## 1. Create an empty working directory called “td4”.
mkdir td4

## 2. Initialize a Git repository in it.
cd td4  
git init

## 3. Install the Linux python3-pip package using your Linux package manager.
sudo apt update  
sudo apt install python3-pip

## 4. Install the VirtualEnv Python package using pip3.
sudo pip3 install virtualenv

## 5. Create a Python virtual environment called “.env”. Do you see the change in your working directory ?
virtualenv .env

## 6. Activate your virtual environment. Do you see the change in your prompt ?
source .env/bin/activate

## 7. List the Python packages installed in your virtual environment.
pip list

## 8. Does Git want you to commit something ? Do you think it is a good thing ?
Yes because i made modifications on some files

## 9. Create a .gitignore file to tell Git which files should be untracked.
git add .gitignore

## 10. Does Git want you to commit something ? Do you think it is a good thing this time ?
Yes

## 11. Do your first commit and check that Git is happy now.
git commit -m "Add .gitignore file"

# Exercise 2: Python Script

## 1. Install the Python package Requests using pip.
pip install requests

## 2. Create a Python script that returns the list of all place ids in Derbyshire.
import requests
url = "https://nominatim.openstreetmap.org/search"
params = {
    "q": "Derbyshire",
    "format": "json",
    "polygon_geojson": 1
}

response = requests.get(url, params=params)
county_boundary = response.json()[0]["geojson"]["coordinates"][0]
url = "https://overpass-api.de/api/interpreter"

query = f"""
[out:json];
area["name"="Derbyshire"]->.searchArea;
(
  node["place"](area.searchArea);
  way["place"](area.searchArea);
);
out center;
"""

payload = {
    "data": query
}

response = requests.post(url, data=payload)

place_ids = []
for feature in response.json()["elements"]:
   


## 3. Commit your changes in Git
git add script.py  
git add .gitignore    
git commit -m "Python"

