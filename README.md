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
|date|block|
|`<textDate calendar=""><!-- may be repeated --><!-- the calendar has to be declared in the attribute calendar --><ruler></ruler><!-- only for the regnal year -->	<year></year><month></month><fornight></fornight><day></day></textDate>`|TO BE DISCUSSED|
|`<origDate notBefore="" notAfter="" precision="" evidence="" datingMethod=""></origDate><!-- equivalence of the date according to the occidental calendar -->`|TO BE DISCUSSED|

<textDate>
<dateRegnalYear>
	<ruler></ruler>
	<year></year>
	<month></month>
	<fornight></fornight>
	<day></day>
</dateRegnalYear>
<date calendar=""><!-- may be repeated --><!-- the calendar has to be declared in the attribute calendar -->
	<year></year>
	<month></month>
	<fornight></fornight>
	<day></day>
</date>
<dateJovianCycle>
	<cycleName></cycleName>
	<month></month>
	<fornight></fornight>
	<day></day>
</dateJovianCycle>
<origDate notBefore="" notAfter="" precision="" evidence="" datingMethod=""></origDate><!-- equivalence of the date according to the occidental calendar -->
</textDate>
	<textFiliation>
		<duplicateTextID idno=""/><!-- may be repeated -->
		<textReissue value=""/>
		<reissueTextID idno=""/>
		<reissueDate when=""/>
	</textFiliation>
  <textSummary><p></p></textSummary>
	<keywords><!-- may be repeated -->
		<term value=""></term>
	</keywords>
	<textRemarks><p></p></textRemarks>
	<textBibliography>
		<listBibl type=""><!-- may be repeated --><!-- choose primary or secondary -->
			<bibl><!-- may be repeated for each bibliographical reference -->
				<ptr target=""/><!-- pointer towards the Zotero short title -->
				<citedRange unit=""></citedRange>
			</bibl>
		</listBibl>
	</textBibliography>
	<textRights>
		<publicationProject></publicationProject>
		<textDistributionRights target=""/>
	</textRights>
	<relatedResources>
		<artefactID idno=""/><!-- may be repeated -->
		<surrogateID idno=""/><!-- may be repeated -->
		<imageID idno=""/><!-- may be repeated -->
	</relatedResources>
</textDescription>
</textMetadataTemplate>
