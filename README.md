# ManchesterNH-Archives-ExhibitData ReadMe

### FILES 

This repository contains the following files:
* [MWW-Image_Item-Level_Metadata_#.#.#.csv](https://github.com/anabelmm/ManchesterNH-Archives-ExhibitData/blob/main/MWW-Images_Item-Level_Metadata_1.0.1.csv)
* [MWW-Images_Item-Level_Metadata_NORMALIZED_#.#.#.csv](https://github.com/anabelmm/ManchesterNH-Archives-ExhibitData/blob/main/MWW-Images_Item-Level_Metadata_NORMALIZED_1.0.1.csv)
* [MWW-Images_Collection-Metadata_#.#.#.csv](https://github.com/anabelmm/ManchesterNH-Archives-ExhibitData/blob/main/MWW-Images_Collection-Metadata_1.0.2.csv)
* [MWW-Images_Data-Dictionary_#.#.#.csv](https://github.com/anabelmm/ManchesterNH-Archives-ExhibitData/blob/main/MWW-Images_Data-Dictionary_1.2.0.csv)


### NAMING CONVENTIONS
Naming Convention follows the following format: Short-Exhibit-Title_File-Description_Semantic.Versioning.Here.csv 

Semantic versioning: Versions will be tracked in a #.#.# format, starting with 1.0.0. Whenever data is normalized, +1 to the third #. If data is updated to fix mistakes or add analysis, +1 to the second #. If new data is collected/produced, +1 to the first #. 

NOTE--THIS README FILE MUST BE UPDATED WITH A CORRECTED LINK EVERY TIME A NEW FILE VERSION IS CREATED, OR THE HYPERLINK WILL GIVE YOU A 404 ERROR. 

### BACKUPS
It is recommended that a local copy of the files be downloaded/updated every time new data is added. A backup of version 1.0.0 is available on [Google Drive](https://docs.google.com/spreadsheets/d/1TJmeKkdVtE6OmK8UkkCG5Y88InfS7b3tuzvm3_nHnrs/edit?usp=sharing).


# Contact
### REPOSITORY OWNER: 
Anabel Moreno-Mendez
- School Email: anabelmm@uw.edu 
- Work Email: amoreno@manchesternh.gov 

### ASSOCIATED INSTITUTION:
University of Washington Information School
-1851 NE Grant Ln,
Seattle, WA 98105



# Background
This project consists of exhibit data from the City of Manchester, New Hampshire's Office of the City Clerk Digital Archives, collected to fulfill the "Data Protocol" assignment for the repository owner's "LIS 545: Data Curation I" course at University of Washington Information School during Winter 2022.  The author hopes that this will be the first step in a longer term quest to assist the City in curating its digital collections (which can be found here: https://www.manchesternh.gov/Departments/City-Clerk/Municipal-Archives-and-Records/Online-Exhibits).

This repository contains sample data from the City of Manchester's "Water Works Department Photograph Collection, 1886-1993" online exhibit, which is currently archived in the Manchester City Archives' Flickr account: https://www.flickr.com/photos/manchesternharchives/albums/72157689724451670

Intended audience: city historians, city archivist(s) and their volunteers

Mission: To create a dataset containing item-level metadata for each data object within the digital exhibit, so that historians and archivists are easily able to search, browse, and access both the digital items within the exhibit and all associated metadata.  

# Methodology and Data
### PROCESSING RAW DATA

The intial raw data for the project consists of a sample of nine photographs from the Manchester Water Works Department (MWW) collection referenced above. It is important to note that the City Archives have stated "Item-Level descriptions for images have not yet been created," so a significant amount of leg work was required in order to establish the datasets in this repository.  There was some metadata available directly from the Flickr gallery (variable fields: "Owner",	"Album",	"Uploaded",	"Image_Name",	"Caption",	"URL", and	"Text in Image"), and this data was pulled for each data object and compiled into the dataset labelled "MWW-Image_Item-Level_Metadata_#.#.#.csv" to begin the process. 

The author contacted the City Archivist via email and confirmed that no item-level metadata were kept internally/ offline, however, she was able to obtain some metadata associated with the MWW Dept. Phot Col., 1886-1993 exhibit by way of an unpublished collection guide (unpublished as it was incomplete). Using the incomplete guide and available information from the website, a table was created containing metadata for the collection, also conforming to the DCAT-US Schema (note: variable definitions for DCAT-US Schema can be found here: https://resources.data.gov/resources/dcat-us/). This dataset is labelled "MWW-Images_CollectionMetadata_#.#.#.csv" and was a key point of reference, as the author was later able to pull information from it to fill in missing item-level metadata. 

The author then compiled and normalized item-level metadata for each of the nine sample photographs from the raw data.
 


### NORMALIZATION
Normalized data is contained in the document labelled "MWW-Images_Item-Level_Metadata_NORMALIZED_#.#.#.csv 

In the normalized file, we observe the following: 
* No changes to the "Owner" variable
* Variables "Publication_Date", "Image_Name", "Exhibit", "Image_Text" and "Identifier" were modified (renamed and/or had data normalized)
* New variables "Creator",	"Creation_Date",	"Publisher", "Contributor",	"Coverage",	"Accession",	"Collection",	"Item_Number", and	"Keywords" were created
* Variable "Caption" was completely eliminated after the addition of the aforementioned variables

Justification:
- Justification for the renaming of any variables is noted in the data dictionary below. Where the justification for renaming simply states "normalized," the variable name change happened for formatting reasons (to avoid spaces for example) or as a common best practic (stating "identifier" instead of "URL"). 
- The normalized "Image_Name" variable consists of a completely revamped file naming convention: CreatorInitials_Exhibit_Title_"Collection"__"Item_Number"
- Variables "Collection", "Accession", and "Publisher" were parsed from the "Caption" variable in the raw data. 
- "Creator" variable was logically deduced from the title of the exhibits. Future exhibits added to the repository may have different creators. 
- "Creation Date" variable was parsed from the "Text in Image" variable. Unfortunately, most photos did not have the date available.
- Variables "Contributor", "Coverage", and "Keywords" were obtained by referencing the Collection metadata documentation. 
- The "Item_Number" variable was more nuanced. After referencing the draft guide provided by the archivist, it was concluded that the image number, or the item number, was the latter portion of the original "Image_Name" formatting. The "Item_Number" variable was therefore parsed from the OG "Image_Name" variable. 


### DATA DICTIONARY

| Variable          | Variable Name    | Variable Type | Allowed Values   | Definition                                                                                                                                                                                                                                                                                                                     |
|-------------------|------------------|---------------|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Owner             | Owner            | String        | -                | Indicates which account holder is the owner of the data object                                                                                                                                                                                                                                                                 |
| Publisher         | Publisher        | String        | -                | Indicates who was responsible for making the data object digitally   available to the public                                                                                                                                                                                                                                   |
| Album             | Album            | String        | -                | Indicates the title of the Flickr album in which the item is being   stored.                                                                                                                                                                                                                                                   |
| Exhibit           | Exhibit          | String        | -                | Normalized equivalent to "Album" variable -renamed for   consistency across digital exhibits made available by the City of Manchester   through various platforms                                                                                                                                                              |
| Uploaded          | Uploaded         | Date          | Month D, YYYY    | Date that the digital object was digitally archived, or uploaded to the   online repository                                                                                                                                                                                                                                    |
| Publication Date  | Publication_Date | Date          | YYYY-MM-DD       | Normalized equivalent to "Uploaded" variable-renamed for   consistency with "Publisher" variable. Date format has been   normalized to standard YYYY-MM-DD format                                                                                                                                                              |
| Image name        | Image_Name       | String        | -                | The file name of the image                                                                                                                                                                                                                                                                                                     |
| Caption           | Caption          | String        | -                | The description that is associated with the image inside the Flickr   album, contains metadata information                                                                                                                                                                                                                     |
| URL               | URL              | String        | -                | Direct link to the image -takes you to the Flickr page where you can view   the file                                                                                                                                                                                                                                           |
| Identifier (URI)  | Identifier       | String        | -                | Normalized equivalent to "URL" variable                                                                                                                                                                                                                                                                                        |
| Text in Image     | Text in Image    | String        | -                | Human readable text that is visible within an image, transcribed for   convenience                                                                                                                                                                                                                                             |
| Image Text        | Image_Text       | String        | -                | Normalized equivalent to "Text in Image" variable                                                                                                                                                                                                                                                                              |
| Collection Number | Collection       | String        | -                | Manchester City Archives internal identifier used to assist in locating   and diferrentiating between collection files. Number prior to the period   corresponds to an pre-assigned collection group code while the number after   the period is sequential for that group (1st item is XXX.001, 2nd item is   XXX.002, etc).  |
| Accession Number  | Accession        | String        | -                | Formatted as the year archived, followed by a period, then the item group   number for that year: YYYY.### (e.g. the 4th collection received and archived   in 2022 would have the accession number 2022.004)                                                                                                                  |
| Image Number      | Item_Number     | String        | -                | Sequentially assigned item-level number within the collection. Formatted   as five digits ##### (e.g. 00029, 00030, 00031, etc.)                                                                                                                                                                                               |                                        |
| Creator           | Creator          | String        | -                | Refers to the individuals, departments, or organizations who created the   original document(s) being archived                                                                                                                                                                                                                 |
| Creation Date     | Creation_Date    | Date          | YYYY-MM-DD       | The date which the original document(s) was produced                                                                                                                                                                                                                                                                           |
| Contributor       | Contributor      | String        | -                | The name and email address of individual(s) responsible for archiving the   document(s)                                                                                                                                                                                                                                        |
| Coverage          | Coverage         | String        | -                | Geographic location(s) to which the document(s) correspond                                                                                                                                                                                                                                                                     |
| Keywords          | Keywords         | String        | Array of Strings | Subject tag(s) associated with the topic of the data object, which assist   users in searching and browsing                                                                                                                                                                                                                    |


### METADATA
Schema Used for this repository: DCAT-US Schema v.1.1 (Project Open Data Metadata Schema)
