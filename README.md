# Web-Crawler
The URL frontier will be a structure of front queues and back queues, as covered in class. When your crawler starts for
the first time, URL frontier will contain seed URLs as given in table 1.
The process will be multithreaded. Each thread will request a URL from frontier when required. The process of getting
data from threads while maintaining politeness and moving data from F-queues to B-queues will be done as studied in
class. Prioritizer function is given the starter notebook.
URLS that go out of frontier should go in some storage (file or in memory list).
Newly encountered URL’s will be en-queued after passing through URL filtering and Dup-URL elimination module.
For this project wait for 15 to 20 seconds after sending one request to send another request 1
After getting one URL from frontier, retrieve its content from the webserver. If you are working in python use
urllib[2] or socket[3] library for this task. If you are working in JAVA you can use similar libraries. URL (IP or
absolute) and content of the fetched page should be stored in database for next modules. You can use database of your
own choice. For example you can use Relation databases or simple XML files (your choice will affect the read/write time
in this and next modules)
3) Parse
Parse the content of the fetched page and retrieve all the URLS from it. The URLS might not be absolute URLS, so make
sure you are able to figure out the absolute URL to send to next module.

For example http://en.wikipedia.org/wiki/Main_Page has a relative link to
/wiki/Wikipedia:General_disclaimer which is the same as the absolute URL
http://en.wikipedia.org/wiki/Wikipedia:General_disclaimer

A lot of this URL links will be of .js .css or .png type. In this assignment we are only interested in HTML pages, so try to
make sure the list of URLS you send to next module is of HTML page. (&lt;!DOCTYPE html&gt;)
To parse the HTML page you can use BeautifulSoup[4] in python or jSoup[5] in JAVA
4) URL Filter
In this module you will have to filter the URLs, received from parser, that are restricted from its webserver. The restricted
page/s will be given in robot.txt file. To retrieve the robot.txt file of a website use the &lt;home page URL of
website&gt;/robots.txt
For Example: robots.txt of Wikipedia is on following URL
https://en.wikipedia.org/robots.txt

You will obtain this file in the same way as any page you retrieved in fetch module, you should be looking for User-
agent: * in this file to see which page/s are allowed for crawlers and which ones are not. More details on how to read
robot.txt is at [1].
Store a local copy of these files for each site, so that you don’t have to fetch it every time.
5) Duplicate URL Elimination
After filtering restricted URLS, check if the newly extracted URLs are already crawled or not. The URLS that pass this
test should be added to the frontier (make sure the URLS in frontier are also distinct).
6) Stopping the process
You can stop the process based on number of URL, for example if you have crawler 1000 URLS then you can stop.
