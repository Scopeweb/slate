---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://www.scopeweb.nl'>Powered by scopeweb.nl</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Linsta API! You can use our API to access Linsta API.

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right in the future when other language bindings become availabe.

If you're interested in the Linsta app, visit the Linsta website

# JSON Web Tokens

Haven uses JSON web token to allow access to the API. You can retrieve a JWT by logging a user in against our login endpoint.

Haven expects for the JSON web token to be included in all API requests - except for the Auth ones - to the server in a header that looks like the following:

Authorization: Bearer jsonwebtoken

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: Bearer jsonwebtoken"
```
> Make sure to replace `Bearer jsonwebtoken` with your API key.


`Authorization: Bearer jsonwebtoken`

<aside class="notice">
You must replace <code>Bearer jsonwebtoken</code> with your personal API key.
</aside>

# Admin

## Add category

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/categories/add-category" \
  -H "Authorization: Bearer jsonwebtoken" \
  --header 'Content-Type: application/json' \
  --data-raw '{
    "serviceName": "Test",
    "industry": "Klusbedrijf",
    "keywords": [
        "Test,Test 1,Test 2"
    ],
    "steps": [
        {
            "step": [
                {
                    "fieldType": "select",
                    "inputType": "text",
                    "label": "Test",
                    "name": "Test Select",
                    "placeholder": "",
                    "isRequired": "true",
                    "selectValues": [
                        {
                            "value": "Test me"
                        },
                        {
                            "value": "Test you"
                        },
                        {
                            "value": "Test"
                        }
                    ]
                },
                {
                    "fieldType": "input",
                    "inputType": "text",
                    "label": "Test",
                    "name": "Test",
                    "placeholder": "Test",
                    "isRequired": "true"
                }
            ]
        }
    ]
}'
```

>The above command returns JSON structured like this:

```json
{
    "message": "Added new category",
    "status": 200
}    
```

This endpoint creates a new category.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/categories/add-category`

### Body Parameters

| Parameter   | Default   | Description                 |
| ----------- | --------- | --------------------------- |
| steps       | undefined | Array of steps              |
| serviceName | undefined | String of the service name  |
| keywords    | undefined | String array of keywords    |
| images      | undefined | Array of image urls         |
| industry    | undefined | String of the industry name |

## Add Place Job field type

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/place-jobs/add-fieldtype" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'type=radio' \
  --data-urlencode 'inputType=text' \
  --data-urlencode 'name=Radio button invoer' \
  --data-urlencode 'description=Radio button met meerdere keuzemogelijkheden maar gelimiteerd tot 1 uiteindelijke keuze'
```

>The above command returns JSON structured like this:

```json
{
    "message": "Added new fieldtype",
    "status": 200
}
```

This endpoint creates a new fieldtype.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/place-jobs/add-fieldtype`

### Body Parameters

| Parameter   | Default   | Description                 |
| ----------- | --------- | --------------------------- |
| type        | undefined | String of type              |
| inputType   | undefined | String of inputType         |
| name        | undefined | String of names             |
| description | undefined | String of description       |
| industry    | undefined | String of the industry name |

<aside class="warning">
Developers only
</aside>

## Delete Place Job

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/admin/category/:job_id" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "message": "Deleted job",
    "status": 200
}
```

This endpoint deletes a category.

### HTTP Request

`DELETE https://api.linsta.nl/v1/admin/place-jobs/fieldtypes`

## Get Place Job fieldtypes

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/place-jobs/fieldtypes" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "fieldTypes": [
        {
            "_id": "5dc94328543a5b4f67018516",
            "type": "input",
            "inputType": "text",
            "name": "Tekst invoer",
            "description": "Veld voor korte tekst invoer",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:16:56.360Z",
            "updatedAt": "2019-11-11T11:16:56.360Z",
            "__v": 0
        },
        {
            "_id": "5dc94337543a5b4f67018519",
            "type": "input",
            "inputType": "number",
            "name": "Nummer invoer",
            "description": "Veld voor nummer invoer",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:17:11.199Z",
            "updatedAt": "2019-11-11T11:17:11.199Z",
            "__v": 0
        },
        {
            "_id": "5dc9433b543a5b4f6701851a",
            "type": "input",
            "inputType": "email",
            "name": "E-mail invoer",
            "description": "Veld voor e-mailadres invoer",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:17:15.139Z",
            "updatedAt": "2019-11-11T11:17:15.139Z",
            "__v": 0
        },
        {
            "_id": "5dc94341543a5b4f6701851c",
            "type": "input",
            "inputType": "tel",
            "name": "Tel. nr invoer",
            "description": "Veld voor telefoonnummer invoer",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:17:21.662Z",
            "updatedAt": "2019-11-11T11:17:21.662Z",
            "__v": 0
        },
        {
            "_id": "5dc9438b543a5b4f67018520",
            "type": "textarea",
            "inputType": "text",
            "name": "Textarea",
            "description": "Tekstveld met meerdere rijen",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:18:35.212Z",
            "updatedAt": "2019-11-11T11:18:35.212Z",
            "__v": 0
        },
        {
            "_id": "5dc943a6543a5b4f67018526",
            "type": "checkbox",
            "inputType": "text",
            "name": "Checkbox invoer",
            "description": "Checkbox vakje met meerdere keuze mogelijkheden",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:19:02.486Z",
            "updatedAt": "2019-11-11T11:19:02.486Z",
            "__v": 0
        },
        {
            "_id": "5dc943ab543a5b4f67018527",
            "type": "radio",
            "inputType": "text",
            "name": "Radio button invoer",
            "description": "Radio button met meerdere keuzemogelijkheden maar gelimiteerd tot 1 uiteindelijke keuze",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:19:07.043Z",
            "updatedAt": "2019-11-11T11:19:07.043Z",
            "__v": 0
        },
        {
            "_id": "5dc943ad543a5b4f67018528",
            "type": "select",
            "inputType": "text",
            "name": "Select dropdown",
            "description": "Dropdown met meerdere keuzes",
            "icon": "https://res.cloudinary.com/scope-web-llc/image/upload/v1573482529/Klusnet/text-icon.png",
            "createdAt": "2019-11-11T11:19:09.528Z",
            "updatedAt": "2019-11-11T11:19:09.528Z",
            "__v": 0
        },
        {
            "_id": "5e4185736b126f154a403e91",
            "type": "radio",
            "inputType": "text",
            "name": "Radio button invoer",
            "description": "Radio button met meerdere keuzemogelijkheden maar gelimiteerd tot 1 uiteindelijke keuze",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves all available fieldtypes

### HTTP Request

`GET https://api.linsta.nl/v1/admin/place-jobs/fieldtypes`

## Get reviews

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/reviews" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "reviews": [
        {
            "_id": "5dd3ebcf57077ed184631a64",
            "reviewer": {
                "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "_id": "5dca7a9a3d5cc53294ff0cff",
                "email": "gebruiker@demo.nl",
                "userProfile": {
                    "_id": "5dca7ab63d5cc53294ff0d00",
                    "firstName": "Teunis",
                    "lastName": "van Kerkhof"
                }
            },
            "company": {
                "location": {
                    "coordinates": [
                        51.8961104,
                        4.1722762
                    ],
                    "type": "Point"
                },
                "industries": [
                    "Aannemer",
                    "Elektricien",
                    "Metselaar",
                    "Verhuisbedrijf"
                ],
                "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "pageVisible": true,
                "accountLevel": "basic",
                "reviews": [
                    "5e189faf796f851bce1ea314",
                    "5ddc39d93512431f7d33a9da",
                    "5ddc2d8309469d93f9c61e28",
                    "5dd3ebcf57077ed184631a64"
                ],
                "activeSubscription": true,
                "_id": "5e09b6027521a16081b1b389",
                "KvkNumber": "12345678",
                "companyName": "Vakman",
                "companyAddress": "Vakman 1",
                "companyZipCode": "3232HE",
                "companyCity": "IJsselmuiden",
                "region": "XZH",
                "firstName": "Test",
                "lastName": "Vakman",
                "phone": "0612345678",
                "pageSlug": "testbv",
                "createdAt": "2019-12-30T08:32:02.129Z",
                "updatedAt": "2020-01-28T17:00:27.342Z",
                "__v": 16,
                "companyDescription": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
                "companySlogan": "Voor elke klus, vakman BV dus",
                "avgReviewRating": 4.7,
                "avgReviews": 4.8,
                "projectPictures": [],
                "subscriptionLevel": "Enterprise"
            },
            "rating": 4.4,
            "industry": "Badkamer specialist",
            "title": "Buitenkraan plaatsen in achtertuin",
            "description": "Een vriendelijke, netjes werkenende en snelle vakman. Werkzaamheden al binnen enkele dagen na eerste contact uitgevoerd. Heldere uitleg ná de installatie. Ik beveel deze vakman dan ook van harte aan.",
            "createdAt": "2019-11-19T13:19:11.996Z",
            "updatedAt": "2019-11-19T13:19:11.996Z",
            "__v": 0
        },
        {
            "_id": "5ddc39d93512431f7d33a9da",
            "reviewer": {
                "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "_id": "5dca7a9a3d5cc53294ff0cff",
                "email": "gebruiker@demo.nl",
                "userProfile": {
                    "_id": "5dca7ab63d5cc53294ff0d00",
                    "firstName": "Teunis",
                    "lastName": "van Kerkhof"
                }
            },
            "company": {
                "location": {
                    "coordinates": [
                        51.8961104,
                        4.1722762
                    ],
                    "type": "Point"
                },
                "industries": [
                    "Aannemer",
                    "Elektricien",
                    "Metselaar",
                    "Verhuisbedrijf"
                ],
                "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "pageVisible": true,
                "accountLevel": "basic",
                "reviews": [
                    "5e189faf796f851bce1ea314",
                    "5ddc39d93512431f7d33a9da",
                    "5ddc2d8309469d93f9c61e28",
                    "5dd3ebcf57077ed184631a64"
                ],
                "activeSubscription": true,
                "_id": "5e09b6027521a16081b1b389",
                "KvkNumber": "12345678",
                "companyName": "Vakman",
                "companyAddress": "Vakman 1",
                "companyZipCode": "3232HE",
                "companyCity": "IJsselmuiden",
                "region": "XZH",
                "firstName": "Test",
                "lastName": "Vakman",
                "phone": "0612345678",
                "pageSlug": "testbv",
                "createdAt": "2019-12-30T08:32:02.129Z",
                "updatedAt": "2020-01-28T17:00:27.342Z",
                "__v": 16,
                "companyDescription": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
                "companySlogan": "Voor elke klus, vakman BV dus",
                "avgReviewRating": 4.7,
                "avgReviews": 4.8,
                "projectPictures": [],
                "subscriptionLevel": "Enterprise"
            },
            "rating": 4.9,
            "title": "Draagbalk plaatsen",
            "industry": "Loodgieter",
            "description": "In contact gekomen met Teunis via Klusnet. Hij was veruit de betrouwbaarste. Een dag later stond hij al bij ons binnen. Duidelijke afspraken gemaakt. Een paar dagen voor dat de klus uitgevoerd werd nam hij weer contact met ons op om de afspraken nog eens door te nemen. Wim en zijn team werken als een razende en binnen een halve dag was de klus geklaard. Kortom een vakman die snel werkt en duidelijke afspraken maakt.",
            "createdAt": "2019-11-25T20:30:17.660Z",
            "updatedAt": "2019-11-25T20:30:17.660Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves all reviews with the ability to filter then.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/reviews`

## Get reviews with fitler

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/reviews/:filter_type" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "reviews": [
        {
            "_id": "5dd3ebcf57077ed184631a64",
            "reviewer": {
                "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "_id": "5dca7a9a3d5cc53294ff0cff",
                "email": "gebruiker@demo.nl",
                "userProfile": {
                    "_id": "5dca7ab63d5cc53294ff0d00",
                    "firstName": "Teunis",
                    "lastName": "van Kerkhof"
                }
            },
            "company": {
                "location": {
                    "coordinates": [
                        51.8961104,
                        4.1722762
                    ],
                    "type": "Point"
                },
                "industries": [
                    "Aannemer",
                    "Elektricien",
                    "Metselaar",
                    "Verhuisbedrijf"
                ],
                "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "pageVisible": true,
                "accountLevel": "basic",
                "reviews": [
                    "5e189faf796f851bce1ea314",
                    "5ddc39d93512431f7d33a9da",
                    "5ddc2d8309469d93f9c61e28",
                    "5dd3ebcf57077ed184631a64"
                ],
                "activeSubscription": true,
                "_id": "5e09b6027521a16081b1b389",
                "KvkNumber": "12345678",
                "companyName": "Vakman",
                "companyAddress": "Vakman 1",
                "companyZipCode": "3232HE",
                "companyCity": "IJsselmuiden",
                "region": "XZH",
                "firstName": "Test",
                "lastName": "Vakman",
                "phone": "0612345678",
                "pageSlug": "testbv",
                "createdAt": "2019-12-30T08:32:02.129Z",
                "updatedAt": "2020-01-28T17:00:27.342Z",
                "__v": 16,
                "companyDescription": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
                "companySlogan": "Voor elke klus, vakman BV dus",
                "avgReviewRating": 4.7,
                "avgReviews": 4.8,
                "projectPictures": [],
                "subscriptionLevel": "Enterprise"
            },
            "rating": 4.4,
            "industry": "Badkamer specialist",
            "title": "Buitenkraan plaatsen in achtertuin",
            "description": "Een vriendelijke, netjes werkenende en snelle vakman. Werkzaamheden al binnen enkele dagen na eerste contact uitgevoerd. Heldere uitleg ná de installatie. Ik beveel deze vakman dan ook van harte aan.",
            "createdAt": "2019-11-19T13:19:11.996Z",
            "updatedAt": "2019-11-19T13:19:11.996Z",
            "__v": 0
        },
        {
            "_id": "5ddc39d93512431f7d33a9da",
            "reviewer": {
                "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "_id": "5dca7a9a3d5cc53294ff0cff",
                "email": "gebruiker@demo.nl",
                "userProfile": {
                    "_id": "5dca7ab63d5cc53294ff0d00",
                    "firstName": "Teunis",
                    "lastName": "van Kerkhof"
                }
            },
            "company": {
                "location": {
                    "coordinates": [
                        51.8961104,
                        4.1722762
                    ],
                    "type": "Point"
                },
                "industries": [
                    "Aannemer",
                    "Elektricien",
                    "Metselaar",
                    "Verhuisbedrijf"
                ],
                "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                "pageVisible": true,
                "accountLevel": "basic",
                "reviews": [
                    "5e189faf796f851bce1ea314",
                    "5ddc39d93512431f7d33a9da",
                    "5ddc2d8309469d93f9c61e28",
                    "5dd3ebcf57077ed184631a64"
                ],
                "activeSubscription": true,
                "_id": "5e09b6027521a16081b1b389",
                "KvkNumber": "12345678",
                "companyName": "Vakman",
                "companyAddress": "Vakman 1",
                "companyZipCode": "3232HE",
                "companyCity": "IJsselmuiden",
                "region": "XZH",
                "firstName": "Test",
                "lastName": "Vakman",
                "phone": "0612345678",
                "pageSlug": "testbv",
                "createdAt": "2019-12-30T08:32:02.129Z",
                "updatedAt": "2020-01-28T17:00:27.342Z",
                "__v": 16,
                "companyDescription": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
                "companySlogan": "Voor elke klus, vakman BV dus",
                "avgReviewRating": 4.7,
                "avgReviews": 4.8,
                "projectPictures": [],
                "subscriptionLevel": "Enterprise"
            },
            "rating": 4.9,
            "title": "Draagbalk plaatsen",
            "industry": "Loodgieter",
            "description": "In contact gekomen met Teunis via Klusnet. Hij was veruit de betrouwbaarste. Een dag later stond hij al bij ons binnen. Duidelijke afspraken gemaakt. Een paar dagen voor dat de klus uitgevoerd werd nam hij weer contact met ons op om de afspraken nog eens door te nemen. Wim en zijn team werken als een razende en binnen een halve dag was de klus geklaard. Kortom een vakman die snel werkt en duidelijke afspraken maakt.",
            "createdAt": "2019-11-25T20:30:17.660Z",
            "updatedAt": "2019-11-25T20:30:17.660Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves all reviews with the ability to filter then.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/reviews/:filter_type`

### Query Parameters

| Parameter   | Default   | Description                                                        |
| ----------- | --------- | ------------------------------------------------------------------ |
| filter_type | undefined | Type of filter.  Supported ones are newest, oldest, rateHL, rateLH |
| industry    | undefined | String ofindustry name                                             |

## Get categories

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/list-categories" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "categories": [
        {
            "keywords": [
                "Aanbouw",
                " Opbouw",
                " Aanbouw plaatsen",
                " Opbouw plaatsen",
                " Aanbouw of opbouw",
                " Aanbouw of opbouw plaatsen"
            ],
            "steps": [],
            "images": [],
            "_id": "5dffe9e9c579034d9380b961",
            "serviceName": "Aanbouw of opbouw plaatsen",
            "industry": "Aannemer",
            "createdAt": "2019-12-22T22:10:49.323Z",
            "updatedAt": "2020-01-08T09:50:13.774Z",
            "__v": 2
        },
        {
            "keywords": [
                "B",
                " bad",
                " Badkamer",
                " Badkamer plaatsen",
                " Badkamer renoveren"
            ],
            "steps": [],
            "images": [],
            "_id": "5e002c4321e54950c27dcc91",
            "serviceName": "Badkamer plaatsen of renoveren",
            "industry": "Badkamer specialist",
            "createdAt": "2019-12-23T02:53:55.984Z",
            "updatedAt": "2019-12-23T07:33:36.906Z",
            "__v": 0
        },
        {
            "keywords": [
                "Fund",
                " funderingen",
                " hei",
                " heiwerk"
            ],
            "steps": [],
            "images": [],
            "_id": "5e0f1d0f739a279ebcfc7356",
            "serviceName": "Funderingen & heiwerk",
            "industry": "Aannemer",
            "createdAt": "2020-01-03T10:53:03.032Z",
            "updatedAt": "2020-01-04T14:21:00.513Z",
            "__v": 0
        },
        {
            "keywords": [
                "Gar",
                " Garage",
                " schuur",
                " verbouw garage",
                " "
            ],
            "steps": [],
            "images": [],
            "_id": "5e0f1dd4739a279ebcfc735d",
            "serviceName": "Garage (ver)bouw",
            "industry": "Aannemer",
            "createdAt": "2020-01-03T10:56:20.851Z",
            "updatedAt": "2020-01-03T10:56:20.851Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves all categories.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/list-categories`

## Get categories by industry

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/list-categories/:industryName" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "categories": [
        {
            "keywords": [
                "Aanbouw",
                " Opbouw",
                " Aanbouw plaatsen",
                " Opbouw plaatsen",
                " Aanbouw of opbouw",
                " Aanbouw of opbouw plaatsen"
            ],
            "steps": [],
            "images": [],
            "_id": "5dffe9e9c579034d9380b961",
            "serviceName": "Aanbouw of opbouw plaatsen",
            "industry": "Aannemer",
            "createdAt": "2019-12-22T22:10:49.323Z",
            "updatedAt": "2020-01-08T09:50:13.774Z",
            "__v": 2
        },
        {
            "keywords": [
                "B",
                " bad",
                " Badkamer",
                " Badkamer plaatsen",
                " Badkamer renoveren"
            ],
            "steps": [],
            "images": [],
            "_id": "5e002c4321e54950c27dcc91",
            "serviceName": "Badkamer plaatsen of renoveren",
            "industry": "Badkamer specialist",
            "createdAt": "2019-12-23T02:53:55.984Z",
            "updatedAt": "2019-12-23T07:33:36.906Z",
            "__v": 0
        },
        {
            "keywords": [
                "Fund",
                " funderingen",
                " hei",
                " heiwerk"
            ],
            "steps": [],
            "images": [],
            "_id": "5e0f1d0f739a279ebcfc7356",
            "serviceName": "Funderingen & heiwerk",
            "industry": "Aannemer",
            "createdAt": "2020-01-03T10:53:03.032Z",
            "updatedAt": "2020-01-04T14:21:00.513Z",
            "__v": 0
        },
        {
            "keywords": [
                "Gar",
                " Garage",
                " schuur",
                " verbouw garage",
                " "
            ],
            "steps": [],
            "images": [],
            "_id": "5e0f1dd4739a279ebcfc735d",
            "serviceName": "Garage (ver)bouw",
            "industry": "Aannemer",
            "createdAt": "2020-01-03T10:56:20.851Z",
            "updatedAt": "2020-01-03T10:56:20.851Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves all categories by the industry name.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/list-categories/:industryName`

### Query Parameters

| Parameter    | Default   | Description            |
| ------------ | --------- | ---------------------- |
| industryName | undefined | String ofindustry name |

## Get category with steps

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/category/:category_id" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "category": {
        "keywords": [
            "Test 1",
            "Test 2",
            "Test 3"
        ],
        "steps": [
            {
                "isActive": true,
                "formFields": [
                    {
                        "required": true,
                        "readOnly": false,
                        "disabled": false,
                        "isActive": true,
                        "_id": "5e417ddee6f708c62a545540",
                        "fieldType": "select",
                        "name": "Test",
                        "label": "Test",
                        "isRequired": true,
                        "placeholder": "",
                        "checkBoxValues": [],
                        "radioValues": [],
                        "selectValues": [
                            {
                                "value": "Test me"
                            },
                            {
                                "value": "TEst you"
                            },
                            {
                                "value": "Test"
                            }
                        ],
                        "__v": 0
                    },
                    {
                        "required": true,
                        "readOnly": false,
                        "disabled": false,
                        "isActive": true,
                        "_id": "5e417ddee6f708c62a545541",
                        "fieldType": "input",
                        "name": "Test",
                        "label": "Test",
                        "isRequired": true,
                        "placeholder": "Test",
                        "checkBoxValues": [],
                        "radioValues": [],
                        "selectValues": [],
                        "__v": 0
                    }
                ],
                "_id": "5e417ddee6f708c62a545542",
                "stepNumber": 0,
                "createdAt": "2020-02-10T15:59:26.692Z",
                "updatedAt": "2020-02-10T15:59:26.692Z",
                "__v": 0
            }
        ],
        "images": [],
        "_id": "5e417ddee6f708c62a545543",
        "serviceName": "Test",
        "industry": "Klusbedrijf",
        "createdAt": "2020-02-10T15:59:26.692Z",
        "updatedAt": "2020-02-10T15:59:26.692Z",
        "__v": 0
    },
    "status": 200
}
```

This endpoint retrieves category with steps.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/category/:category_id`

### Query Parameters

| Parameter   | Default   | Description                        |
| ----------- | --------- | ---------------------------------- |
| category_id | undefined | MongoDB Object ID of the  category |

## Update category

```shell
curl --location --request PUT "https://api.linsta.nl/v1/admin/update-category/:category_id" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "message": "Category has been updated.",
    "status": 200
}
```

This endpoint updates a category.

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/update-category/:category_id`

### Query Parameters

| Parameter   | Default   | Description                        |
| ----------- | --------- | ---------------------------------- |
| category_id | undefined | MongoDB Object ID of the  category |

### Body Parameters

| Parameter    | Default   | Description             |
| ------------ | --------- | ----------------------- |
| industryName | undefined | String of industry name |
| serviceName  | undefined | String of service name  |
| keywords     | undefined | Array of keywords       |

## Add category question

```shell
curl --location --request PUT "https://api.linsta.nl/v1/admin/category/add-question/:step_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'type=Test' \
  --data-urlencode 'icon=Test' \
  --data-urlencode 'label=Test' \
  --data-urlencode 'required=Test' \
  --data-urlencode 'readOnly=Test' \
  --data-urlencode 'disabled=Test' \
  --data-urlencode 'isActive=Test' \
  --data-urlencode 'placeholder=Test' \
```

>The above command returns JSON structured like this:

```json
{
      "message": "Question has been added to step.",
      "status": 200
}
```

This endpoint adds a qustion to step.

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/category/add-question/:step_id`

### Query Parameters

| Parameter | Default   | Description                   |
| --------- | --------- | ----------------------------- |
| step_id   | undefined | MongoDB Object ID of the step |

### Body Parameters

| Parameter   | Default   | Description           |
| ----------- | --------- | --------------------- |
| type        | undefined | String of type        |
| icon        | undefined | String of icon        |
| label       | undefined | String of label       |
| required    | undefined | String of required    |
| readOnly    | undefined | String of readOnly    |
| disabled    | undefined | String of disabled    |
| isActive    | undefined | String of isActive    |
| placeholder | undefined | String of placeholder |

## Delete category question

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/admin/category/:question_id/:step_id" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
  "message": "Removed qustion from step",
  "status": 200
}
```

This endpoint delete a qustion from step.

### HTTP Request

`DELETE https://api.linsta.nl/v1/admin/category/:question_id/:step_id`

### Query Parameters

| Parameter   | Default   | Description                       |
| ----------- | --------- | --------------------------------- |
| step_id     | undefined | MongoDB Object ID of the step     |
| question_id | undefined | MongoDB Object ID of the question |

## Update category question order

```shell
curl --location --request PUT "https://api.linsta.nl/v1/admin/category/update-step/:step_id" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
  "message": "Step has been updated.",
  "status": 200
}
```

This endpoint update a qustion order from step.

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/category/update-step/:step_id`

### Query Parameters

| Parameter | Default   | Description                   |
| --------- | --------- | ----------------------------- |
| step_id   | undefined | MongoDB Object ID of the step |

### Body Parameters

| Parameter   | Default   | Description  |
| ----------- | --------- | ------------ |
| newPosition | undefined | New Position |
| oldPosition | undefined | Old Position |

## Delete step

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/category/delete-step/:job_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'stepId=5dd570d1873225ab198e47d4'
```

>The above command returns JSON structured like this:

```json
{
  "message": "De stap is verwijderd en niet meer zichtbaar",
  "status": 200
}
```

This endpoint update a qustion order from step.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/category/delete-step/:job_id`

### Query Parameters

| Parameter | Default   | Description                  |
| --------- | --------- | ---------------------------- |
| job_id    | undefined | MongoDB Object ID of the job |

### Body Parameters

| Parameter | Default   | Description                             |
| --------- | --------- | --------------------------------------- |
| stepId    | undefined | MongoDB Object ID of the step to remove |

## Add industry

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/industry" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'name=Test'
```

>The above command returns JSON structured like this:

```json
{
  "message": "De stap is verwijderd en niet meer zichtbaar",
  "status": 200
}
```

This endpoint add new industry.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/industry`

### Body Parameters

| Parameter | Default   | Description    |
| --------- | --------- | -------------- |
| name      | undefined | String of name |

## Update industry

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/industry/:industry_name" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'name=Test'
```

>The above command returns JSON structured like this:

```json
{
  "message": "Industry has been updated.",
  "status": 200
}
```

This endpoint updates industry.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/industry/:industry_name`

### Query Parameters

| Parameter     | Default   | Description             |
| ------------- | --------- | ----------------------- |
| industry_name | undefined | String of industry name |

### Body Parameters

| Parameter | Default   | Description    |
| --------- | --------- | -------------- |
| name      | undefined | String of name |

## Delete industry

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/admin/industry/:industry_name" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
  "message": "Industry has been removed.",
  "status": 200
}
```

This endpoint updates industry.

### HTTP Request

`DELETE https://api.linsta.nl/v1/admin/industry/:industry_name`

### Query Parameters

| Parameter     | Default   | Description             |
| ------------- | --------- | ----------------------- |
| industry_name | undefined | String of industry name |

## Get industry

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/industries" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "industries": [
        {
            "_id": "5deff89e0d7146299c84419e",
            "name": "Aannemer",
            "createdAt": "2020-01-07T00:44:15.231Z",
            "updatedAt": "2020-01-07T20:19:45.069Z",
            "__v": 0
        },
        {
            "_id": "5deff8a80d7146299c84419f",
            "name": "Badkamer specialist",
            "createdAt": "2020-01-07T00:44:15.231Z",
            "updatedAt": "2020-01-07T20:19:45.069Z",
            "__v": 0
        },
        {
            "_id": "5deff8d00d7146299c8441a0",
            "name": "Behanger",
            "createdAt": "2020-01-07T00:44:15.231Z",
            "updatedAt": "2020-01-07T20:19:45.069Z",
            "__v": 0
        },
        {
            "_id": "5deff8ea0d7146299c8441a1",
            "name": "Dakspecialist",
            "createdAt": "2020-01-07T00:44:15.231Z",
            "updatedAt": "2020-01-07T20:19:45.069Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves all available industries.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/industries`

## Serach category and steps

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/category" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "category": [
        {
            "keywords": [
                "Aanbouw",
                " Opbouw",
                " Aanbouw plaatsen",
                " Opbouw plaatsen",
                " Aanbouw of opbouw",
                " Aanbouw of opbouw plaatsen"
            ],
            "steps": [
                "5dffe9e9c579034d9380b959",
                "5dffe9e9c579034d9380b960",
                "5dffe9e9c579034d9380b95d"
            ],
            "images": [],
            "_id": "5dffe9e9c579034d9380b961",
            "serviceName": "Aanbouw of opbouw plaatsen",
            "industry": "Aannemer",
            "createdAt": "2019-12-22T22:10:49.323Z",
            "updatedAt": "2020-01-08T09:50:13.774Z",
            "__v": 2
        },
        {
            "keywords": [
                "Car",
                " Port",
                " Carport",
                " Carport plaatsen"
            ],
            "steps": [
                "5e002c9d21e54950c27dcc95",
                "5e002c9d21e54950c27dcc93"
            ],
            "images": [],
            "_id": "5e002c9d21e54950c27dcc96",
            "serviceName": "Carport plaatsen",
            "industry": "Aannemer",
            "createdAt": "2019-12-23T02:55:25.226Z",
            "updatedAt": "2020-01-03T10:27:18.300Z",
            "__v": 3
        },
        {
            "keywords": [
                "Af",
                " afvoeren",
                " afvoer",
                " grof",
                " vuil",
                " grofvuil"
            ],
            "steps": [
                "5e0f14b1739a279ebcfc732a",
                "5e0f14b1739a279ebcfc732e"
            ],
            "images": [],
            "_id": "5e0f14b1739a279ebcfc732f",
            "serviceName": "Afvoer puin / grof vuil",
            "industry": "Aannemer",
            "createdAt": "2020-01-03T10:17:21.411Z",
            "updatedAt": "2020-01-04T14:21:05.284Z",
            "__v": 0
        },
    ],
    "status": 200
}
```

This endpoint find category and steps via industry keyword.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/category`

### Body Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| industry  | undefined | String of industry |

## Get Admins

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "admins": [
        {
            "_id": "5dd585fd84501322bb9bcb07",
            "email": "nathan@scopeweb.nl",
            "userProfile": {
                "_id": "5dd56a4f84501322bb9bcb08",
                "firstName": "Nathan",
                "lastName": "Henniges"
            }
        }
    ],
    "status": 200
}
```

This endpoint retrieve list of admins.

### HTTP Request

`GET https://api.linsta.nl/v1/admin`

## Get regions

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/regions" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "regions": [
        {
            "active": false,
            "professionalCount": 0,
            "gigCount": 0,
            "userCount": 0,
            "_id": "5e0fa431cfad22318b0429ac",
            "name": "DR",
            "fullName": "Drenthe",
            "createdAt": "2020-01-03T20:29:37.241Z",
            "updatedAt": "2020-01-04T08:01:04.689Z",
            "__v": 0
        },
        {
            "active": false,
            "professionalCount": 0,
            "gigCount": 0,
            "userCount": 0,
            "_id": "5e0fa477cfad22318b0429ad",
            "name": "FL",
            "fullName": "Flevoland",
            "createdAt": "2020-01-03T20:30:47.140Z",
            "updatedAt": "2020-01-03T21:09:44.834Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieve list of regions.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/regions`

## Add region

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/geo/add-region" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{ "message": "Created new region", "status": 200 }
```

This endpoint add region.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/geo/add-region`

### Body Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| name      | undefined | String of industry |
| fullName  | undefined | String of fullName |
| active    | undefined | String of active   |

## Update region visibility

```shell
curl --location --request PUT "https://api.linsta.nl/v1/admin/geo/region-visibility/:regionId" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{ "message": "De zichtbaarheid van de provincie is gewijzigd", "status": 200 }
```

This endpoint update the visibility of a region (provincie)

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/geo/region-visibility/:regionId`

### Body Parameters

| Parameter | Default   | Description                   |
| --------- | --------- | ----------------------------- |
| status    | undefined | MongoDB Object ID of regionId |
| status    | undefined | String of status              |

## Create KB article

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/kb/create" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{ "message": "Knowledge base article has been created.", "status": 200 }
```

This endpoint update the visibility of a region (provincie)

### HTTP Request

`POST https://api.linsta.nl/v1/admin/kb/create`

### Body Parameters

| Parameter   | Default   | Description           |
| ----------- | --------- | --------------------- |
| title       | undefined | String of title       |
| category    | undefined | String of category    |
| description | undefined | String of description |
| userGroup   | undefined | String of userGroup   |

## Get KB articles

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/view-kb" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "articles": [
        {
            "feedback": [],
            "_id": "5e1f3b979354cc1fc3bf76ee",
            "title": "Leverage agile frameworks ",
            "category": {
                "_id": "5e1f7926efac6e58c731b346",
                "title": "Mijn Account",
                "description": "Account gerelateerde kennisbank FAQ vragen & antwoorden",
                "createdAt": "2020-01-15T20:42:14.071Z",
                "updatedAt": "2020-01-15T20:42:14.071Z",
                "__v": 0
            },
            "description": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
            "createdAt": "2020-01-15T16:19:35.642Z",
            "updatedAt": "2020-01-26T17:07:25.246Z",
            "__v": 0,
            "userGroup": "Leverage agile frameworks "
        }
    ],
    "status": 200
}
```

This endpoint update the visibility of a region (provincie)

### HTTP Request

`GET https://api.linsta.nl/v1/admin/view-kb`

### Query Parameters

| Parameter | Default   | Description         |
| --------- | --------- | ------------------- |
| category  | undefined | String of category  |
| userGroup | undefined | String of userGroup |

## Get KB categories

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/view/kb-categories" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "categories": [
        {
            "_id": "5e1f40ff95ed512bbbc6dd67",
            "title": "Een klus plaatsen",
            "description": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
            "createdAt": "2020-01-15T16:42:39.061Z",
            "updatedAt": "2020-01-15T16:42:39.061Z",
            "__v": 0
        },
        {
            "_id": "5e1f7926efac6e58c731b346",
            "title": "Mijn Account",
            "description": "Account gerelateerde kennisbank FAQ vragen & antwoorden",
            "createdAt": "2020-01-15T20:42:14.071Z",
            "updatedAt": "2020-01-15T20:42:14.071Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieve all the knowledge base categories.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/view/kb-categories`

### Query Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| userGroup | undefined | String of category |

## Create KB category

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/create/kb-category" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'title=Testing' \
  --data-urlencode 'description=This is a test.' \
  --data-urlencode 'userGroup=Test' \
```

>The above command returns JSON structured like this:

```json
{"message": "De categorie is aan de kennisbank toegevoegd.", "status": 200}
```

This endpoint create KB category.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/create/kb-category`

### Body Parameters

| Parameter   | Default   | Description           |
| ----------- | --------- | --------------------- |
| title       | undefined | String of title       |
| description | undefined | String of description |
| userGroup   | undefined | String of userGroup   |

## Edit KB article

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/edit/kb/:kb_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'title=Testing' \
  --data-urlencode 'category=Test' \
  --data-urlencode 'description=This is a test.' \
  --data-urlencode 'userGroup=Test' \
```

>The above command returns JSON structured like this:

```json
{"message": "Het kennisbank artikel is gewijzigd en opgeslagen.", "status": 200}
```

This endpoint edit a KB article.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/edit/kb/:kb_id`

### Body Parameters

| Parameter   | Default   | Description                     |
| ----------- | --------- | ------------------------------- |
| kb_id       | undefined | MongoDB Object ID of KB article |
| title       | undefined | String of title                 |
| description | undefined | String of description           |
| category    | undefined | String of category              |
| userGroup   | undefined | String of userGroup             |

## Get KB category infomation

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/view/kb-category/:category_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "category": {
        "_id": "5e1f40ff95ed512bbbc6dd67",
        "title": "Een klus plaatsen",
        "description": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
        "createdAt": "2020-01-15T16:42:39.061Z",
        "updatedAt": "2020-01-15T16:42:39.061Z",
        "__v": 0
    },
    "status": 200
}
```

This endpoint returns more category infomation.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/view/kb-category/:category_id`

### Body Parameters

| Parameter   | Default   | Description                      |
| ----------- | --------- | -------------------------------- |
| category_id | undefined | MongoDB Object ID of KB category |

## Edit KB category infomation

```shell
curl --location --request PUT "https://api.linsta.nl/v1/admin/edit/kb-category/:category_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'title=Great enterprise business.' \
  --data-urlencode 'description=Helped make my company a lot more enterprise by offering me great service at a great price.'
  --data-urlencode 'userGroup=Testing' \
```

>The above command returns JSON structured like this:

```json
{ "message": "Updated kb category", "status": 200 }
```

This endpoint updates kb category infomation

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/edit/kb-category/:category_id`

### Body Parameters

| Parameter   | Default   | Description                      |
| ----------- | --------- | -------------------------------- |
| category_id | undefined | MongoDB Object ID of KB category |
| title       | undefined | String of title                  |
| description | undefined | String of description            |
| userGroup   | undefined | String of userGroup              |

## Delete KB article

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/admin/edit/kb-category/:category_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{ "message": "Het kennisbank artikel is verwijderd", "status": 200 }
```

This endpoint removes single knowledge base article

### HTTP Request

`DELETE https://api.linsta.nl/v1/admin/edit/kb-category/:category_id`

### Body Parameters

| Parameter | Default   | Description             |
| --------- | --------- | ----------------------- |
| kb_id     | undefined | MongoDB Object ID of KB |

## Get applications

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/view/applications" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "applications": [
        {
            "_id": "5e29be6d2571812aeb1da531",
            "name": "John Doe",
            "email": "joe@doe.com",
            "motivation": "test",
            "photo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579794036/linsta/vacatures/profiel-foto/profiel-foto-HvLhgEPSL5s29gf2yVkKw2jU.jpg",
            "photoId": "profiel-foto-HvLhgEPSL5s29gf2yVkKw2jU",
            "resume": "http://localhost:8080/uploads/application/gTq8all2zYSeUzZasesbKt2p.pdf",
            "resumeId": "test-lIusdpLokadWoMoWqGw9MgRj",
            "createdAt": "2020-01-23T15:40:36.139Z",
            "updatedAt": "2020-01-23T15:40:36.139Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves job applications

### HTTP Request

`GET https://api.linsta.nl/v1/admin/view/applications`

### Query Parameters

| Parameter | Default   | Description                                  |
| --------- | --------- | -------------------------------------------- |
| date      | undefined | Sort by created supports (newest and oldest) |

## Get Feeedback

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/view/feedback" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "feedback": [
        {
            "_id": "5e2c8db7053d042e0887eeb6",
            "comment": "This is just a test",
            "feedbackType": "Good",
            "createdAt": "2020-01-25T18:49:27.475Z",
            "updatedAt": "2020-01-25T18:49:27.475Z",
            "__v": 0
        },
        {
            "_id": "5e2edcb4f960e1dad9ea3835",
            "comment": "This is just a test",
            "feedbackType": "Bad",
            "createdAt": "2019-01-25T18:49:27.475Z",
            "updatedAt": "2019-01-25T18:49:27.475Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieves feedback

### HTTP Request

`GET https://api.linsta.nl/v1/admin/view/feedback`

### Query Parameters

| Parameter    | Default   | Description                                  |
| ------------ | --------- | -------------------------------------------- |
| feedbackType | undefined | Sort by feedback type                        |
| date         | undefined | Sort by created supports (newest and oldest) |

## Delete image

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/delete-image/:image_name" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'reason=Bad image' \
```

>The above command returns JSON structured like this:

```json
{"message": "De afbeelding is verwijderd en de gebruiker is op de hoogte gebracht.", "status": 200}
```

This endpoint removes a image and sends the reason

### HTTP Request

`POST https://api.linsta.nl/v1/admin/delete-image/:image_name`

### Body Parameters

| Parameter  | Default   | Description                    |
| ---------- | --------- | ------------------------------ |
| image_name | undefined | Image name to remove           |
| reason     | undefined | Reason for image to be removed |

# Analytics

## View analytics

```shell
curl --location --request POST "https://api.linsta.nl/v1/analytics" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "reviews": {
        "posted": 0
    },
    "vacancies": {
        "posted": 0
    },
    "gig": {
        "professionals": {
            "selected": 0
        },
        "total": 1
    },
    "pitches": {
        "avgPrice": "2750.00",
        "sent": 2
    },
    "paying": {
        "total": 1
    },
    "status": 200
} 
```

This endpoint view analytics.

### HTTP Request

`GET https://api.linsta.nl/v1/analytics`

### Query Parameters

| Parameter | Default   | Description                |
| --------- | --------- | -------------------------- |
| region    | undefined | String of type of region   |
| industry  | undefined | String of type of industry |

## View Gigs

```shell
curl --location --request POST "https://api.linsta.nl/v1/analytics/gig" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "gigs": [
        {
            "location": {
                "type": "Point",
                "coordinates": [
                    52.17905700000001,
                    5.27834
                ]
            },
            "matchedProfessionals": [
                {
                    "gigStatus": 0,
                    "hasReplied": false,
                    "_id": "5e4303ec8cf85ee10b5e038b",
                    "professional": "5e3dc07d8a59d476a83f761e",
                    "industry": "Aannemer",
                    "gig": "5e4303ec8cf85ee10b5e038a",
                    "createdAt": "2020-02-11T19:43:40.261Z",
                    "updatedAt": "2020-02-11T19:43:40.261Z",
                    "__v": 0
                },
                {
                    "gigStatus": 2,
                    "hasReplied": false,
                    "_id": "5e4303ec8cf85ee10b5e038c",
                    "professional": "5e3db32c6389b859f05b598b",
                    "industry": "Aannemer",
                    "gig": "5e4303ec8cf85ee10b5e038a",
                    "createdAt": "2020-02-11T19:43:40.261Z",
                    "updatedAt": "2020-02-11T19:47:28.348Z",
                    "__v": 0
                }
            ],
            "approvedProfessionals": [
                {
                    "gigStatus": 2,
                    "hasReplied": false,
                    "_id": "5e4303ec8cf85ee10b5e038c",
                    "professional": "5e3db32c6389b859f05b598b",
                    "industry": "Aannemer",
                    "gig": "5e4303ec8cf85ee10b5e038a",
                    "createdAt": "2020-02-11T19:43:40.261Z",
                    "updatedAt": "2020-02-11T19:47:28.348Z",
                    "__v": 0
                }
            ],
            "invitedProfessionals": [],
            "declinedProfessionals": [],
            "underReviewProfessionals": [],
            "hasBeenUpdated": false,
            "pitches": [
                "5e4304668cf85ee10b5e0390"
            ],
            "_id": "5e4303ec8cf85ee10b5e038a",
            "title": "Aan - & uitbouw",
            "zipCode": "3762KG",
            "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec tincidunt augue at nunc elementum egestas. Sed id enim sit amet mi porttitor vehicula quis vel nunc. Suspendisse vel fermentum leo. In ex mi, bibendum eget nisl vel, euismod sodales ligula. Quisque posuere nisi dolor, sit amet dapibus purus fringilla ac. Nam nec erat gravida, aliquet urna nec, imperdiet tellus. Duis et consequat urna. Curabitur sed laoreet ante. Nulla quis dignissim elit. Aenean at diam posuere, posuere ex faucibus, imperdiet sem. Vivamus consectetur a nibh interdum semper. Mauris sit amet euismod nibh, sit amet viverra nibh. Nulla facilisi. Vestibulum quis tempus diam.",
            "projectPictures": [],
            "industry": "Aannemer",
            "consumer": "5e3dbfac8a59d476a83f7618",
            "budgetIndication": "€ 5000 - € 10.000",
            "city": "Soest",
            "steps": [
                {
                    "select": [],
                    "radio": [],
                    "checkbox": [],
                    "value": "100",
                    "fieldType": "other",
                    "title": "Wat is de grootte van de aan- of uitbouw in m2? ",
                    "ref": "5e2efe83123cb54da3be0d6d"
                },
                {
                    "select": [],
                    "radio": [
                        "Nee"
                    ],
                    "checkbox": [],
                    "fieldType": "radio",
                    "title": "Is een fundering noodzakelijk?",
                    "ref": "5e2efe83123cb54da3be0d6e"
                },
                {
                    "select": [],
                    "radio": [
                        "Plat dak"
                    ],
                    "checkbox": [],
                    "fieldType": "radio",
                    "title": "Welk soort dak wil je laten plaatsen?",
                    "ref": "5e2efe83123cb54da3be0d70"
                },
                {
                    "select": [],
                    "radio": [],
                    "checkbox": [],
                    "value": "6",
                    "fieldType": "other",
                    "title": "Hoeveel ramen wil je laten plaatsen?",
                    "ref": "5e2efe83123cb54da3be0d71"
                },
                {
                    "select": [],
                    "radio": [],
                    "checkbox": [],
                    "value": "2",
                    "fieldType": "other",
                    "title": "Hoeveel deuren wil je laten plaatsen?",
                    "ref": "5e2efe83123cb54da3be0d72"
                },
                {
                    "select": [],
                    "radio": [
                        "Nee"
                    ],
                    "checkbox": [],
                    "fieldType": "radio",
                    "title": "Heb je al bouwtekeningen?",
                    "ref": "5e2efe83123cb54da3be0d74"
                },
                {
                    "select": [],
                    "radio": [
                        "Nee - niet nodig"
                    ],
                    "checkbox": [],
                    "fieldType": "radio",
                    "title": "Heb je al een bouwvergunning?",
                    "ref": "5e2efe83123cb54da3be0d75"
                }
            ],
            "createdAt": "2020-02-11T19:43:40.269Z",
            "updatedAt": "2020-02-11T19:47:28.353Z",
            "orderNumber": 8403869585,
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint view analytics gigs.

### HTTP Request

`GET https://api.linsta.nl/v1/analytics/gig`

### Query Parameters

| Parameter | Default   | Description                                  |
| --------- | --------- | -------------------------------------------- |
| date      | undefined | String of date supported (newest and oldest) |
| budget    | undefined | String of the budget (must in database)      |

## View Pitches

```shell
curl --location --request POST "https://api.linsta.nl/v1/analytics/pitches" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "pitches": [
        {
            "_id": "5e4304668cf85ee10b5e0390",
            "owner": {
                "_id": "5e3db2c86389b859f05b5989",
                "businessProfile": {
                    "_id": "5e3db32c6389b859f05b598b",
                    "companyName": "Pro-Ject Klussenbedrijf"
                }
            },
            "gig": "5e4303ec8cf85ee10b5e038a",
            "price": 5500,
            "description": "Fusce euismod erat a ligula convallis lacinia. Nunc eu scelerisque arcu, vel mollis odio. Nulla eleifend mi erat, quis finibus purus condimentum ac. Donec ipsum orci, faucibus tristique rutrum sed, vehicula sed augue. Cras non enim eros. Maecenas bibendum lacinia luctus. Donec nisi lorem, mollis sed odio at, cursus luctus augue. Suspendisse porttitor tempor dolor, vel faucibus sapien fermentum at. Maecenas tempus nunc urna, quis sodales ipsum sagittis sed. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. In hendrerit massa nec ipsum rhoncus viverra. Nunc bibendum a lacus sed dapibus. Ut accumsan tempor neque, nec eleifend enim viverra non. Vivamus tristique sapien porttitor augue ornare commodo. Etiam suscipit sapien in mauris semper, id commodo nisi finibus.",
            "gigProfessional": "5e4303ec8cf85ee10b5e038c",
            "createdAt": "2020-02-11T19:45:42.228Z",
            "updatedAt": "2020-02-11T19:45:42.228Z",
            "pitchId": 7935188203,
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint view analytics pitches.

### HTTP Request

`GET https://api.linsta.nl/v1/analytics/pitches`

### Query Parameters

| Parameter | Default   | Description                                  |
| --------- | --------- | -------------------------------------------- |
| date      | undefined | String of date supported (newest and oldest) |
| priceFrom | undefined | String of priceFrom                          |
| priceTo   | undefined | String of priceTo                            |

## View Professionals

```shell
curl --location --request POST "https://api.linsta.nl/v1/analytics/professionals" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "professionals": [
        {
            "location": {
                "type": "Point",
                "coordinates": [
                    52.14384099999999,
                    5.5695808
                ]
            },
            "industries": [
                "Aannemer"
            ],
            "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "pageVisible": false,
            "accountLevel": "basic",
            "reviews": [],
            "activeSubscription": true,
            "_id": "5e3db32c6389b859f05b598b",
            "KvkNumber": "12345678",
            "companyName": "Pro-Ject Klussenbedrijf",
            "companyCity": "Barneveld",
            "companyAddress": "Straat 1",
            "companyZipCode": "3771ZD",
            "region": "GE",
            "firstName": "Pieter",
            "lastName": "Klus",
            "phone": "0181729191",
            "projectPictures": [],
            "pageSlug": "pro-ject-klussenbedrijf",
            "createdAt": "2020-02-07T18:57:48.488Z",
            "updatedAt": "2020-02-07T21:08:04.707Z",
            "avgReviews": 0,
            "__v": 0,
            "subscriptionLevel": "Professional"
        },
        {
            "location": {
                "type": "Point",
                "coordinates": [
                    52.1742004,
                    5.2848865
                ]
            },
            "industries": [
                "Aannemer"
            ],
            "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "pageVisible": false,
            "accountLevel": "basic",
            "reviews": [],
            "activeSubscription": false,
            "_id": "5e3dc07d8a59d476a83f761e",
            "KvkNumber": "12345678",
            "companyName": "Vakman 3",
            "companyCity": "Soest",
            "companyAddress": "Straat 1",
            "companyZipCode": "3762XK",
            "region": "UT",
            "firstName": "Vakman",
            "lastName": "MatchTest",
            "phone": "0181729191",
            "projectPictures": [],
            "pageSlug": "vakman-3",
            "createdAt": "2020-02-07T19:54:37.293Z",
            "updatedAt": "2020-02-07T19:54:37.293Z",
            "avgReviews": 0,
            "__v": 0
        },
        {
            "location": {
                "type": "Point",
                "coordinates": [
                    52.25661729999999,
                    6.2995715
                ]
            },
            "industries": [
                "Aannemer"
            ],
            "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "pageVisible": false,
            "accountLevel": "basic",
            "reviews": [],
            "activeSubscription": false,
            "_id": "5e3dc5908a59d476a83f7620",
            "KvkNumber": "12345678",
            "companyName": "Aap B.V.",
            "companyCity": "Apenhuizen",
            "companyAddress": "Straat 1",
            "companyZipCode": "7437SB",
            "region": "Overste",
            "firstName": "Test",
            "lastName": "Aap",
            "phone": "0612345678",
            "projectPictures": [],
            "pageSlug": "aap-bv",
            "createdAt": "2020-02-07T20:16:16.292Z",
            "updatedAt": "2020-02-07T20:16:16.292Z",
            "avgReviews": 0,
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint view analytics professionals.

### HTTP Request

`GET https://api.linsta.nl/v1/analytics/professionals`

### Query Parameters

| Parameter          | Default   | Description                                  |
| ------------------ | --------- | -------------------------------------------- |
| createdAt          | undefined | String of date supported (newest and oldest) |
| avgReviews         | undefined | String of avgReviews                         |
| activeSubscription | undefined | String of true or false                      |

## View users

```shell
curl --location --request POST "https://api.linsta.nl/v1/analytics/users" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "user": [
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "admin",
            "_id": "5dc16583e67a00461058ae2d",
            "accountType": "admin",
            "createdAt": "2019-11-05T12:05:23.127Z",
            "userProfile": {
                "_id": "5dc16727e67a00461058ae2e",
                "firstName": "Admin",
                "lastName": "Account",
                "street": "Straat 1",
                "zipCode": "1234AB",
                "city": "Brielle",
                "phone": "0612345678",
                "createdAt": "2019-11-05T12:12:23.675Z",
                "updatedAt": "2019-11-12T16:08:19.847Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "admin",
            "_id": "5dc431ddf522236be10ca75b",
            "accountType": "admin",
            "createdAt": "2019-11-07T15:01:49.084Z",
            "userProfile": {
                "_id": "5dc43209f522236be10ca75c",
                "firstName": "Amy",
                "lastName": "Anderson",
                "street": "Van Galenstraat 5",
                "zipCode": "3071AG",
                "city": "Rotterdam",
                "phone": "0612345678",
                "createdAt": "2019-11-07T15:02:33.083Z",
                "updatedAt": "2019-11-07T15:02:33.083Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "admin",
            "_id": "5dc58ab69f2c053aeb04ed01",
            "accountType": "admin",
            "createdAt": "2019-11-08T15:33:10.288Z",
            "userProfile": {
                "_id": "5dc43209f522236be10ca85c",
                "firstName": "Wieger",
                "lastName": "van Ooijen",
                "street": "Straat 1",
                "zipCode": "1234AB",
                "city": "Leusden",
                "phone": "0612345678",
                "createdAt": "2019-11-07T15:02:33.083Z",
                "updatedAt": "2019-11-08T15:41:15.305Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579191185/linsta/vakmannen/portfolio/project-afbeelding-65882723.jpg",
            "role": "admin",
            "_id": "5dd569fd84501322bb9bcb07",
            "accountType": "developer",
            "createdAt": "2019-11-20T16:29:49.967Z",
            "userProfile": {
                "_id": "5dd56a4f84501322bb9bcb08",
                "firstName": "Nathan",
                "lastName": "Henniges",
                "street": " Wielingen 8",
                "zipCode": "3232HH",
                "city": "Brielle",
                "phone": "6084666280",
                "createdAt": "2019-11-20T16:31:11.154Z",
                "updatedAt": "2019-11-20T16:31:11.154Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "admin",
            "_id": "5dd570d1873225ab198e47d4",
            "accountType": "developer",
            "createdAt": "2019-11-20T16:58:57.568Z",
            "userProfile": {
                "_id": "5dd570f7873225ab198e47d5",
                "firstName": "Stephan",
                "lastName": "Moerman",
                "street": "Wielingen 8",
                "zipCode": "3232HH",
                "city": "Brielle",
                "phone": "0612434923",
                "createdAt": "2019-11-20T16:59:35.240Z",
                "updatedAt": "2019-11-20T16:59:35.240Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "consument",
            "_id": "5de1a0ee54d8b4755fec5e35",
            "accountType": "consument",
            "createdAt": "2019-11-29T22:51:26.995Z",
            "userProfile": {
                "_id": "5de1a10054d8b4755fec5e36",
                "firstName": "Admin",
                "lastName": "Name",
                "street": "Street 1",
                "zipCode": "1234 AB",
                "city": "Amsterdam",
                "phone": "06712212746217",
                "createdAt": "2019-11-29T22:51:44.032Z",
                "updatedAt": "2019-11-29T22:51:44.032Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "vakman",
            "_id": "5e3db2c86389b859f05b5989",
            "accountType": "vakman",
            "createdAt": "2020-02-07T18:56:08.688Z"
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "consument",
            "_id": "5e3dbfac8a59d476a83f7618",
            "accountType": "consument",
            "createdAt": "2020-02-07T19:51:08.419Z",
            "userProfile": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        52.1171789,
                        5.404344
                    ]
                },
                "_id": "5e3dbfc58a59d476a83f7619",
                "firstName": "Jan",
                "lastName": "Jansen",
                "street": "straatnaam 1",
                "zipCode": "3832CK",
                "region": "UT",
                "city": "Amersfoort",
                "phone": "06123456789",
                "createdAt": "2020-02-07T19:51:33.978Z",
                "updatedAt": "2020-02-07T19:51:33.978Z",
                "__v": 0
            }
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "vakman",
            "_id": "5e3dc02f8a59d476a83f761d",
            "accountType": "vakman",
            "createdAt": "2020-02-07T19:53:19.584Z"
        },
        {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "vakman",
            "_id": "5e3dc56a8a59d476a83f761f",
            "accountType": "vakman",
            "createdAt": "2020-02-07T20:15:38.156Z"
        }
    ],
    "status": 200
}
```

This endpoint view analytics users.

### HTTP Request

`GET https://api.linsta.nl/v1/analytics/users`

### Query Parameters

| Parameter        | Default   | Description                                  |
| ---------------- | --------- | -------------------------------------------- |
| profileCompleted | undefined | String of profileCompleted                   |
| accountType      | undefined | String of accountType                        |
| createdAt        | undefined | String of date supported (newest and oldest) |

# Contact

## Add contact

```shell
curl --location --request POST "https://api.linsta.nl/v1/contact" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'name=Test'
  --data-urlencode 'email=example@example.com'
  --data-urlencode 'subject=Test Subject 9001'
  --data-urlencode 'message=I wanted to contact you.'
```

>The above command returns JSON structured like this:

```json
{ "success": "Your message has been sent.", "status": 200 }  
```

This endpoint creates a new contact.

### HTTP Request

`POST https://api.linsta.nl/v1/contact`

### Body Parameters

| Parameter | Default   | Description       |
| --------- | --------- | ----------------- |
| name      | undefined | String of name    |
| email     | undefined | String of email   |
| subject   | undefined | String of subject |
| message   | undefined | String of message |

# Geo

## Calculate the distance

```shell
curl --location --request POST "https://api.linsta.nl/v1/geo/distance" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'zipCodeFrom=12564'
  --data-urlencode 'zipCodeTo=12365'
```

>The above command returns JSON structured like this:

```json
{ "success": "Your message has been sent.", "status": 200 }  
```

This endpoint calculate the distance between two zipcodes.

### HTTP Request

`POST https://api.linsta.nl/v1/geo/distance`

### Body Parameters

| Parameter   | Default   | Description            |
| ----------- | --------- | ---------------------- |
| zipCodeFrom | undefined | String of from zipcode |
| zipCodeTo   | undefined | String of to zipcode   |

# Newsletter

## Subscribe to newsletter

```shell
curl --location --request POST "https://api.linsta.nl/v1/newsletter/subscribe" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=example@example.com'
```

>The above command returns JSON structured like this:

```json
{ "success": "Bedankt voor uw inschrijving voor de Linsta nieuwsbrief, u blijft nu op de hoogte van de laatste nieuwtjes", "status": 200 }  
```

This endpoint subscribes the email to the newsletter.

### HTTP Request

`POST https://api.linsta.nl/v1/newsletter/subscribe`

### Body Parameters

| Parameter | Default   | Description     |
| --------- | --------- | --------------- |
| email     | undefined | String of email |

# Lead

## Import Leads

```shell
curl --location --request POST "https://api.linsta.nl/v1/lead/import" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --form 'file=@/C:/Users/scopeweb B.V/Downloads/leads.csv'
```

>The above command returns JSON structured like this:

```json
{ "success": "CSV has been imported", "status": 200 }  
```

This endpoint upload and import a CSV.

### HTTP Request

`POST https://api.linsta.nl/v1/lead/import`

### Body Parameters

| Parameter | Default   | Description |
| --------- | --------- | ----------- |
| file      | undefined | CSV file    |

## View imported leads

```shell
curl --location --request GET "https://api.linsta.nl/v1/lead/view-all" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "lead": [
        {
            "_id": "5e42fe0b25f60cc43d1cdf6f",
            "businessName": "bedrijfsnaam",
            "street": "Straatnaam",
            "number": 20,
            "numberAddition": "",
            "zipCode": "1234 AB",
            "city": "STAD",
            "province": "ZH",
            "phoneNumber": "06-12345678",
            "email": "email@email.nl",
            "url": "www.website.nl",
            "mainLocation": "Ja",
            "kvkNumber": 12345678,
            "branche": 4120,
            "businessDescription": "Algemene burgerlijke en utiliteitsbouw",
            "createdAt": "2020-02-11T19:18:35.129Z",
            "updatedAt": "2020-02-11T19:18:35.129Z",
            "__v": 0
        },
        {
            "_id": "5e42fe0b45f60cc43d1cdf70",
            "businessName": "bedrijfsnaam.",
            "street": "Straatnaam",
            "number": 1,
            "numberAddition": "",
            "zipCode": "1234 AB",
            "city": "STAD",
            "province": "ZH",
            "phoneNumber": "06-12345678",
            "email": "email@email.nl",
            "url": "www.website.nl",
            "mainLocation": "Ja",
            "kvkNumber": 12345678,
            "branche": 4120,
            "businessDescription": "Algemene burgerlijke en utiliteitsbouw",
            "createdAt": "2020-02-11T19:18:35.130Z",
            "updatedAt": "2020-02-11T19:18:35.130Z",
            "__v": 0
        }
    ],
    "status": 200
} 
```

This endpoint shows all the leads in a array.

### HTTP Request

`GET https://api.linsta.nl/v1/lead/view-all`

# Utility

## View budgets

```shell
curl --location --request GET "https://api.linsta.nl/v1/utility/budgets" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "budgets": [
        {
            "_id": "5e1fb0506ccd161000c8690f",
            "budget": "€ 1500 of minder",
            "__v": 0
        },
        {
            "_id": "5e1fb0656ccd161000c86910",
            "budget": "€ 1500 - € 5000",
            "__v": 0
        },
        {
            "_id": "5e1fb06b6ccd161000c86911",
            "budget": "€ 5000 - € 10.000",
            "__v": 0
        },
        {
            "_id": "5e1fb0726ccd161000c86912",
            "budget": "€ 10.000 of meer",
            "__v": 0
        },
        {
            "_id": "5e1fb0776ccd161000c86913",
            "budget": "Nader te bepalen",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint retrieve available budgets.

### HTTP Request

`GET https://api.linsta.nl/v1/utility/budgets`

## Add feedback

```shell
curl --location --request POST "https://api.linsta.nl/v1/utility/feedback" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'description=This is great.' \
  --data-urlencode 'feedbackType=Good' 
```

>The above command returns JSON structured like this:

```json
{ "message": "Uw feedback is verstuurd", "status": 200 }
```

This endpoint adds feedback.

### HTTP Request

`POST https://api.linsta.nl/v1/utility/feedback`

### Body Parameters

| Parameter    | Default   | Description                |
| ------------ | --------- | -------------------------- |
| description  | undefined | String of the description  |
| feedbackType | undefined | String of the service name |
