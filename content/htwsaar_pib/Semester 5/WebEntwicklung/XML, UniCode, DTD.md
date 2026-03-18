  

- XML = Extensible Markup Language

- Dieser Standard ist Lesbar für Maschinen und Menschen

Es wurde als Standard zum DatenAustausch entwickelt

  

### XML Elemente

```XML
<buch>
Grundlagen von XML     <-- Content des Elements
</buch>
```

  

### XML : Attribute

```XML
<buch preis="19,95 Euro" auflage="2.">

	<titel> Grundlagen von XML </titel>
	
</buch>
```

  

- when to use child elements / when to use attributes

```XML
<book>
<authors>

<author> John Doe  </author>
<author> Jane Smith </author>

</authors>

</book>
```

  

### XML : Declaration

- Use UTF-8 instead of `ISO-8859-1`

  

### DTD : Declaration

- DTD : Document Type Definition, specifies rules on how XML files are structured

- an XML is valid, if it follows these rules

  

```XML
<!ELEMENT katalog (buch*)>
<!ELEMENT buch (author*, titel)>
<!ELEMENT vorname (\#PCDATA)>
<!ELEMENT nachname (\#PCDATA)>
<!ELEMENT titel (\#PCDATA)>
```

  

```XML
<!ELEMENT para (\#PCDATA | example | figure | table)*>
```

  

- Wir benutztn \#PCDATA für Elemrente, und CDATA für Attribute.

- P bedeutet dass der Parser diesen Text scannt und darin `&amp` oder `<` erkennt.

  

### Beispiele :

- Verlag O’Reilly : `<buch verlag =’O&apos;Reilly’ </buch>`

- `&gt;` für das Zeichen `>`

- `&quot;` für das Zeichen `"`

- `&apos;` für das Zeichen `'`

  

- Kommentare in XML : `<!- - DAs ist ein Comment - - >`

  

```XML
<!ATTLIST buch 

ISBN DATA \#REQUIRED

preis CDATA \#REQUIRED

author CDATA \#REQUIRED


>
```

  

```XML
<!ATTLIST eintrag
name             ID      \#REQUIRED 
elterneintrag    IDREF   \#REQUIRED 
>
```

  

### Makro as Entity

```XML
<!ENTITY sb "Saarbruecken">

<info> Er ist 35 und wohnt in &sb;.</info>
```

  

  

> [!important]
> 
> DTD FIles können `standalone` sein → werden nicht validiert  
> Mit Reglwerk → werden gegen diese Rules geprüft

  

  

### ASCII ZeichenSatz

Wir können 128 Chars encoden

  

### UniCode

- Unicode defines >100K characters

- is a SuperSet of ASCII → No mismatches

  

> [!important]
> 
> U+0054 (HEX) → 84 (DEZ) → T (ASCII)

  

> If Possible, use UTF-8, or at least the same encoding everywhere