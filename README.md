# Hospital Charge Master Data Schema
This document details the machine readable data structure of a hospital chargemaster data release, in compliance with CMS policy. 

* This ReadMe can also be found on the [Hospital Charge Master Data Schema Github Project](https://github.com/docgraph/Hospital_Charge_Master_Data_Schema)
* If you would like more help interpreting this data, please visit [hospitalpricedata.org](http://hospitalpricedata.org/)
* If you would like to know more about what a Chargemaster is, [Wikipedia has an article on Chargemasters](https://en.wikipedia.org/wiki/Chargemaster)
 

## Core Files

There are several files that should be included released as part of this Hospital Chargemaster data release:

* Chargemaster.README.md - A readme (possibly this one) that details the data structures found in the other files.
* Chargemaster.csv - The actual Chargemaster data
* Chargemaster.csv.MD5 - an MD5 file that should be updated everytime the Chargemaster file is updated
* Chargemaster.metadata.json - JSON metadata for the Chargemaster 
* Chargemaster.metadata.json.MD5 - an MD5 file that should be updated everytime the Chargemaster file updates

### Chargemaster.csv
The Hospital ChargeMaster data will be released as a Comma Delimited (CSV) in accordance with [IETF RFC4180](https://tools.ietf.org/html/rfc4180) with the following columns structure:

* CCN - CCN of the hospital (allows for one file to detail several hospitals or sub-facilities)
* NPI - NPI of the hospital (allows for one file to detail several hospitals or sub-facilities)
* HPID - "master" if this is the Charge data is the "master", otherwise this is the HPID of the respective payer 
* Charge_Code - The internally specified Charge Code
* Charge_Code_Description - A short clinical description of the charge without abbreviations whenever possible
* Code_Source - HCPCS/CPT/ICD Procedure/DRG 
* Code_Version - CPT is currently '4' ICD is currently '10' etc etc.
* Code - The actual HCPCS or CPT or DRG etc etc
* Price - The dollars and cents charged, without commas.. so 1500.00 not "1,500.00"
* Price_Data - The Date this price was released in MM-DD-YYYY format (this is USA, after all)

### Chargemaster.csv.hash.SHA and Chargemaster.metadata.json.hash.SHA

These files are hashes of the downloaded files so that you can be sure that what you downloaded is the same as what the hospital released. 

To verify them run a command line shasum program to create a new hash. Something like 

```
shasum Chargemaster.csv 
shasum Chargemaster.metadata.json
```

should work. If you are going to build a spider to repeatidly check to see if chargemaster files have changes


### Chargemaster.metadata.json

A JSON formatted file with the following contents:

* Hospital_Name - The name of the hospital
* Hospital_EIN - The EIN of the hospital
* Data_Contact_Name - The first and last name of the person who manages the release of the chargemaster data
* Data_Contact_Email - The email to contact regarding problems with the chargemaster data
* Last_Update_DateTime - The [correct JSON DateTime](https://stackoverflow.com/a/15952652/144364) of the ChargeMasters last release
* Hospital_CCN_List - a JSON List of CCN numbers of the hospitals included in the file
* Hospital_NPI_List - a JSON List of the NPI numbers of the hospitals included in the file


## More information 
If you are hospital data administrator and you would like to use this data format to release your own data, please look here
[For Hospital Data Teams](https://github.com/docgraph/Hospital_Charge_Master_Data_Schema/blob/master/ForHospitalDataTeams.md)


