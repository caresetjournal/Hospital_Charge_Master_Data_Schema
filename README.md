# Hospital Charge Master Data Schema
Proposed data formats and best practices for the release of Hospital Charge Master Data.

We want to keep this simple, so we are making a single short document

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



