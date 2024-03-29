# mdt-texts
DHARMA textual metadata

**Tooltip with explation at each field.**

## Block Resource Management
|ELEMENT|DISPLAY IN EDITOR|
|:-----:|:-----:|
|`<resourceManagement>`| Block title => Medatata Management |
|`<resourceID digitalID=""/>`|No display|
|`<metadataOrigin>`|optional field|
|`<metadataEditor>`| block title => metadata edition|
|<creation who="" when=""/>| 2 mandatory fields who and when, child of block metadata edition, may be repeated so +|
|`<metadataContribution>`|block => Revision History/Modification|
|`<change who="" when="" status="">`|4 fiels who (Ids project), when, status (closed list:draft, candidate, approved, published) and free text mandatory, for each a new version is mandatory. Existing fields should be displayed as list|
|`<project>`|DHARMA - not editable - Preedited|
|`<corpus>`|closed list- mandatory|
|`<metadataRights target=""/> `|CC O  - not editable|

## Bloc texts
|ELEMENT|DISPLAY IN EDITOR|
|:-----:|:-----:|
|`<textDescription>`| block => Text Description |
|`<textID idno=""/>`|field- mandatory |
|`<alternativeID>`| field-optional, eventual control over string|
|`<textDesignation>`| text field - mandatory|
|`<alternativeDesignation>`|text field - optional - may be repeated|
|`<textType value=""/>`|closed list - mandatory - may be repeated with symbol|
|`<linesNumber></linesNumber>`| field mandatory - content type number|
|`<textLanguage value=""/>`| mandatory closed list-- may be repeated with symbol|
|`<textScript value=""/>`| mandatory closed list-- may be repeated with symbol|
|date `textDate`|block|
|`<dateRegnalYear>`|1 line with 5 fields free text -- optional with titles: ruler, year, month, fornight and day. One occurence + field commentary free text optional => to be display with symbol + |
|`<date calendar="">`| 1 line with 4 fields free text for year, month, fornight and day and 1 closed list for calendar + field commentary free text optional  => to be display with symbol +. One occurence to several occurences|
|`<dateJovianCycle>`|1 line with 4 fields free text -- optional with titles: cycleName, month, fornight and day. One occurence + field commentary free text optional => to be display with symbol + |
|`<origDate notBefore="" notAfter="" when="" precision="" evidence="" datingMethod=""></origDate><!-- equivalence of the date according to the occidental calendar -->`|1 line notBefore and notAfter OR when. mandatory. + precision closed list mandatory + evidence closed list mandatory for one value; one to several occurences BUT if several each entry must different + datingMethod fixed= gregorian + field commentary free text optional => to be display with symbol + |
|text Filiation|optional block|
|`<duplicateTextID><textId/><corpus/><ref/></duplicateTextID>`|3 fields: Id in free text + corpus in free text mandatory if field ID added + url/reference free text mandatory if field ID added - all the block can be repeated|
|`<reissue><textReissue value=""/><reissueTextID idno=""/><reissueDate when=""/></reissue>`|3 fields: TextReissue tick box + reissueTextID mandatory if textReissue ticked free text field+ reissueDate mandatory if textReissue ticked free text field|
|`<textSummary>`| block for free text with <p> - optional|
|`<keywords><term/></keywords>`|block- field free text - optional - may be repeated|
|`<textRemarks><p></p></textRemarks>`|block for free text with <p> - optional|
|`<textRights>`|block|
|`<publicationProject></publicationProject>`|DHARMA - not editable|
|`<textDistributionRights target=""/>`|CC-BY 4.0 - not editable|
|`<relatedResources>`|block mandatory|
|<artefactID idno=""/>| content should be formatted ART+6digits - may be repeated|
|<surrogateID idno=""/>| content should be formatted SUR+6digits - may be repeated|
|<imageID idno=""/>| content should be formatted DHARMA_INS+string+5digits_3digits.extension - may be repeated|

## content of the repo and working of the github action
CSV folder = stored the csv files for texts mdt of the projects downloaded from googleSheets. 
output = temporary files for each surrogate, to check if necessary. Splitted by xslt stored in project-documentatation/Stylesheets/mdt_inscriptions/mdtText_splitting.xsl
temporary=  1 xml file containing all texts description used to render the html display. Made with xslt stored in project-documentatation/Stylesheets/mdt_inscriptions/mdtText_start.xsl

build_to_xml.xml = launch the transformation for splitting the output file into several files sotred into temporary.
clone-projectDoc.xml = clone project-documentation for github action

.github/workflows
1- run csvtoxml.yml on push on java line launching project-documentation/stylesheets/mdt_inscriptions/mdtText_start.xsl, source folder github api and destination: temporary folder. 
2- run commacleaning.yml on finishingcsvtoxml.yml .yml task, one java line launching project-documentation/stylesheets/mdt_inscriptions/mdt_CommaCleaning.xsl, source temporary folder, destination temporary folder. 
3- run xmltodisplay.yml on finishing commacleaning.yml task,  launch the two ant tasks clone-projectDoc.xml then build_to_display.xm, source folder temporary, destination folder output

folder output called for all corpora repository from the main build.xml and transform with project-documentatation/Stylesheets/mdt_inscriptions/mdtText_display.xsl to generate a html available with index-mdt.html retrieved thanks to github api. 