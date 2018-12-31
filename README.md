# Hospital Charge Master Data Schema
Proposed data formats and best practices for the release of Hospital Charge Master Data.

We want to keep this simple, so we are making a single short document.

You can read more about the effort to develop this document at [hospitalpricedata.org](http://hospitalpricedata.org/)

## Core Files

There are several files that should be released as part of the Hospital Chargemaster data release:
* Chargemaster.csv - The actual Chargemaster data
* Chargemaster.csv.MD5 - an MD5 file that should be updated everytime the Chargemaster file is updated
* Chargemaster.metadata.json - JSON metadata for the Chargemaster 
* Chargemaster.metadata.json.MD5 - an MD5 file that should be updated everytime the Chargemaster file updates

### Chargemaster.csv
The Hospital ChargeMaster data will be released as a Comma Delimited (CSV) in accordance with [IETF RFC4180](https://tools.ietf.org/html/rfc4180) with the following columns structure.

* CCN - CCN of the hospital (allows for one file to detail several hospitals or sub-facilities)
* NPI - NPI of the hospital (allows for one file to detail several hospitals or sub-facilities)
* HPID - "0" if this is the root ChargeMaster, otherwise this is the HPID of the payor 
* Charge_Code - The internally specified Charge Code
* Charge_Code_Description - A short clinical description of the charge without abbreviations whenever possible
* Code_Source - HCPCS/CPT/ICD Procedure/DRG 
* Code_Version - CPT is currently '4' ICD is currently '10' etc etc.
* Code - The actual HCPCS or CPT or DRG etc etc
* Price - The dollars and cents charged, without commas.. so 1500.00 not "1,500.00"
* Price_Data - The Date this price was released in MM-DD-YYYY format (this is USA, after all)



### Chargemaster.metadata.json

A JSON formatted file with the following contents:

* Hospital_Name - The name of the hospital
* Hospital_EIN - The EIN of the hospital
* Last_Update_DateTime - The [correct JSON DateTime](https://stackoverflow.com/a/15952652/144364) of the ChargeMasters last release
* Hospital_CCN_List - a JSON List of CCN numbers of the hospitals included in the file
* Hospital_NPI_List - a JSON List of the NPI numbers of the hospitals included in the file



## Data Download Location

Please place your chargemaster data download under the following url on your website

https://yourhospitaldomain.com/chargemasterdata/

If you have more than one EIN (and therefore need to release multiple chargemaster data file sets) then place them under numberic directories starting from 1 like so:

https://yourhospitaldomain.com/chargemasterdata/1/

https://yourhospitaldomain.com/chargemasterdata/2/

....

https://yourhospitaldomain.com/chargemasterdata/15/

etc.


## Rational

* Why not JSON?

* Why not Excel?

* Why do you require MD5 files?

* Why have the HPID field?

* Why the EIN?
Because we need to be able to have a top level identifier for your hospital as an entity. Large hospitals can have multiple CCN and NPI numbers, but the EIN is the highest level identifier for a given hospital.

If you need to publish under two different EINs then you need to release two different chargemaster data files. But if you just have several NPI fields, then you can put evertything in a single chargemaster data release under one EIN. 

Contrary to popular belief EINs are not private in healthcare and are defined as part of the public data released by CMS. They should be releasing that data "real soon now". Please be careful not to accidentally release a Social Security Number in the place of an EIN, because that is private information.  



* Why not define this as a CSV Schema?
There is a [CSV Schema](http://digital-preservation.github.io/csv-schema/csv-schema-1.1.html) that we could have used. However, many of the columns in our CSV specification need to be valid codes of one type or another (CCN, NPI, HCPCS, CPT, etc etc) and it was not immediately clear how you specify "valid NPI" or "valid HCPCS" in the CSV Schema. But we would welcome this as a contribution if someone can figure out a way to do that correctly or mostly correctly.




