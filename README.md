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

* CCN of the hospital (allows for one file to detail several hospitals or sub-facilities)
* NPI of the hospital (allows for one file to detail several hospitals or sub-facilities)
* HPID - "0" if this is the root ChargeMaster, otherwise this is the HPID of the payor 
* 




## CSV Data Format

## Data Download Location

## Rational

* Why not JSON?

* Why not Excel?

* Why do you require MD5 files?

* Why have the HPID field?

* Why not define this as a CSV Schema?
There is a [CSV Schema](http://digital-preservation.github.io/csv-schema/csv-schema-1.1.html) that we could have used. However, many of the columns in our CSV specification need to be valid codes of one type or another (CCN, NPI, HCPCS, CPT, etc etc) and it was not immediately clear how you specify "valid NPI" or "valid HCPCS" in the CSV Schema. But we would welcome this as a contribution if someone can figure out a way to do that correctly or mostly correctly.




