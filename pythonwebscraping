import requests
from bs4 import BeautifulSoup
import pandas as pd

url='http://books.toscrape.com/'

response=requests.get(url)

if response.status_code==200:
    soup=BeautifulSoup(response.text,'html.parser')
    books=soup.find_all('article',class_='product_pod')
    titles=[]
    prices=[]

    for book in books:
        title=book.h3.a['title']
        price=book.find('p',class_='price_color').text
        titles.append(title)
        prices.append(price)

        df=pd.DataFrame({
            'Title':titles,
            'Price':prices
            })
        df.to_csv('books.csv',index=False)
        print("Data scraped and saved into books.csv")

else:
    print(f"Failed to retrieve the webpage. Status code:{response.status_code}")

