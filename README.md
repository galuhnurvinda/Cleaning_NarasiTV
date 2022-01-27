# Cleaning_NarasiTV

   from urllib.request import urlopen
   import json
   import pandas as pd

    #====================================open data=======================================
    url = "https://gist.githubusercontent.com/jorinvo/7f19ce95a9a842956358/raw/e319340c2f6691f9cc8d8cc57ed532b5093e3619/data.json"
    response = urlopen(url)
    data_json = json.loads(response.read())
    #print(data_json)

    #=====================extract name and credit card without missing value==============
    df = pd.DataFrame.from_dict(data_json, orient='columns')
    df1=df[['name', 'creditcard']]
    df1
    cleansing=df1.dropna() #drop missing value
    cleansing

    #==================================save to csv========================================   
    cleansing.to_csv('C:/Users/Bappenas/OneDrive/Pribadi/Narasi TV/20220126.csv', index=False) #path folder bisa disesuaikan
