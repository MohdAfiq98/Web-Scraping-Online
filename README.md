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

As for the extraction process, we are interested in extracting:
1. listing id
2. list_title
3. price
4. property_type
5. date
6. agent_name
7. agency_name

