# import libraries 

from bs4 import BeautifulSoup
import requests
import time
import datetime

import smtplib

URL = 'https://www.amazon.com/Surround-Headphones-Cancelling-Flexible-Earmuffs/dp/B09TB15CTL/ref=sr_1_1?_encoding=UTF8&content-id=amzn1.sym.12129333-2117-4490-9c17-6d31baf0582a&dib=eyJ2IjoiMSJ9.kFa4r_d6Ai_ZS6dUSLhwfSpmcGNBhQxULfjaHbYVNmdi1KF3uHNdCyOpiwc2tqT_UyEaJ1TsDBfaCWLLHD-KnQzB5wfVQL3vMbr2tZ-X1zTKk-9rHNdDALE3ip-hMaLNR2pI0LIpfP3YvW8evK1-EsnWYxEMcfMDXmumM9QsSj0tfmex4YXXZGJtCxZf2PROh5sf971GBuHOqthLB2Xw1uApM4H38ELjXCO2ElybDeY._kx3pvBv7wCLqdcxEmsHKdrJv2Hm8cK1aTDbVBh78fA&dib_tag=se&keywords=gaming+headsets&pd_rd_r=e2da7633-97c2-46f0-b0c2-0c0d30ed86ec&pd_rd_w=sE5Le&pd_rd_wg=E77Vg&pf_rd_p=12129333-2117-4490-9c17-6d31baf0582a&pf_rd_r=SPGAX0YK3TD2TSCJNC05&qid=1719733234&sr=8-1'

headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}

page = requests.get(URL, headers=headers)

soup1 = BeautifulSoup(page.content, "html.parser")

soup2 = BeautifulSoup(soup1.prettify(),"html.parser")

title = soup2.find(id='title').get_text()

ratings = soup2.find(id='acrCustomerReviewText').get_text()

print(title)
print(ratings)




title =title.strip()
ratings=ratings.strip()
print(title)
print(ratings)


import datetime

date = datetime.date.today()

print(date)



import csv

headers = ['Title','Ratings','Date']

data = [title,ratings,date]


# type(data)

with open('Amazonscraping.csv','w',newline='',encoding='UTF8') as f:
    writer = csv.writer(f)
    writer.writerow(headers)
    writer.writerow(data)




import pandas as pd
dataset = pd.read_csv(r'C:\Users\Mourya\Desktop\python\Amazonscraping.csv')

print(dataset)


#Appending data

with open('Amazonscraping.csv','a+',newline='',encoding='UTF8') as f:
    writer = csv.writer(f)
    writer.writerow(data)




def check_price_automate():
    URL = 'https://www.amazon.com/Surround-Headphones-Cancelling-Flexible-Earmuffs/dp/B09TB15CTL/ref=sr_1_1?_encoding=UTF8&content-id=amzn1.sym.12129333-2117-4490-9c17-6d31baf0582a&dib=eyJ2IjoiMSJ9.kFa4r_d6Ai_ZS6dUSLhwfSpmcGNBhQxULfjaHbYVNmdi1KF3uHNdCyOpiwc2tqT_UyEaJ1TsDBfaCWLLHD-KnQzB5wfVQL3vMbr2tZ-X1zTKk-9rHNdDALE3ip-hMaLNR2pI0LIpfP3YvW8evK1-EsnWYxEMcfMDXmumM9QsSj0tfmex4YXXZGJtCxZf2PROh5sf971GBuHOqthLB2Xw1uApM4H38ELjXCO2ElybDeY._kx3pvBv7wCLqdcxEmsHKdrJv2Hm8cK1aTDbVBh78fA&dib_tag=se&keywords=gaming+headsets&pd_rd_r=e2da7633-97c2-46f0-b0c2-0c0d30ed86ec&pd_rd_w=sE5Le&pd_rd_wg=E77Vg&pf_rd_p=12129333-2117-4490-9c17-6d31baf0582a&pf_rd_r=SPGAX0YK3TD2TSCJNC05&qid=1719733234&sr=8-1'

    headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/126.0.0.0 Safari/537.36", "Accept-Encoding":"gzip, deflate", "Accept":"text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8", "DNT":"1","Connection":"close", "Upgrade-Insecure-Requests":"1"}

    page = requests.get(URL, headers=headers)

    soup1 = BeautifulSoup(page.content, "html.parser")

    soup2 = BeautifulSoup(soup1.prettify(),"html.parser")

    title = soup2.find(id='title').get_text()

    ratings = soup2.find(id='acrCustomerReviewText').get_text()
    
    title=title.strip()
    ratings=ratings.strip()
    
    import datetime

    date = datetime.date.today()
    import csv

    headers = ['Title','Ratings','Date']

    data = [title,ratings,date]
    with open('Amazonscraping.csv','a+',newline='',encoding='UTF8') as f:
        writer = csv.writer(f)
        writer.writerow(data)


    #Adding a timer and automating the data

while(True):
    check_price_automate()
    time.sleep(86400)


import pandas as pd
dataset = pd.read_csv(r'C:\Users\Mourya\Desktop\python\Amazonscraping.csv')

print(dataset)
    
