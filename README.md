- š Hi, Iām @mysitecreator
- š Iām interested in ...
- š± Iām currently learning ...
- šļø Iām looking to collaborate on ...
- š« How to reach me ...

<!---
mysitecreator/mysitecreator is a āØ special āØ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import requests
from bs4 import BeautifulSoup as bs

base_url = 'https://yaoilib.me/'

r = requests.get('https://yaoilib.me/manga-list?types[]=1')
soup = bs(r.content, features='html.parser')

image = soup.find_all('a', class_='media-card')
manga_list = []

for images in image:
  manga = {}
  manga['image'] = base_url + images['data-src']
  manga['title'] = images.text
  manga['link'] = images['href']
  manga_list.append(manga)

import random

print(random.choice(manga_list))
