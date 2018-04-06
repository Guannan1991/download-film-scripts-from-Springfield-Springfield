# Download film scripts from Springfield Springfield
R codes for downloading all dialogue scripts from the famous site Springfield! Springfield! (https://www.springfieldspringfield.co.uk/)

## Before you download the code
This script relies on several packages: `rvest`, `data.table`, `stringr`, and `stringi`. Use `install.packages()` to install them if you haven't had them ready. 

The work flow of this script is simple. Since all scripts are listed in an alphabetical manner (plus 0 at the very beginning, see this https://www.springfieldspringfield.co.uk/movie_scripts.php), this script will fetch the number of pages of scripts starting with each letter (0 and A-Z) first. Then it will scrape all titles based on the page information it gets previously. Titles will be used to composite the webpage link of each script. The scripts will be fetched and saved in a designated local disk (as .txt) as a result.

## When you use it
1. Set up your working directory (where you store the scripts) first.
```
setwd("F:/your/lucky/directory")
```
2. Run the codes. The first step (fetching maximum page) is going to spend you less than one minute; the second step (fetching titles) will take more time (roughly 10 minutes); the last step (downloading scripts) will take your several hours. The time needed will vary in differnt PCs.

3. Note that some of the scripts cannot be fetch because of the irregularity of some script links. In this case the function will return an error stored in the .txt file. Among the 22,000 scripts, roughly 200 scripts can't be fetch.
> Error in open.connection(x, "rb") : HTTP error 404.

4. Sometimes the function will return error 504.
> Error in open.connection(x, “rb”) : Timeout was reached

This error happens when the website can not be openned. In this case segmenting the fetching of scripts is recommended. This could be achieved by using:
```
sapply(title_info[1:1000], get_script) #fetch 1000 scripts each time
```

TO BE CONTINUED
