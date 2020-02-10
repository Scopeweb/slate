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
curl --location --request POST "https://dev.linsta.nl/v1/admin/categories/add-category" \
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

`POST https://dev.linsta.nl/v1/admin/categories/add-category`

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
curl --location --request POST "https://dev.linsta.nl/v1/admin/place-jobs/add-fieldtype" \
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

`POST https://dev.linsta.nl/v1/admin/place-jobs/add-fieldtype`

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
curl --location --request DELETE "https://dev.linsta.nl/v1/admin/category/:job_id" \
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

`DELETE https://dev.linsta.nl/v1/admin/place-jobs/fieldtypes`

## Get Place Job fieldtypes

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/place-jobs/fieldtypes" \
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

`GET https://dev.linsta.nl/v1/admin/place-jobs/fieldtypes`

## Get reviews

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/reviews" \
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

`GET https://dev.linsta.nl/v1/admin/reviews`

## Get reviews with fitler

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/reviews/:filter_type" \
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

`GET https://dev.linsta.nl/v1/admin/reviews/:filter_type`

### Query Parameters

| Parameter   | Default   | Description                                                        |
| ----------- | --------- | ------------------------------------------------------------------ |
| filter_type | undefined | Type of filter.  Supported ones are newest, oldest, rateHL, rateLH |
| industry    | undefined | String ofindustry name                                             |

## Get categories

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/list-categories" \
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

`GET https://dev.linsta.nl/v1/admin/list-categories`

## Get categories by industry

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/list-categories/:industryName" \
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

`GET https://dev.linsta.nl/v1/admin/list-categories/:industryName`

### Query Parameters

| Parameter    | Default   | Description            |
| ------------ | --------- | ---------------------- |
| industryName | undefined | String ofindustry name |

## Get category with steps

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/category/:category_id" \
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

`GET https://dev.linsta.nl/v1/admin/category/:category_id`

### Query Parameters

| Parameter   | Default   | Description                        |
| ----------- | --------- | ---------------------------------- |
| category_id | undefined | MongoDB Object ID of the  category |

## Update category

```shell
curl --location --request PUT "https://dev.linsta.nl/v1/admin/update-category/:category_id" \
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

`PUT https://dev.linsta.nl/v1/admin/update-category/:category_id`

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
curl --location --request PUT "https://dev.linsta.nl/v1/admin/category/add-question/:step_id" \
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

`PUT https://dev.linsta.nl/v1/admin/category/add-question/:step_id`

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
curl --location --request DELETE "https://dev.linsta.nl/v1/admin/category/:question_id/:step_id" \
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

`DELETE https://dev.linsta.nl/v1/admin/category/:question_id/:step_id`

### Query Parameters

| Parameter   | Default   | Description                       |
| ----------- | --------- | --------------------------------- |
| step_id     | undefined | MongoDB Object ID of the step     |
| question_id | undefined | MongoDB Object ID of the question |

## Update category question order

```shell
curl --location --request PUT "https://dev.linsta.nl/v1/admin/category/update-step/:step_id" \
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

`PUT https://dev.linsta.nl/v1/admin/category/update-step/:step_id`

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
curl --location --request POST "https://dev.linsta.nl/v1/admin/category/delete-step/:job_id" \
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

`POST https://dev.linsta.nl/v1/admin/category/delete-step/:job_id`

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
curl --location --request POST "https://dev.linsta.nl/v1/admin/industry" \
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

`POST https://dev.linsta.nl/v1/admin/industry`

### Body Parameters

| Parameter | Default   | Description    |
| --------- | --------- | -------------- |
| name      | undefined | String of name |

## Update industry

```shell
curl --location --request POST "https://dev.linsta.nl/v1/admin/industry/:industry_name" \
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

`POST https://dev.linsta.nl/v1/admin/industry/:industry_name`

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
curl --location --request DELETE "https://dev.linsta.nl/v1/admin/industry/:industry_name" \
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

`DELETE https://dev.linsta.nl/v1/admin/industry/:industry_name`

### Query Parameters

| Parameter     | Default   | Description             |
| ------------- | --------- | ----------------------- |
| industry_name | undefined | String of industry name |

## Get industry

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin/industries" \
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

`GET https://dev.linsta.nl/v1/admin/industries`

## Serach category and steps

```shell
curl --location --request POST "https://dev.linsta.nl/v1/admin/category" \
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

`POST https://dev.linsta.nl/v1/admin/category`

### Body Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| industry  | undefined | String of industry |

## Get Admins

```shell
curl --location --request GET "https://dev.linsta.nl/v1/admin" \
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

`GET https://dev.linsta.nl/v1/admin`

## Get regions

```shell
curl --location --request POST "https://dev.linsta.nl/v1/admin/regions" \
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

`GET https://dev.linsta.nl/v1/admin/regions`
