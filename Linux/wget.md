# wget

## Usage

```sh
wget [option] url
```

### Options

* `-O` `--output-file` specify outfile
* `-o` `-olog` logfile
* `-c` `--continue`
* `-r` `--recursive` turn on recursive
* `-l` `--level=depth` specify recursion maximum depth level
* `-m` `--mirror`
* `-k` `--convert-links`
* `-p` `--page-requisites`
* `-i` `--input-file`
* `-b` `--background`
* `-t` `--tries`

### Examples

* Find broken links
    ```sh
    wget -o wget.log -r -l 10 --spider http://example.com
    ```

* Mirror a website
    ```sh
    wget -mk http://example.com
    wget -mkp http://example.com
    ```

* Reject Certain File Types while Downloading
    ```sh
    wget --reject=gif WEBSITE-TO-BE-DOWNLOADED
    ```

* Quit Downloading When it Exceeds Certain Size
    ```sh
    wget -Q5m -i FILE-WHICH-HAS-URLS
    ```

* Download Only Certain File Types
    ```sh
    wget -r -A "*.pdf" http://url-to-webpage-with-pdfs/
    ```

## Reference

* [Linux and Unix wget command tutorial with examples](https://shapeshed.com/unix-wget/)
* [The Ultimate Wget Download Guide With 15 Awesome Examples](https://www.thegeekstuff.com/2009/09/the-ultimate-wget-download-guide-with-15-awesome-examples/)
