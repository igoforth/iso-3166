# iso-3166-2.js

> Lookup information about ISO-3166-2 subdivisions.

### Fork Information

_This package is a fork of [iso-3166-2](https://www.npmjs.com/package/iso-3166-2), which was originally created by [Ola Holmström](https://github.com/olahol). The original repository can be found [here](https://github.com/olahol/iso-3166-2.js). This fork is now maintained by MapQuest, and the original author is no longer involved in the maintenance of this package._

## Country code format

The country codes in the data are in the ISO 3166-1 alpha 2 format (US,
SE ...), but there is a conversion table that makes possible to input
alpha 3 codes (USA, SWE ...) to the `subdivision` and `country` functions.

https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2

https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3

## Examples

```js
> iso3166.subdivision("SE-O");

{ type: 'County',
  name: 'Västra Götalands län',
  countryName: 'Sweden',
  countryCode: 'SE',
  regionCode: 'O',
  code: 'SE-O' }
```

```js
> iso3166.subdivision("UN-1");
null
```

```js
> iso3166.subdivision("SE", "O");

{ type: 'County',
  name: 'Västra Götalands län',
  countryName: 'Sweden',
  countryCode: 'SE',
  regionCode: 'O',
  code: 'SE-O' }
```

```js
> iso3166.subdivision("USA", "Indiana");

{ type: 'state',
  name: 'Indiana',
  countryName: 'United States',
  countryCode: 'US',
  regionCode: 'IN',
  code: 'US-IN' }
```

```js
> iso3166.country("Sweden");
{ name: 'Sweden',
  sub:
   { 'SE-O': { type: 'County', name: 'Västra Götalands län' },
     'SE-N': { type: 'County', name: 'Hallands län' },
     'SE-M': { type: 'County', name: 'Skåne län' },
     'SE-K': { type: 'County', name: 'Blekinge län' },
     'SE-I': { type: 'County', name: 'Gotlands län' },
     'SE-H': { type: 'County', name: 'Kalmar län' },
     'SE-G': { type: 'County', name: 'Kronobergs län' },
     'SE-F': { type: 'County', name: 'Jönköpings län' },
     'SE-E': { type: 'County', name: 'Östergötlands län' },
     'SE-D': { type: 'County', name: 'Södermanlands län' },
     'SE-C': { type: 'County', name: 'Uppsala län' },
     'SE-W': { type: 'County', name: 'Dalarnas län' },
     'SE-Z': { type: 'County', name: 'Jämtlands län' },
     'SE-Y': { type: 'County', name: 'Västernorrlands län' },
     'SE-X': { type: 'County', name: 'Gävleborgs län' },
     'SE-AC': { type: 'County', name: 'Västerbottens län' },
     'SE-AB': { type: 'County', name: 'Stockholms län' },
     'SE-BD': { type: 'County', name: 'Norrbottens län' },
     'SE-T': { type: 'County', name: 'Örebro län' },
     'SE-S': { type: 'County', name: 'Värmlands län' },
     'SE-U': { type: 'County', name: 'Västmanlands län' } },
  code: 'SE' }
```

```js
> iso3166.country("United Nations");
null
```

## Functions

### iso3166.subdivision(code)
Retrieves a subdivision by its full code, ex "SE-O", "US-IN". Returns
`null` if not found.

* * *

### iso3166.subdivision(country code, subdivision code)
Retrieves a subdivision by its country code and subdivision code, ex
("SWE", "O"). Returns `null` if not found.

* * *

### iso3166.subdivision(country code, subdivision name)
Retrieves a subdivision by its country code and subdivision name, ex
("US", "Indiana"). Returns `null` if not found.

* * *

### iso3166.country(country code)
Retrieves a country by its code, ex "US", "SE", "SWE". Returns `null`
if not found.

* * *

### iso3166.country(country name)
Retrieves a country by its name, ex "United States", "Sweden". Returns
`null` if not found.

* * *

### iso3166.data

The raw ISO 3166-2 data, the layout is:

```js
{
  country code (alpha 2): {
    name: country name, ex Sweden, United States ...
    sub: {
      subdivision code: {
        type: subdivision type, ex county, divison ...
        name: subdivision name, ex Västra Götaland, Indiana
      }
    }
  }
}
```

* * *

### iso3166.codes

The ISO 3166-1 alpha 3 to alpha 2 conversion table, the layout is:

```js
{
  country code (alpha 3): country code (alpha 2)
}
```
