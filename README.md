# Web Pro Migration

Selenium project using python for web scraping anda data filler

> Please follow

#### 1. PIP install requirement.txt
```sh
pip install ./Config/requirement.txt
```

#### 2. Setup Config/config.ini
Change the <*webpro_*> with your credential
```sh
username=<webpro_username>
password=<webpro_password>
webProUrl=<webpro_url>
```

#### 3. RUN
```sh
python .\webProDataFiller.py
```

## Databases

Used to controll migration progress. 
- To Reset DB just delete the DB file.
- To Resume / reRun Progress, change "Status" column for progress you want to reRun to "Pending"

| Migration Progress | Status |
| ------ | ------ |
| Web Pro migration | In Progress / Pending / Error / Finished |
| Tag Set migration | In Progress / Pending / Error / Finished |
| Asset File migration | In Progress / Pending / Error / Finished |
| Category migration | In Progress / Pending / Error / Finished |
| Content File CSV migration | In Progress / Pending / Error / Finished |
| Publish Content approval | In Progress / Pending / Error / Finished |
| Group Config setup | In Progress / Pending / Error / Finished |

## Features
- tearUpMethod() - method to start up browser and login to Web Pro
- webProCreateTagSet() - method to migrate Tag Set
- webProUploadFileLibrary() - method to upload File Library
- webProCreateCategory() - method to migrate Category
- webProUploadCsvContent() - method to migrate CSV Content
- webProPublishContent() - method to Publish Content
- webProGroupConfig() - method to make a Group Config
- tearDownMethod() - method to close browser

If you want to skip some migration step or progress just find "runMigration" function and comment the code that you need to skip. Eg.
```sh
def runMigration(self, progress=""):
    if progress == self.progress[1]:
      self.webProCreateTagSet()
    elif progress == self.progress[2]:
      self.webProUploadFileLibrary()
    # elif progress == self.progress[3]:
    #   self.webProCreateCategory()
    elif progress == self.progress[4]:
      self.webProUploadCsvContent()
    elif progress == self.progress[5]:
      self.webProPublishContent()
    elif progress == self.progress[6]:
      self.webProGroupConfig()
```
Note: *If you use this method, better yo delete the DB file before you do clean migration.*