# Download film scripts from Springfield Springfield
R codes for downloading all dialogue scripts from the famous site Springfield! Springfield! (https://www.springfieldspringfield.co.uk/)

## Before you download the code
This script relies on several packages: `rvest`, `data.table`, `stringr`, and `stringi`. Use `install.packages()` to install them if you haven't had them ready. 

The work flow of this script is simple. Since all scripts are listed in an alphabetical manner (plus 0 at the very beginning, see this https://www.springfieldspringfield.co.uk/movie_scripts.php), this script will first fetch the number of webpages of scripts starting with a certain letter (0 and A-Z). Then it will retrieve all titles based on the page information. Titles will be used to composite the webpage link of each script. The scripts will be fetched and saved in a designated local disk (as `.txt`) as a result.

## When you use it
1. Set up your working directory (where you store the scripts) first.
```
setwd("F:/your/lucky/directory")
```
2. Run the codes. The first step (fetching maximum page) is going to spend you less than one minute; the second step (fetching titles) will take more time (roughly 10 minutes); the last step (downloading scripts) will take your several hours. The time needed varies in differnt settings.

3. Note that some of the scripts will not be fetched because of the irregularity of their links. In this case the function will return an error message stored in the `.txt` file. Roughly 200 scripts are not fetched among all ≈ 22,000 scripts,
> Error in open.connection(x, "rb") : HTTP error 404.

4. Sometimes the function will return this error:
> Error in open.connection(x, “rb”) : Timeout was reached

This error happens when the website can not be openned. Hence segmenting the fetching process is recommended. This could be achieved by using the following line repeatly (around Line 95) until you reach the end of `title_info`.
```
sapply(title_info[1:1000], get_script) #fetch the first 1000 scripts
```
