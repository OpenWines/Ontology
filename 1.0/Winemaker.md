
![OpenWines](https://raw.githubusercontent.com/OpenWines/Resources/master/elements/favicons/android-icon-96x96.png)

# Winemaker

`winemaker` (plural `winemakers`)

- a person or company that makes wine

(source: [wiktionary](https://en.wiktionary.org/wiki/winemaker))

## THIS IS A DRAFT

Current status: Proposal, RFC. Use [Github online editor to propose your changes](https://help.github.com/articles/editing-files-in-another-user-s-repository/).

## The JSON-LD format choice

The JSON-LD format choice was [motivated in this article](http://openwines.eu/data-formats.html).

Proposing a JSON-LD format definition is compliant with both linked-data objectives, semantic web, and interoperability concerns, being a RDFa compatible format.

Learn more about [JSON-LD](http://www.w3.org/TR/json-ld/) (full spec on W3C)

[Schema.org](http://schema.org) already proposes a JSON-LD output for each entity it defines.

## Extending other ontologies

Ontologies namespaces, such as [Schema.org](http://schema.org), provide a core, basic vocabulary for describing the kind of entities the most common web applications need. There is often a need for more specialized and/or deeper vocabularies, that build upon the core. [Schema.org](http://schema.org) extension mechanisms facilitate the creation of such additional vocabularies.

[See how Extension Mechanism works](https://schema.org/docs/extension.html) on Schema.org website.

`@vocab` actually allow you to use an existing vocabulary in an inherited entity definition  

This entity is an overlay on top of the core Schema's [Winery](https://schema.org/Winery) definition

```
{
  "@context": [ 
      "http://schema.org/",
      { "ow": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0/" }
  ],
  "@type": "Winemaker",             <-- this entity type, defined in this context
  "name" : "Durand Vigneron"         <-- name property inherited from Schema.org's Winery entity
}
```

This approach allows also to define french terms spelled sub-types: `vigneron`, `viticulteur`, `viniviticulteur`, `récoltant`, or the english `winegrower` / `vintner`.

## Inherited definitions

These properties are given only for information, the whole list can be found in the [`Winery`] parent type definition on [Schema.org](https://schema.org), so this list is not intended to be exhaustive.

### Ex: Schema's [`memberOf`](https://schema.org/memberOf)

Property    | Expected Type               | Type origin                        | Description | Example
----------- | --------------------------- | ---------------------------------- | ----------- | -------
[`memberOf`](https://schema.org/memberOf) | [`Person`](https://schema.org/Person), [`Organization`](https://schema.org/Organization) | [`Winery`](https://schema.org/Winery)| memberships | see below

```json
{
  "memberOf": {
    "@type": "Organization",
    "name": "Vigneron Indépendant",
    "url": "http://www.vigneron-independant.com"
}
```

## New definitions

### DISCLAIMERS

- This is Work In Progress
- Each new property mentioned here always needs to be evaluated accurately before being accepted. Expect to face contradictions ;-) 

These are the properties actually proposed in addition, in the [OpenWines.org](http://openwines.org) namespace.

### `isLandowner`

Motivation: In both french and english vocabulary, many sub-types exists to define more precisely the person that make wine : (english) `winegrower`, `vintner`, (french) `vigneron`, `viticulteur`, `viniviticulteur`, `récoltant`. Each one is a variant of a global job family, but some of them have common the fact that they describe a person who owns the lands where the grapes are grown and harvested.

Property    | Expected Type               | Description | Example
----------- | --------------------------- | ----------- | -------
`ow:isLandowner` | [`Boolean`](https://schema.org/Boolean) | owns the lands where he produces his wines | `true`

```json
{
  "@context": [ 
      "http://schema.org/",
      { "ow": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0/" }
  ],
  "@type": "Winemaker",
  "ow:isLandowner": true,
  "name" : "Durand Vigneron"
}
```

## Full example


```json
{
  "@context": [ 
      "http://schema.org/",
      { "ow": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0/" }
  ],
  "@type": "Winemakerr",
  "ow:isLandowner": true,  
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Sainte Lumine de Clisson",
    "addressRegion": "Pays de la Loire",
    "postalCode": "44190",
    "streetAddress": "26 les Défois"
  },
  "memberOf": {
    "@type": "Organization",
    "name": "Syndicat Défense Des AOC Muscadet",
    "url" : "http://www.muscadet-grosplant.fr/",
    "telephone": "+33 2 40 80 14 90"
  },
  "businessRegistration": "RCS Nantes 514582691",
  "isicV4": "11.02",
  "name": "Durand Vigneron",
  "openingHours": [
    "Mo-Sa 11:00-14:30",
    "Mo-Th 17:00-21:30",
    "Fr-Sa 17:00-22:00"
  ],
  "telephone": "+33 2 40 54 70 03",
  "fax": "+33 2 40 54 70 03",
  "email": "mailto:durand.verteprairie@wanadoo.fr",
  "url": "http://www.durand-vigneron.com"
}
```
