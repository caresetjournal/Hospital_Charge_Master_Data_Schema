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


## Rationale

### What counts as "Machine Readable" according to CMS?
The CMS regulation specifically mentions the PDF does not count as machine readable. However, Machine Readable is defined by The Office of Management and Budgetment (OMB) [OMB Circular A-11, Part 6](https://obamawhitehouse.archives.gov/sites/default/files/omb/assets/a11_current_year/s200.pdf) as:

```
Machine Readable Format. Format in a standard computer language (not English text) that can be read
automatically by a web browser or computer system. (e.g., xml). Traditional word processing documents,
hypertext markup language (HTML) and portable document format (PDF) files are easily read by humans
but typically are difficult for machines to interpret. Other formats such as extensible markup language
(XML), (JSON), or spreadsheets with header columns that can be exported as comma separated values
(CSV) are machine readable formats. It is possible to make traditional word processing documents and
other formats machine readable but the documents must include enhanced structural elements. 
```

This specifically states that spreadsheets only count when they can be converted to CSV in order to count as machine readable. We simply require this demonstration upfront. 

This parallels information from the Federal CIO [Project Open Data website](https://project-open-data.cio.gov/principles/), which [specifically lists acceptable open standards](https://project-open-data.cio.gov/open-standards/). This notes that standards that require proprietary software are not open standards. 

### Should we put the data inside a zip file?

No, the whole point of the MD5 files is to allow crawlers to determine if they should re-download your data. This benifit is negated if the hashes are not readily downloadable. 

### Why not JSON?

Because some of these files could have tens of thousands of rows (especially if charges are different for different NPI/CCNs etc etc)
JSON files are excellent for smaller data files, but they are nor very fault tolerant. 

### Why not Excel?

Excel requires proprietary software to run and is not an machine readable open data standard. See the question on what counts as Machine Readable. 

### Why do you require MD5 files?

It will reduce some of repeated downloads of these data files, hopefully. 
Also it is a way for others to demonstrate that a download was succesful. 
It is also best practices for data/documents that are date-stamped as part of a medico-legal record. 

### Why have the HPID field?

Currently the government only requires 'master' charge data to be released. 
However, in the future, hospitals may chose, or be required, to release prices for specific payers. 
To future proof this standard, we are adding this field.

### Why the EIN?

Because we need to be able to have a top level identifier for your hospital as an entity. Large hospitals can have multiple CCN and NPI numbers, but the EIN is the highest level identifier for a given hospital.

If you need to publish under two different EINs then you need to release two different chargemaster data files. But if you just have several NPI fields, then you can put evertything in a single chargemaster data release under one EIN. 

Contrary to popular belief EINs are not private in healthcare and are defined as part of the public data released by CMS. They should be releasing that data "real soon now". Please be careful not to accidentally release a Social Security Number in the place of an EIN, because that is private information.  

### Why not define this as a CSV Schema?

There is a [CSV Schema](http://digital-preservation.github.io/csv-schema/csv-schema-1.1.html) that we could have used. However, many of the columns in our CSV specification need to be valid codes of one type or another (CCN, NPI, HCPCS, CPT, etc etc) and it was not immediately clear how you specify "valid NPI" or "valid HCPCS" in the CSV Schema. But we would welcome this as a contribution if someone can figure out a way to do that correctly or mostly correctly.

### Can we modify this schema?

Yes, BUT please do not without a good reason. Instead, please submit issues or pull requests to this project so that we can fix these data formats and schemas to be more generic and work for more people. 

If you really need to change it, please remove the name "DocGraph" or "hospitalpricedata.org" from the ReadMe.
Your use of those Trademark's are only allowed if you are using a version of this data schema and format.

We may also ask you to stop using this readme, if your data does not properly conform to this data standard. 
Please expect more formalization of the legalize required to facilitate this shortly. 

### Can we release another readme along side the DocGraph Readme?

Of course, please do!


### Where to get help with this schema

Start by submitting an issue here: https://github.com/docgraph/Hospital_Charge_Master_Data_Schema/issues
