
## THIS IS A DRAFT

## Extending other ontologies

[See Extension Mechanism](https://schema.org/docs/extension.html) on Schema.org website.

This entity is an overlay on top of the core Schema's [Winery](https://schema.org/Winery) definition

```
{
  "@context": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0",
  "@vocab": [
    "https://schema.org/Winery"
  ],
  "@type": "Winegrower"          <-- this entity type, in this context
  "name" : "Durand Vigneron"     <-- name property inherited from Schema.org's Winery entity
}
```

## Definitions

__Proposal / RFC__:

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

## Full example


```js
{
  "@context": "https://github.com/OpenWines/Open-Data/tree/master/Ontologies/1.0",
  "@vocab": [
    "https://schema.org"
  ],
  "@type": "Winegrower",
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
