# For Hospital Data Teams

This readme details how to use the Hospital Charge Master Data Schema

## Where should we put the data on our website

Please place your chargemaster data download under the following url on your website

https://yourhospitaldomain.com/chargemasterdata/

If you have more than one EIN (and therefore need to release multiple chargemaster data file sets) then place them under numberic directories starting from 1 like so:

https://yourhospitaldomain.com/chargemasterdata/1/

https://yourhospitaldomain.com/chargemasterdata/2/

....

https://yourhospitaldomain.com/chargemasterdata/15/

etc.


## Rational

* Should we put the data inside a zip file
No, the whole point of the MD5 files is to allow crawlers to determine if they should re-download your data. This benifit is negated if the hashes are not readily downloadable. 

* Why not JSON?

Because some of these files could have tens of thousands of rows (especially if charges are different for different NPI/CCNs etc etc)
JSON files are excellent for smaller data files, but they are nor very fault tolerant. 


* Why not Excel?

Excel requires proprietary software to run and is not an machine readable open data standard, as [per government definitions](https://project-open-data.cio.gov/open-standards/)

* Why do you require MD5 files?

It will reduce some of repeated downloads of these data files, hopefully. 
Also it is a way for others to demonstrate that a download was succesful. 
It is also best practices for data/documents that are date-stamped as part of a medico-legal record. 

* Why have the HPID field?
Currently the government only requires 'master' charge data to be released. 
However, in the future, hospitals may chose, or be required, to release prices for specific payers. 
To future proof this standard, we are adding this field.

* Why the EIN?
Because we need to be able to have a top level identifier for your hospital as an entity. Large hospitals can have multiple CCN and NPI numbers, but the EIN is the highest level identifier for a given hospital.

If you need to publish under two different EINs then you need to release two different chargemaster data files. But if you just have several NPI fields, then you can put evertything in a single chargemaster data release under one EIN. 

Contrary to popular belief EINs are not private in healthcare and are defined as part of the public data released by CMS. They should be releasing that data "real soon now". Please be careful not to accidentally release a Social Security Number in the place of an EIN, because that is private information.  

* Why not define this as a CSV Schema?
There is a [CSV Schema](http://digital-preservation.github.io/csv-schema/csv-schema-1.1.html) that we could have used. However, many of the columns in our CSV specification need to be valid codes of one type or another (CCN, NPI, HCPCS, CPT, etc etc) and it was not immediately clear how you specify "valid NPI" or "valid HCPCS" in the CSV Schema. But we would welcome this as a contribution if someone can figure out a way to do that correctly or mostly correctly.



