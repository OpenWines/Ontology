
## THIS IS A DRAFT

Current status: Proposal, RFC. Use [Github online editor to propose your changes](https://help.github.com/articles/editing-files-in-another-user-s-repository/).

## Extending other ontologies

Onotologies namespaces, such as [Schema.org](http://schema.org), provide a core, basic vocabulary for describing the kind of entities the most common web applications need. There is often a need for more specialized and/or deeper vocabularies, that build upon the core. [Schema.org](http://schema.org) The extension mechanisms facilitate the creation of such additional vocabularies.

[See Extension Mechanism](https://schema.org/docs/extension.html) on Schema.org website.

`@vocab` actually allow you to use an existing vocabulary in an inherited entity definition  

This entity is an overlay on top of the core Schema's [Winery](https://schema.org/Winery) definition

```
{
  "@context": [ 
      "http://schema.org/",
      { "ow": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0/" }
  ],
  "@type": "Winegrower",             <-- this entity type, defined in this context
  "name" : "Durand Vigneron"         <-- name property inherited from Schema.org's Winery entity
}
```

This approach also allow to define french terms spelled sub-types: `vigneron`, `viticulteur`, `viniviticulteur`, `récoltant`, which are more precise entities from the english `winegrower`.

## Inherited definitions

### `memberOf`

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

### `isLandowner`

Property    | Expected Type               | Description | Example
----------- | --------------------------- | ----------- | -------
`ow:isLandowner` | [`Boolean`](https://schema.org/Boolean) | owns the lands where he produces his wines | `true`

```json
{
  "@context": [ 
      "http://schema.org/",
      { "ow": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0/" }
  ],
  "@type": "Winegrower",
  "ow:isLandowner" : true,
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
  "@type": "Winegrower",
  "ow:isLandowner" : true,  
  "address":
    "@type": "sc:PostalAddress",
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
  "isicV4": "11.02"
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
