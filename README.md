# KatRevive

## About
KatRevive is a project to allow revival of the Kickass Torrents API dumps.

There was originally a site at [katrevive.xyz](https://katrevive.xyz/), and there still is. But due to DMCA complaints, I have taken it down. I am not trying to start a torrent site, only allowing people to get torrents that they wanted.

Dumps for your testing available here:  
*Hourly Dump:*  
http://www.filedropper.com/hourlydumptxt  
http://www.speedyshare.com/uqXpq/hourlydump.txt.gz  
http://www.multiupfile.com/f/eec39cb8  
*Daily Dump:*  
http://www.speedyshare.com/JRjCR/dailydump.txt.gz  
http://www.filehosting.org/file/details/589629/dailydump.txt.gz  
http://www.multiupfile.com/f/dfb816fe29  

## Files
#### create_db.sql
This is the MySQL code needed to generate the database. By default, the username is *root* and the password is blank.  
To use this, copy it into a MySQL terminal instance, or copy it into PHPMyAdmin or your respective MySQL manager.  

#### index.php
This is the root file, and the file that you will use to view torrents. You can access other torrents by using the `GET` parameter of `s`.  
This layout shows 5 columns.
- Verified: Displayed as a star
- Hash: The info hash for that specific torrent, this is unique in the db
- Name: The name of the torrent
- Category: What main category it was in on KAT, the DB also contains the `category_id` which allows for subcategories as well
- URLs: The torrent file link, and the magnet link

#### install.php
The installer file. Just run this, and select an import type.  
*Please note, these will need to be downloaded beforehand and added to the `import_lists` folder.*  

There are 2 example [import files](https://github.com/PXgamer/KatRevive/tree/master/import_lists) with the same torrent, to demonstrate. The actual imports can be downloaded elsewhere.

Just select the type you want to import, and hit the import button.

#### import_db_list.php
This shouldn't be accessed from anywhere, it will automatically be called by using the `install.php` file.  
Please don't run this more than once, and please note that it **will** be slow when installing.

#### api/index.php
The API, will create a JSON formatted array of torrents. Is limited to 20 at a time, and can be browsed using the `GET` parameter `s`.

#### gen_sql_import.php
Used to generate MySQL imports of any dump.

#### favicon.png
Just ignore this, it's the favicon to load when using the site in a browser.

#### funcs.php
No need to touch this file, unless changing the db details. It's self contained and used in the other files.

## Instructions
Clone to your local or remote server using `git clone https://github.com/PXgamer/KatRevive.git`.  

I have set this up to use MySQL with a username of `root` and no password. This can be changed in the `funcs.php` file, or during the install process.   

Next, copy the code out of the `create_db.sql` file and run this in your MySQL administration tool. For example, in PHPMyAdmin, navigate to the SQL tab for the database, and paste it there. Then run this. 

Copy your `hourlydump.txt` and/or `dailydump.txt` file(s) to the `import_lists` folder.  

Open the `install.php` file in a browser, and check that no errors appear, if not, select the file you'd like to install. Then click `import`.  

This can take a while depending on the number of torrents your file contains, I tested with 3 Million+ torrents in the data dump I had, which took roughly 5 minutes, alternatively you can generate a MySQL import file using the `gen_sql_import.php` file.  

## The Database/Table
The database is called `kat_db` by default and contains a single table `t_collection`. This table contains 10 columns, as follows:  
- torrent_info_hash
- torrent_name
- torrent_category
- torrent_info_url
- torrent_download_url
- size
- category_id
- files_count
- upload_date
- verified

## Other Features
The API: https://github.com/PXgamer/KatRevive/tree/master/api  
Main Search: https://github.com/PXgamer/KatRevive/tree/master/search  
Hash Searching: https://github.com/PXgamer/KatRevive/tree/master/hash  
MySQL Import Generation: https://github.com/PXgamer/KatRevive/tree/master/sql_imports  

## Gallery
#### Main Page
![Index Image](https://pximg.xyz/images/ee2b0357f515d530c7c46acc71d6d287.png)  
#### Individual Torrent Pages
![Individual Torrent Pages](https://pximg.xyz/images/fd181e06a5f5d4de7f0d6199e1a22c35.png)  
#### Main Search System
![Main Search](https://pximg.xyz/images/172911e84f10ddd93d3e41c02373bff6.png)  
#### API Results
![API Results](https://pximg.xyz/images/4dd5c7daf945c110945dcda6fad03dd9.png)  
#### KAT Header Theme
![KAT Header Theme](https://pximg.xyz/images/5bc7939c5fd0e74703b7b7e289dcab2e.png)
