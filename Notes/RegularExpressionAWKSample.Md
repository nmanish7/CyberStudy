# Regular Expression Using AWK

## IPv4 Address:
#### Regular Expression 1:
	'/(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/'
> ##### Sample:
    awk '/(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/' filename.txt
	
  
#### Regular Expression 2:
	'/(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/'

> #####  Sample:
    awk '/(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/' filename.txt
	

#### Get only Expression with Blank Line:
	awk '{match($0, /(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/,a)}' filename.txt

#### Remove Blank Line and Get only Expression:
	awk '{match($0, /(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/,a)};  length(a)>1{print(a[0])}' filename.txt
#### Remove Blank Line and Get only Expression with Multiple Occurrence in Single Line :
	awk '{split($0,t,/(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?\.){3}(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)/, a)} length(a)>0{for (i=1;i<=length(a); i++) print a[i]}' filename.txt


## MAC Address:

#### Regular Expression :
	'/([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}/'
	
> ##### Sample:
    awk '/([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}/' filename.txt

#### Get only Expression with Blank Line:
	awk '{match($0,/([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}/, a)}' filename.txt

#### Remove Blank Line and Get only Expression:
	awk '{match($0,/([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}/, a)}; length(a)>1{print a[0]}' filename.txt

#### Remove Blank Line and Get only Expression with Multiple Occurrence in Single Line :
	awk '{split($0,t,/([[:xdigit:]]{1,2}:){5}[[:xdigit:]]{1,2}/, a)} length(a)>0{for (i=1;i<=length(a); i++) print a[i]}' filename.txt
