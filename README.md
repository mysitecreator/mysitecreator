- 👋 Hi, I’m @mysitecreator
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
mysitecreator/mysitecreator is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import requests
from bs4 import BeautifulSoup as bs

base_url = 'https://yaoilib.me/'

r = requests.get('https://yaoilib.me/manga-list?types[]=1')
soup = bs(r.content, features='html.parser')
# headers = {
#     'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/103.0.0.0 Safari/537.36'
# }
# another = requests.post(base_url + 'filterlist', headers=headers)
# print(another.text)

# print(x.find('img', class_='top-user__avatar'))

image = soup.find_all('a', class_='media-card')
# print(image['data-scr'])
manga_list = []

for images in image:
  manga = {}
  manga['image'] = base_url + images['data-src']
  manga['title'] = images.text
  manga['link'] = images['href']
  manga_list.append(manga)

import random

print(random.choice(manga_list))
