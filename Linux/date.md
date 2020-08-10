
# date

## Syntax

    date [OPTION]... [+FORMAT]
    date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

## Examples

### no option

```sh
date
Thu 27 Feb 2020 10:05:10 AM CST
date +%c
Thu 27 Feb 2020 10:05:14 AM CST
```

### transform to GMT/UTC+0

```sh
date -u
Thu 27 Feb 2020 02:07:01 AM UTC
```

### `--date` or `-d`

```sh
date --date="now"
Thu 27 Feb 2020 10:14:03 AM CST

date --date="2020-01-01"
Wed 01 Jan 2020 12:00:00 AM CST

date --date="2 year ago"
Tue 27 Feb 2018 10:18:01 AM CST

date --date="5 sec ago"
Thu 27 Feb 2020 10:18:05 AM CST

date --date="yesterday"
Wed 26 Feb 2020 10:18:19 AM CST

date --date="2 month ago"
Fri 27 Dec 2019 10:18:32 AM CST

date --date="10 day ago"
Mon 17 Feb 2020 10:18:42 AM CST

date --date="next tue"
Tue 03 Mar 2020 12:00:00 AM CST

date --date="2 day"
Sat 29 Feb 2020 10:18:58 AM CST

date --date="tomorrow"
Fri 28 Feb 2020 10:19:06 AM CST

date --date="1 year"
Sat 27 Feb 2021 10:19:13 AM CST
```

### Set system datetime

```sh
date --set="Tue Nov 13 15:23:34 PDT 2018"
```

### Read date in file

```sh
date --file=filename.txt
```

### Display the last modified timestamp of a file

```sh
date -r filename.txt
Sat 15 Feb 2020 01:23:12 PM CST

date -r filename.txt +%s
1581744192

date -r filename.txt +%Y-%m-%d
2020-02-15
```

### Format

```sh
date +%D
02/27/20

date "+%D %T"
02/27/20 10:29:55

date "+%Y-%m-%d"
2020-02-27

date "+%Y/%m/%d"
2020/02/27

date "+%A %B %d %T %y"
Thursday February 27 10:30:24 20
```

## Transform

Convert a specific date to the Unix timestamp format:

```sh
date -d "2018-09-01 00:00" +%s --utc
1535760000
```
