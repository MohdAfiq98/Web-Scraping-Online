# Web-Scraping-Online

## Table of Contents

## Introduction
Web scraping is a process of data extraction from websites using bots or tools retrieving content based on their html tags. The data then will be stored in database for observation or analysis purposes.

Web scraping allows for the quick and efficient extraction of data in the form of information from various sources. Hence, the data obtained is more up-to-date compared using secondary data which will be limited in the field of study.

As for this project, the objective is 1. to extract data from a real estate website and convert the findings into a database and 2. data cleaning and standardization for better data view. Python along with BeautifulSoup library is used to complete the task. The website choosen will be the Realtor.com website, a platform sells property around the world. In this field of study, property in Malaysia will be observed.

The project consists of a demo program, to test the extraction mechanism and the full progran that will demonstrate the full extraction process. At the end of the project, we successfully extract the data from one page and export the data to csv file, before proceed with data cleaning using python.

## Tools
Web scraping need a proper tools to execute and all the process will be automated by proper algorithms. Below are the tools used in this project.  

1. Jupyter Notebook : A open-sourced web-based platform consists multuiple programming language including Python.
2. BeautifulSoup : A python package or built-in library for parsing HTML and XML documents.


## Methodology
We will explain details on how the project beeing conducted methodically. We will included the library importation, data extraction process, data exportation, and data cleaning. All process can be seen by refering the image output based on real output throughout the project being held. All coding and output files can be dowloaded for more informations on how it is conducted.

### Import Appropriate Library
Starting the project by importing related  python libraries to help build the data scrapping automation. All the libraries are :

1. Pandas : A library for data manipulation and analysis that offers data structures and operations for manipulating numerical tables and time series
2. BeautifulSoup : A python package for parsing HTML and XML documents that can be used to extract data from HTML which useful for web scrapping.
3. Requests : A HTTP client library for python that maps the HTTP protocol onto Python's object-oriented semantics.

![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/5a15cce0-6178-4eca-8fc2-4680ffc53d6e)


### Data Extraction
In this section, we will start the extraction process. We will using [realtor.com](https://www.realtor.com/), a platform that sells property all around the world. This website really helps us to meet the objectives as it is available for scraping. Response [200] is an output that indicates that we successfully request the website for scrapping.  

![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/27bb15aa-6421-4c86-9f9d-e4a467ef2f32)

The project consist of two different jupyternotebook files where, the first file named 'realtor_scrap_demo.ipynb' is the demo where we will test the extraction algorithm by extracting only one property. The second file named 'realtor_scrap_project.ipynb' will be the finalised programme where we successfully extract all the property data.

As for the extraction process, we are interested in extracting listing id, list_title, price, property_type. date, agent_name, agency_name. We will extract all this information by refering the html tags from the website. To view the html tags, we open the developer tools to have more insights for each particular tags of the data that we want.  

![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/414cc6ef-e0c6-4b28-8261-7c1e23f49aeb)
_Image above is the screenshot of the parts from the developer tools to extract data using HTML tags_  

Below are the python code demos to extract the data for a single property listing.

```python
# Extract List ID
new_soup.find('span', attrs={'class':'listing-id'}).text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/8f04907e-5069-446a-9f57-324bf66cf608)

```python
# Extract Property Tittle
new_soup.find('h3', attrs={'class':'lbxu17-2 qvrsN description-title'}).text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/8bad9dc1-5f5f-4cbe-a791-4de94cbf993f)

```python
#Extract Property Price
new_soup.find('div', attrs={'class':'sc-10v3xoh-1 cqrlhJ'}).text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/3328a59d-f414-42c6-9184-eb5053b4ddc9)

```python
# Extract Property Type
new_soup.find('div', attrs={'class':'sc-12iqlu8-2 dPeBQf basicInfoValue'}).text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/005630ee-dc30-401f-937f-875f0a6f5dc6)

```python
#Extract Date Post and Updated
new_soup.find('div',attrs={'class':'data'}).text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/733b48c4-9688-4264-bc55-bc44ecf7ed15)

```python
#Extract Agent Name
new_soup.find('div', attrs={'class':'agent-name'}).text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/120d7255-bd8d-49b6-ad95-6cfed32b7f90)

```python
# Extract Agency Name
new_soup.find('p').text
```
![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/2092fabe-6ef1-477f-a646-68db3b6b8155)

After successfully extracted data from a single listing, we proceed to extract all property listing from the whole page by programming a full code. The full program was run in different jupyter notebook file named 'Realtor Scrap Project.ipynb'. We developed a full programm to extract all the data from numerous of property listing. We assigned functions specifically to obtain the automation in extracting all the data. 

```python
# Function to extract property tille
def get_property_title(soup):
    try:
        title = soup.find('h3', attrs={'class':'lbxu17-2 qvrsN description-title'})
        title_value = title.text
        
    except:
        title_value = ''
        
    return title_value

# Function to extract property listing id
def get_property_id(soup):
    try:
        id = soup.find('span', attrs={'class':'listing-id'})
        id_value = id.text
    except:
        id_value = ''
    
    return id_value

    
# Function to extract property price
def get_price(soup):
    try:
        price = soup.find('div', attrs={'class':'sc-10v3xoh-1 cqrlhJ'})
        price_value = price.text
    except:
        price_value = ''
        
    return price_value
    
# Extract property type
def get_property_type(soup): 
    div = soup.findAll('div', attrs={'class':'sc-12iqlu8-2 dPeBQf basicInfoValue'})
    try:
        property_type = div[0]
        property_type_value = property_type.text
    except: 
        property_type_value = ''
        
    return property_type_value
    

# Extract post and update date
def get_date(soup):
    try:
        date = soup.find('div',attrs={'class':'data'})
        date_value = date.text
    except
        date_value = ''
        
    return date_value

# Extract Agent Name
def get_agent(soup):
    try:
        agent = soup.find('div', attrs={'class':'agent-name'})
        agent_value = agent.text
    except:
        agent_value = ''
    
    return agent_value

# Extract agency name
def get_agency(soup):
    try:
        agency = soup.find('p')
        agency_value = agency.text
    except:
        agency_value = ''
        
    return agency_value
```

The main programme as below

```python
if __name__ == '__main__':
    
    # add user agent
    headers = ({"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36"})
    
    # webpage url
    url = 'https://www.realtor.com/international/my//'
    
    # HTTP requests
    webpage = requests.get(url,headers=headers)
    
    # soup object contain html
    soup = BeautifulSoup(webpage.content, 'html.parser')
    
    # Fetch all tag that contains list of object
    links = soup.findAll('a', attrs={'class':'sc-1dun5hk-0 cOiOrj'})
    
    # Store the links
    links_list = []
    
    # Loop for extracting links from tag objects
    for link in links:
        links_list.append(link.get('href'))
        
    d = {'list_id':[], 'list_title':[],'price':[], 'property_type':[],
         'date':[], 'agent_name':[], 'agency_name':[]}
    

    # loop for extracting property details from each link
    for link in links_list:
        new_webpage = requests.get("https://www.realtor.com/" + link, headers=headers)
        new_soup = BeautifulSoup(new_webpage.content, 'html.parser')
        
        d['list_id'].append(get_property_id(new_soup))
        d['list_title'].append(get_property_title(new_soup))
        d['price'].append(get_price(new_soup))
        d['property_type'].append(get_property_type(new_soup))
        d['date'].append(get_date(new_soup))
        d['agent_name'].append(get_agent(new_soup))
        d['agency_name'].append(get_agency(new_soup))
        
    property_df = pd.DataFrame.from_dict(d)
    property_df.to_csv("property_list_data.csv", header=True, index=False)
```
All data is successfully extracted. Snippet of result can be seen below. The full data is stored in file named 'property_listed_data.csv'.  

![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/4446214e-9fa8-40f5-af71-f6b42e1243cc)


### Data Cleaning
The data extracted after the data mining process is not standardize to its format. In this section, all data are cleaned to meet appropriate format and standardized. The data cleaning process was inititate using python again in the jupyter notebook platform. The csv filed named 'property_listed_data.csv' that obtained previously again imported to jupyter notebook to proceed with the data cleaning process. As result, we want the data structure from,  

![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/1deae811-84f2-43bc-91a6-724d0032e54f)

to the clean and standardized result,

![image](https://github.com/MohdAfiq98/Web-Scraping-Online/assets/119799325/92522efb-9a1b-4451-b881-c1c8ece8e8dd)

We obtained the above result by running the code below

```python
# Standardize price column
data['price'] = data['price'].str.lstrip('MYR')

# Standardize date column
data['date'] = data['date'].str.lstrip('Published on:')
data[['date_published','date_updated']] = data['date'].str.split('Last updated on:',1,expand=True)

data = data.drop(columns='date')

# Standardize agency column
data['agency_name'] = data['agency_name'].str.strip('Email enquiry to')
data['agency_name'] = data['agency_name'].str.upper()

# remove null from title column
data['list_title'] = data['list_title'].str.strip('null,')
data['list_title'] = data['list_title'].str.strip('null, ')
data
```

After cleaning process, the data was exported into csv file named 'property_listing_data_cleaned'.





