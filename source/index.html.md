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

## Add gig category

```shell
curl --location --request POST "https://api.linsta.nl/v1/admin/categories/add-category" \
  -H "Authorization: Bearer jsonwebtoken" \
  --header 'Content-Type: application/json' \
  --data-raw '{
    "serviceName": "Test",
    "industry": "Klusbedrijf",
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

This endpoint allows admins to create a new gig category.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/categories/add-category`

### Body Parameters

| Parameter   | Default   | Description                 |
| ----------- | --------- | --------------------------- |
| steps       | undefined | Array of steps              |
| serviceName | undefined | Service name                |
| images      | undefined | Images                      |
| industry    | undefined | Industry name               |

## Add gig category fieldtype

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

This endpoint allows admins to create a new fieldtype.

### HTTP Request

`POST https://api.linsta.nl/v1/admin/place-jobs/add-fieldtype`

### Body Parameters

| Parameter   | Default   | Description                 |
| ----------- | --------- | --------------------------- |
| type        | undefined | Type of field               |
| inputType   | undefined | Input type for the field    |
| name        | undefined | Name for the field          |
| description | undefined | Description for the field   |
| industry    | undefined | Industry name               |

<aside class="warning">
Developers only
</aside>

## Delete gig category

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

This endpoint allows admins to delete a category.

### HTTP Request

`DELETE https://api.linsta.nl/v1/admin/category/:job_id`

## Retrieve gig fieldtypes

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

This endpoint allows admins to retrieve all available fieldtypes.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/place-jobs/fieldtypes`

## Retrieve a Gig by it's ID

```shell
curl --location --request GET "https://api.linsta.nl/v1/admin/view-gig/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "gig": {
        "location": {
            "type": "Point",
            "coordinates": [
                51.8975292,
                4.172136099999999
            ]
        },
        "matchedProfessionals": [
            {
                "gigStatus": 0,
                "hasReplied": false,
                "_id": "5e4d860321848d2cd157b9c7",
                "professional": "5e09b6027521a16081b1b389",
                "industry": "Aannemer",
                "gig": "5e4d860321848d2cd157b9c6",
                "createdAt": "2020-02-19T19:01:23.575Z",
                "updatedAt": "2020-02-19T19:01:23.575Z",
                "__v": 0
            },
            {
                "gigStatus": 0,
                "hasReplied": false,
                "_id": "5e4d860321848d2cd157b9c8",
                "professional": "5e19ec5a2156e739680c6e71",
                "industry": "Aannemer",
                "gig": "5e4d860321848d2cd157b9c6",
                "createdAt": "2020-02-19T19:01:23.575Z",
                "updatedAt": "2020-02-19T19:01:23.575Z",
                "__v": 0
            },
            {
                "gigStatus": 0,
                "hasReplied": false,
                "_id": "5e4d860321848d2cd157b9c9",
                "professional": "5e19ebb45afd28391470b121",
                "industry": "Aannemer",
                "gig": "5e4d860321848d2cd157b9c6",
                "createdAt": "2020-02-19T19:01:23.575Z",
                "updatedAt": "2020-02-19T19:01:23.575Z",
                "__v": 0
            },
            {
                "gigStatus": 0,
                "hasReplied": false,
                "_id": "5e4d860321848d2cd157b9ca",
                "professional": "5e24f48a998f1077b7982991",
                "industry": "Aannemer",
                "gig": "5e4d860321848d2cd157b9c6",
                "createdAt": "2020-02-19T19:01:23.576Z",
                "updatedAt": "2020-02-19T19:01:23.576Z",
                "__v": 0
            }
        ],
        "approvedProfessionals": [],
        "invitedProfessionals": [],
        "declinedProfessionals": [],
        "underReviewProfessionals": [],
        "hasBeenUpdated": false,
        "pitches": [],
        "_id": "5e4d860321848d2cd157b9c6",
        "title": "Aan - & uitbouw",
        "zipCode": "3232HB",
        "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Fusce accumsan purus ut dui vulputate suscipit. Quisque rutrum elit at turpis luctus faucibus. Vestibulum mauris diam, interdum non lectus eget, aliquet faucibus est. Pellentesque ultrices nisl ut justo maximus convallis. Donec faucibus nibh nec urna faucibus varius. Fusce quis arcu vel nisl tristique pharetra porta vel leo. Etiam aliquet cursus eros quis porttitor. Quisque consequat, metus eget suscipit semper, risus eros congue mi, ultrices bibendum orci risus vel neque. Morbi eget lorem eu velit malesuada consequat. Donec dictum lorem sit amet eros viverra varius. Integer pellentesque lacinia facilisis. Phasellus tempor laoreet justo eget dapibus. Nunc quis sapien ut magna commodo luctus in ac nisl. Praesent mauris dui, fermentum elementum libero eget, pretium congue leo. Nam quis risus pulvinar, egestas purus vel, molestie tellus. Ut finibus ultrices erat, sed gravida ligula imperdiet at.",
        "projectPictures": [
            {
                "src": "https://res.cloudinary.com/scope-web-llc/image/upload/v1582138868/linsta/opdrachten/klus-afbeelding/klus-afbeelding-13905611.jpg",
                "fileName": "klus-afbeelding-13905611"
            }
        ],
        "industry": "Aannemer",
        "consumer": {
            "profileCompleted": true,
            "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
            "role": "consument",
            "notifications": "daily",
            "newsletter": true,
            "twoFactor": false,
            "bookmarkedBusinesses": [
                "5dcdb0369eb3bb1308bd87a1"
            ],
            "_id": "5dca7a9a3d5cc53294ff0cff",
            "email": "gebruiker@demo.nl",
            "accountType": "consument",
            "lastLogin": "2020-02-19T19:01:22.070Z",
            "createdAt": "2019-11-12T09:25:46.951Z",
            "updatedAt": "2020-02-19T19:01:22.073Z",
            "__v": 1,
            "userProfile": "5dca7ab63d5cc53294ff0d00"
        },
        "budgetIndication": "1500 - 5000",
        "city": "Brielle",
        "leadValue": 3250,
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
        "startDateText": "Zo snel mogelijk",
        "createdAt": "2020-02-19T19:01:23.772Z",
        "updatedAt": "2020-02-19T19:01:23.772Z",
        "orderNumber": 6367614460,
        "__v": 0
    },
    "status": 200
}
```

This endpoint allows admins to retrieve a single Gig by it's ID.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/view-gig/:gig_id`

## Retrieve all available reviews

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

This endpoint allows admins to retrieve all available reviews.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/reviews`

## Retrieve reviews by filter

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

This endpoint allows admins to retrieve all reviews after filtering them by industry or filter_type.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/reviews/:filter_type`

### Query Parameters

| Parameter   | Default   | Description                                                        |
| ----------- | --------- | ------------------------------------------------------------------ |
| filter_type | undefined | Type of filter.  Supported ones are newest, oldest, rateHL, rateLH |
| industry    | undefined | The industry name used for filtering                               |

## Retrieve available categories

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

This endpoint allows admins to retrieve all available categories.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/list-categories`

## Retrieve categories

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

This endpoint allows an admin to retrieve all available categories.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/list-categories/:industryName`

### Query Parameters

| Parameter    | Default   | Description            |
| ------------ | --------- | ---------------------- |
| industryName | undefined | Industry name          |

## Retrieve category by ID

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

This endpoint allows an admin to retrieve a category by it's ID.

### HTTP Request

`GET https://api.linsta.nl/v1/admin/category/:category_id`

### Query Parameters

| Parameter   | Default   | Description                        |
| ----------- | --------- | ---------------------------------- |
| category_id | undefined | Category ID                        |

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

This endpoint allows admins to update a category.

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/update-category/:category_id`

### Query Parameters

| Parameter   | Default   | Description                        |
| ----------- | --------- | ---------------------------------- |
| category_id | undefined | Step ID                            |

### Body Parameters

| Parameter    | Default   | Description             |
| ------------ | --------- | ----------------------- |
| industryName | undefined | Industry name           |
| serviceName  | undefined | Service name            |

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

This endpoint allows admins to add a question to step, used in categories.

### HTTP Request

`PUT https://api.linsta.nl/v1/admin/category/add-question/:step_id`

### Query Parameters

| Parameter | Default   | Description                   |
| --------- | --------- | ----------------------------- |
| step_id   | undefined | MongoDB Object ID of the step |

### Body Parameters

| Parameter   | Default   | Description           |
| ----------- | --------- | --------------------- |
| type        | undefined | Question type         |
| icon        | undefined | Icon (optional)       |
| label       | undefined | Question label        |
| required    | undefined | Field required status |
| readOnly    | undefined | Read only status      |
| disabled    | undefined | Disabled input status |
| isActive    | undefined | Status for the input  |
| placeholder | undefined | Input placeholder     |

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

This endpoint allows an admin to delete a question from a step.

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
| imageType  | undefined | Type of image (gig or gallery) |
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
                "phone": "123456789",
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

# Auth

## Signup

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/register" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=nathan@scopeweb.nl' \
  --data-urlencode 'password=thisisapassword' \
  --data-urlencode 'accountType=developer' \
  --data-urlencode 'role=developer'
```

>The above command returns JSON structured like this:

```json
{ "message": "Registration successful.", "status": 200 }
```

This endpoint creates a new user.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/register`

### Body Parameters

| Parameter   | Default   | Description               |
| ----------- | --------- | ------------------------- |
| email       | undefined | String of the email       |
| password    | undefined | String of the password    |
| accountType | undefined | String of the accountType |
| role        | undefined | String of the role        |

## Login

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/login" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=nathan@scopeweb.nl' \
  --data-urlencode 'password=thisisapassword' 
```

>The above command returns JSON structured like this:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkZDU2OWZkODQ1MDEzMjJiYjliY2IwNyIsImF2YXRhciI6Imh0dHBzOi8vcmVzLmNsb3VkaW5hcnkuY29tL3Njb3BlLXdlYi1sbGMvaW1hZ2UvdXBsb2FkL3YxNTc5MTkxMTg1L2xpbnN0YS92YWttYW5uZW4vcG9ydGZvbGlvL3Byb2plY3QtYWZiZWVsZGluZy02NTg4MjcyMy5qcGciLCJyb2xlIjoiYWRtaW4iLCJpYXQiOjE1ODE1MTk4MTYsImV4cCI6MTU4MTU2MzAxNn0.645Mpm9V0sBhepNX0Ij8M0Hh7k7ECKzIDvDUZV6a7G4",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkZDU2OWZkODQ1MDEzMjJiYjliY2IwNyIsImF2YXRhciI6Imh0dHBzOi8vcmVzLmNsb3VkaW5hcnkuY29tL3Njb3BlLXdlYi1sbGMvaW1hZ2UvdXBsb2FkL3YxNTc5MTkxMTg1L2xpbnN0YS92YWttYW5uZW4vcG9ydGZvbGlvL3Byb2plY3QtYWZiZWVsZGluZy02NTg4MjcyMy5qcGciLCJyb2xlIjoiYWRtaW4iLCJpYXQiOjE1ODE1MTk4MTYsImV4cCI6MTU4MTU2MzAxNn0.645Mpm9V0sBhepNX0Ij8M0Hh7k7ECKzIDvDUZV6a7G4",
    "twoFactor": false,
    "status": 200
}
```

This endpoint login the user and returns a jwt token.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/login`

### Body Parameters

| Parameter | Default   | Description            |
| --------- | --------- | ---------------------- |
| email     | undefined | String of the email    |
| password  | undefined | String of the password |

## Login with Two Factor

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/login-2fa/:token" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkZDU2OWZkODQ1MDEzMjJiYjliY2IwNyIsImF2YXRhciI6Imh0dHBzOi8vcmVzLmNsb3VkaW5hcnkuY29tL3Njb3BlLXdlYi1sbGMvaW1hZ2UvdXBsb2FkL3YxNTc5MTkxMTg1L2xpbnN0YS92YWttYW5uZW4vcG9ydGZvbGlvL3Byb2plY3QtYWZiZWVsZGluZy02NTg4MjcyMy5qcGciLCJyb2xlIjoiYWRtaW4iLCJpYXQiOjE1ODE1MTk4MTYsImV4cCI6MTU4MTU2MzAxNn0.645Mpm9V0sBhepNX0Ij8M0Hh7k7ECKzIDvDUZV6a7G4",
    "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkZDU2OWZkODQ1MDEzMjJiYjliY2IwNyIsImF2YXRhciI6Imh0dHBzOi8vcmVzLmNsb3VkaW5hcnkuY29tL3Njb3BlLXdlYi1sbGMvaW1hZ2UvdXBsb2FkL3YxNTc5MTkxMTg1L2xpbnN0YS92YWttYW5uZW4vcG9ydGZvbGlvL3Byb2plY3QtYWZiZWVsZGluZy02NTg4MjcyMy5qcGciLCJyb2xlIjoiYWRtaW4iLCJpYXQiOjE1ODE1MTk4MTYsImV4cCI6MTU4MTU2MzAxNn0.645Mpm9V0sBhepNX0Ij8M0Hh7k7ECKzIDvDUZV6a7G4",
    "twoFactor": true,
    "status": 200
}
```

This endpoint login the user and returns a jwt token.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/login-2fa/:token`

### Body Parameters

| Parameter | Default   | Description                   |
| --------- | --------- | ----------------------------- |
| token     | undefined | String of the two factor code |


## Resend Two Factor

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/login-2fa/resend" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=nathan@scopeweb.nl' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Two Factor token has been sent to your email.",
  "twoFactor": true,
  "status": 200
}
```

This endpoint resends a two factor token to the user email

### HTTP Request

`POST https://api.linsta.nl/v1/auth/login-2fa/resend`

### Body Parameters

| Parameter | Default   | Description         |
| --------- | --------- | ------------------- |
| email     | undefined | String of the email |

## Complate Profile

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/complete-profile" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'companyZipCode=3232HE' 
  --data-urlencode 'email=nathan@scopeweb.nl' 
  --data-urlencode 'industries=Aannemer,Elektricien,Metselaar,Verhuisbedrijf' 
  --data-urlencode 'KvKnumber=12345678' 
  --data-urlencode 'companyName=Vakman' 
  --data-urlencode 'companyCity=IJsselmuiden' 
  --data-urlencode 'firstName=Test' 
  --data-urlencode 'lastName=Vakman 1'
  --data-urlencode 'phone=0612345678'
  --data-urlencode 'street=Straat 1'
  --data-urlencode 'zipCode=3544 CL'
  --data-urlencode 'city=Woonplaats'
```

>The above command returns JSON structured like this:

```json
{
      "success": "Uw Linsta account is succesvol geactiveerd",
      status: 200
}
```

This endpoint complates the user or business profile.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/complete-profile`

### Body Parameters

| Parameter      | Default   | Description                                                 |
| -------------- | --------- | ----------------------------------------------------------- |
| companyZipCode | undefined | If account type is vakman use string companyZipCode         |
| industries     | undefined | If account type is vakman use string industries             |
| KvKnumber      | undefined | If account type is vakman use string KvKnumber              |
| companyName    | undefined | If account type is vakman use string companyName            |
| companyCity    | undefined | If account type is vakman use string companyCity            |
| companyAddress | undefined | If account type is vakman use string companyAddress         |
| firstName      | undefined | If account type is vakman or consument use string firstName |
| lastName       | undefined | If account type is vakman or consument use string lastName  |
| phone          | undefined | If account type is vakman or consument  use string phone    |
| street         | undefined | If account type is consument use string street              |
| zipCode        | undefined | If account type is consument use string zipCode             |
| city           | undefined | If account type is consument use string city                |

## Verify Token

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/verify-token" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkZDU2OWZkODQ1MDEzMjJiYjliY2IwNyIsImF2YXRhciI6Imh0dHBzOi8vcmVzLmNsb3VkaW5hcnkuY29tL3Njb3BlLXdlYi1sbGMvaW1hZ2UvdXBsb2FkL3YxNTc5MTkxMTg1L2xpbnN0YS92YWttYW5uZW4vcG9ydGZvbGlvL3Byb2plY3QtYWZiZWVsZGluZy02NTg4MjcyMy5qcGciLCJyb2xlIjoiYWRtaW4iLCJpYXQiOjE1ODE1NDY1ODUsImV4cCI6MTU4MTYzMjk4NX0.-04ZyxTDT1A0rjdOxrF8Pizigbqfv-Jp4jfKHTp2RSo",
    "expiresIn": "2020-02-13T22:29:45.272Z",
    "status": 200
}
```

This endpoint verify token and returns a new one.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/verify-token`

## Forgot Password

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/forgot-password" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=nathan@scopeweb.nl' 
```

>The above command returns JSON structured like this:

```json
{
  "success": "We hebben een e-mail verstuurd naar ${req.body.email} met verdere instructies",
  "status": 200
}
```

This endpoint login the user and returns a jwt token.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/forgot-password`

| Parameter | Default   | Description     |
| --------- | --------- | --------------- |
| email     | undefined | String of email |

## Reset Password with Token

```shell
curl --location --request GET "https://api.linsta.nl/v1/auth/forgot-password/:token" 
```

>The above command returns JSON structured like this:

```json
{ "success": "Uw nieuwe wachtwoord is opgeslagen", "status": 200 }
```

This endpoint process password reset token.

### HTTP Request

`POST https://api.linsta.nl/v1/auth/forgot-password/:token`

| Parameter | Default   | Description                    |
| --------- | --------- | ------------------------------ |
| token     | undefined | String of password reset token |

# Helpdesk

## Create ticket

```shell
curl --location --request POST "https://api.linsta.nl/v1/helpdesk/create-ticket" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'type=Critical issue' \
  --data-urlencode 'tags=test,test 2,test 3' \
  --data-urlencode 'subject=Testing helpdesk ticket' \
  --data-urlencode 'issue=EZ Clap'
```

>The above command returns JSON structured like this:

```json
{
  "message": "Support ticket #37935274 created.",
  "status": 200
}
```


This endpoint creates a new ticket.

### HTTP Request

`POST https://api.linsta.nl/v1/helpdesk/create-ticket`

### Body Parameters

| Parameter | Default   | Description           |
| --------- | --------- | --------------------- |
| type      | undefined | String of type        |
| tags      | undefined | String array of tags  |
| subject   | undefined | String of the subject |
| issue     | undefined | String of the issue   |

## Edit ticket

```shell
curl --location --request PUT "https://api.linsta.nl/v1/helpdesk/edit-ticket" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'ticketId=Critical issue' \
  --data-urlencode 'issue=EZ Clap'
```

>The above command returns JSON structured like this:

```json
{
  "message": "Ticket has been updated",
  "status": 200
}
```


This endpoint edit a ticket by its ID.

### HTTP Request

`PUT https://api.linsta.nl/v1/helpdesk/edit-ticket`

### Body Parameters

| Parameter | Default   | Description         |
| --------- | --------- | ------------------- |
| ticketId  | undefined | String of ID        |
| issue     | undefined | String of the issue |

## Delete ticket

```shell
curl --location --request POST "https://api.linsta.nl/v1/helpdesk/delete-ticket" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'ticketId=Critical issue' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Ticket has been deleted",
  "status": 200
}
```


This endpoint mark ticket as delete.

### HTTP Request

`POST https://api.linsta.nl/v1/helpdesk/delete-ticket`

### Body Parameters

| Parameter | Default   | Description  |
| --------- | --------- | ------------ |
| ticketId  | undefined | String of ID |


## List tickets (user)

```shell
curl --location --request GET "https://api.linsta.nl/v1/helpdesk/user/view-tickets" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "_count": 1,
    "tickets": [
        {
            "deleted": false,
            "status": 1,
            "comments": [],
            "notes": [],
            "attachments": [],
            "history": [
                "5e1e54e3a666f656c540e997"
            ],
            "_id": "5e1e50af0452dd30df4fcd59",
            "owner": "5dd569fd84501322bb9bcb07",
            "type": "Critical issue",
            "subject": "Testing helpdesk ticket",
            "issue": "EZ Clap",
            "createdAt": "2020-01-14T23:37:19.815Z",
            "updatedAt": "2020-01-14T23:55:15.667Z",
            "ticketId": 37935274,
            "__v": 1,
            "assignee": "5dc58ab69f2c053aeb04ed01"
        }
    ],
    "status": 200
}
```


This endpoint retrieve all user tickets.

### HTTP Request

`GET https://api.linsta.nl/v1/helpdesk/user/view-tickets`

## List tickets (admin)

```shell
curl --location --request GET "https://api.linsta.nl/v1/helpdesk/admin/view-tickets" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "_count": 2,
    "tickets": [
        {
            "deleted": false,
            "status": 1,
            "comments": [
                {
                    "deleted": false,
                    "_id": "5df2a66784e0106d29bf8cb5",
                    "owner": "5dd569fd84501322bb9bcb07",
                    "date": "2019-12-12T20:43:19.254Z",
                    "comment": "Hello World",
                    "__v": 0
                }
            ],
            "notes": [],
            "attachments": [],
            "history": [
                {
                    "_id": "5df12af9a3a4262782032ba2",
                    "action": "assigned",
                    "owner": "5dd569fd84501322bb9bcb07",
                    "date": "2019-12-11T17:44:25.163Z",
                    "__v": 0
                }
            ],
            "_id": "5deffaaf4b4947368d238f4d",
            "owner": {
                "role": "consument",
                "_id": "5e0fae88f756286cbe61f36a",
                "userProfile": {
                    "_id": "5e0fc4771c5efe6969f10e44",
                    "firstName": "User",
                    "lastName": "Demo"
                }
            },
            "type": "Critical issue",
            "subject": "Testing helpdesk ticket",
            "issue": "EZ Clap",
            "createdAt": "2019-12-10T20:06:07.468Z",
            "updatedAt": "2019-12-12T20:44:35.872Z",
            "ticketId": 54496259,
            "__v": 77,
            "assignee": {
                "role": "admin",
                "_id": "5dd569fd84501322bb9bcb07",
                "userProfile": {
                    "_id": "5dd56a4f84501322bb9bcb08",
                    "firstName": "Nathan",
                    "lastName": "Henniges"
                }
            }
        },
        {
            "deleted": false,
            "status": 1,
            "comments": [],
            "notes": [],
            "attachments": [],
            "history": [
                {
                    "_id": "5e1e54e3a666f656c540e997",
                    "action": "assigned",
                    "owner": "5dc16583e67a00461058ae2d",
                    "date": "2020-01-14T23:55:15.645Z",
                    "__v": 0
                }
            ],
            "_id": "5e1e50af0452dd30df4fcd59",
            "owner": {
                "role": "admin",
                "_id": "5dd569fd84501322bb9bcb07",
                "userProfile": {
                    "_id": "5dd56a4f84501322bb9bcb08",
                    "firstName": "Nathan",
                    "lastName": "Henniges"
                }
            },
            "type": "Critical issue",
            "subject": "Testing helpdesk ticket",
            "issue": "EZ Clap",
            "createdAt": "2020-01-14T23:37:19.815Z",
            "updatedAt": "2020-01-14T23:55:15.667Z",
            "ticketId": 37935274,
            "__v": 1,
            "assignee": {
                "role": "admin",
                "_id": "5dc58ab69f2c053aeb04ed01",
                "userProfile": {
                    "_id": "5dc43209f522236be10ca85c",
                    "firstName": "Wieger",
                    "lastName": "van Ooijen"
                }
            }
        }
    ],
    "status": 200
}
```

This endpoint retrieve all tickets.

### HTTP Request

`GET https://api.linsta.nl/v1/helpdesk/admin/view-tickets`

### Query Parameters

| Parameter  | Default   | Description                                 |
| ---------- | --------- | ------------------------------------------- |
| date       | undefined | String of date supports (newest and oldest) |
| ticketType | undefined | String of ticketType                        |
| status     | undefined | String of status                            |


## View ticket by id

```shell
curl --location --request GET "https://api.linsta.nl/v1/helpdesk/admin/view-tickets/:ticket_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "ticket": {
        "deleted": false,
        "status": 1,
        "comments": [],
        "notes": [],
        "attachments": [],
        "history": [
            {
                "_id": "5e1e54e3a666f656c540e997",
                "action": "assigned",
                "owner": {
                    "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                    "_id": "5dc16583e67a00461058ae2d",
                    "email": "admin@demo.nl",
                    "userProfile": {
                        "_id": "5dc16727e67a00461058ae2e",
                        "firstName": "Admin",
                        "lastName": "Account"
                    }
                },
                "date": "2020-01-14T23:55:15.645Z",
                "__v": 0
            }
        ],
        "_id": "5e1e50af0452dd30df4fcd59",
        "owner": {
            "_id": "5dd569fd84501322bb9bcb07",
            "userProfile": {
                "_id": "5dd56a4f84501322bb9bcb08",
                "firstName": "Nathan",
                "lastName": "Henniges"
            }
        },
        "type": "Critical issue",
        "subject": "Testing helpdesk ticket",
        "issue": "EZ Clap",
        "createdAt": "2020-01-14T23:37:19.815Z",
        "updatedAt": "2020-01-14T23:55:15.667Z",
        "ticketId": 37935274,
        "__v": 1,
        "assignee": {
            "_id": "5dc58ab69f2c053aeb04ed01",
            "userProfile": {
                "_id": "5dc43209f522236be10ca85c",
                "firstName": "Wieger",
                "lastName": "van Ooijen"
            }
        }
    },
    "status": 200
}
```

This endpoint retrieve ticket by its ID.

### HTTP Request

`GET https://api.linsta.nl/v1/helpdesk/admin/view-tickets/:ticket_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| ticket_id | undefined | MongoDB Object ID of the ticket |

## Assign ticket

```shell
curl --location --request POST "https://api.linsta.nl/v1/helpdesk/admin/assign-ticket/:ticket_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'assignee=5e19e9eba95d3e3721b39da1'
```

>The above command returns JSON structured like this:

```json
{ "messaage": "Ticket has been asigned", "status": 200 }
```

This endpoint assign ticket to someone.

### HTTP Request

`POST https://api.linsta.nl/v1/helpdesk/admin/assign-ticket/:ticket_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| ticket_id | undefined | MongoDB Object ID of the ticket |
| assignee  | undefined | Who assignee of the ticket      |

## ReAssign ticket

```shell
curl --location --request PUT "https://api.linsta.nl/v1/helpdesk/admin/reassign-ticket/:ticket_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'assignee=5e19e9eba95d3e3721b39da1'
```

>The above command returns JSON structured like this:

```json
{ "messaage": "Ticket has been reassign", "status": 200 }
```

This endpoint reassign ticket to someone.

### HTTP Request

`PUT https://api.linsta.nl/v1/helpdesk/admin/reassign-ticket/:ticket_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| ticket_id | undefined | MongoDB Object ID of the ticket |
| assignee  | undefined | Who assignee of the ticket      |

## Archive ticket

```shell
curl --location --request POST "https://api.linsta.nl/v1/helpdesk/admin/archive-ticket/:ticket_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{ "messaage": "Ticket has been reassign", "status": 200 }
```

This endpoint archive ticket.

### HTTP Request

`POST https://api.linsta.nl/v1/helpdesk/admin/archive-ticket/:ticket_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| ticket_id | undefined | MongoDB Object ID of the ticket |

## View Archive tickets

```shell
curl --location --request GET "https://api.linsta.nl/v1/helpdesk/admin/archive-tickets" \
  -H "Authorization: Bearer jsonwebtoken
```

>The above command returns JSON structured like this:

```json
{
    "tickets": [
        {
            "deleted": false,
            "status": 3,
            "comments": [],
            "notes": [],
            "attachments": [],
            "history": [
                {
                    "_id": "5e1e54e3a666f656c540e997",
                    "action": "assigned",
                    "owner": "5dc16583e67a00461058ae2d",
                    "date": "2020-01-14T23:55:15.645Z",
                    "__v": 0
                }
            ],
            "_id": "5e1e50af0452dd30df4fcd59",
            "owner": {
                "_id": "5dd569fd84501322bb9bcb07",
                "userProfile": {
                    "_id": "5dd56a4f84501322bb9bcb08",
                    "firstName": "Nathan",
                    "lastName": "Henniges"
                }
            },
            "type": "Critical issue",
            "subject": "Testing helpdesk ticket",
            "issue": "EZ Clap",
            "createdAt": "2020-01-14T23:37:19.815Z",
            "updatedAt": "2020-01-14T23:55:15.667Z",
            "ticketId": 37935274,
            "__v": 1,
            "assignee": {
                "_id": "5dc58ab69f2c053aeb04ed01",
                "userProfile": {
                    "_id": "5dc43209f522236be10ca85c",
                    "firstName": "Wieger",
                    "lastName": "van Ooijen"
                }
            }
        }
    ],
    "status": 200
}
```

This endpoint archive tickets.

### HTTP Request

`GET https://api.linsta.nl/v1/helpdesk/admin/archive-tickets`

## Admin Comment on ticket

```shell
curl --location --request POST "https://api.linsta.nl/v1/helpdesk/admin/:ticket_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'comment=Hello World' \
```

>The above command returns JSON structured like this:

```json
{ "messaage": "Admin Comment was added", "status": 200 }
```

This endpoint adds a admin comment to ticket.

### HTTP Request

`POST https://api.linsta.nl/v1/helpdesk/admin/:ticket_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| ticket_id | undefined | MongoDB Object ID of the ticket |
| comment   | undefined | String of comment               |

## User Comment on ticket

```shell
curl --location --request POST "https://api.linsta.nl/v1/helpdesk/user/:ticket_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'comment=Hello World' \
```

>The above command returns JSON structured like this:

```json
{ "messaage": "Comment was added", "status": 200 }
```

This endpoint adds a comment to ticket.

### HTTP Request

`POST https://api.linsta.nl/v1/helpdesk/user/:ticket_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| ticket_id | undefined | MongoDB Object ID of the ticket |
| comment   | undefined | String of comment               |

# Order

## Get Status

```shell
curl --location --request POST "https://api.linsta.nl/v1/order/status?orderId=" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{
    "order": {
        "status": "paid",
        "_id": "5e30689405bdd556a23c8d6e",
        "orderedBy": "5e05427728248507d762ec88",
        "orderNumber": "2947186430",
        "paymentMethod": "iDeal",
        "price": 640.09,
        "billingCycle": "yearly",
        "plan": "Enterprise",
        "paymentId": "tr_WGWbBt8sbD",
        "createdAt": "2020-01-28T17:00:07.705Z",
        "updatedAt": "2020-01-28T17:00:32.498Z",
        "__v": 0,
        "orderInvoice": "https://res.cloudinary.com/scope-web-llc/raw/upload/v1580230832/linsta/test/Linsta-factuur-2947186430.pdf"
    },
    "status": 200
}
```


This endpoint creates a new ticket.

### HTTP Request

`POST https://api.linsta.nl/v1/order/status`

### Body Parameters

| Parameter | Default   | Description            |
| --------- | --------- | ---------------------- |
| orderId   | undefined | String of the order id |

# Vacancy

## Apply for job

```shell
curl --location --request POST "https://api.linsta.nl/v1/vacancy/apply/:vacancy_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  --form 'name=Nathan Henniges' \
  --form 'email=nathan@scopeweb.nl' \
  --form 'photo=base64s' \
  --form 'motivation=Hello World' \
  --form 'phoneNumber=Hello World' \
  --form 'file=@/C:/Users/scopeweb B.V/Downloads/resumeFile.pdf'
```

>The above command returns JSON structured like this:

```json
{ "messaage": "Uw sollicitatie is in goede orde ontvangen", "status": 200 }
```

This endpoint apply for job

### HTTP Request

`POST https://api.linsta.nl/v1/vacancy/apply/:vacancy_id`

### Body Parameters

| Parameter   | Default   | Description                      |
| ----------- | --------- | -------------------------------- |
| vacancy_id  | undefined | MongoDB Object ID of the vacancy |
| name        | undefined | String of name                   |
| email       | undefined | String of email                  |
| photo       | undefined | Base64 of file photo             |
| motivation  | undefined | String of motivation             |
| phoneNumber | undefined | String of phoneNumber            |

# Business

## Get business

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/:companyId" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "business": {
        "location": {
            "type": "Point",
            "coordinates": [
                51.8961104,
                4.1722762
            ]
        },
        "industries": [],
        "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
        "pageVisible": false,
        "accountLevel": "basic",
        "reviews": [],
        "activeSubscription": false,
        "_id": "5e19ebb45afd28391470b121",
        "KvkNumber": "12345678",
        "companyName": "Aannemersbedrijf De Jong B.V.",
        "companyAddress": "Vakman 1",
        "companyZipCode": "3232HE",
        "region": "ZH",
        "firstName": "Jan",
        "lastName": "De Vakman",
        "phone": "0612345678",
        "pageSlug": "aannemersbedrijf-de-jong-bv",
        "createdAt": "2020-01-11T15:37:24.126Z",
        "updatedAt": "2020-01-11T15:37:24.126Z",
        "__v": 0,
        "projectPictures": []
    },
    "jobs": [],
    "status": 200
}
```

This endpoint get business infomation by its id.

### HTTP Request

`GET https://api.linsta.nl/v1/business/:companyId`

### Body Parameters

| Parameter | Default   | Description                      |
| --------- | --------- | -------------------------------- |
| companyId | undefined | MongoDB Object ID of the company |

## Get business for pages

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/page/:pageSlug" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "business": {
        "location": {
            "type": "Point",
            "coordinates": [
                51.8961104,
                4.1722762
            ]
        },
        "industries": [],
        "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
        "pageVisible": false,
        "accountLevel": "basic",
        "reviews": [],
        "activeSubscription": false,
        "_id": "5e19ebb45afd28391470b121",
        "KvkNumber": "12345678",
        "companyName": "Aannemersbedrijf De Jong B.V.",
        "companyAddress": "Vakman 1",
        "companyZipCode": "3232HE",
        "region": "ZH",
        "firstName": "Jan",
        "lastName": "De Vakman",
        "phone": "0612345678",
        "pageSlug": "aannemersbedrijf-de-jong-bv",
        "createdAt": "2020-01-11T15:37:24.126Z",
        "updatedAt": "2020-01-11T15:37:24.126Z",
        "__v": 0,
        "projectPictures": []
    },
    "jobs": [],
    "status": 200
}
```

This endpoint get business infomation by its id.

### HTTP Request

`GET https://api.linsta.nl/v1/business/page/:pageSlug`

### Body Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| pageSlug  | undefined | String of pageSlug |

## Get business industries

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/profile/industries" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "business": {
        "industries": [
            "Aannemer"
        ],
        "_id": "5e3db32c6389b859f05b598b"
    },
    "status": 200
}
```

This endpoint retrieve industries active for a business.

### HTTP Request

`GET https://api.linsta.nl/v1/business/profile/industries`

### Body Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| pageSlug  | undefined | String of pageSlug |

## Update business

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/update" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'KvkNumber=12345678' \
  --data-urlencode 'companyName=Aannemersbedrijf De Jong B.V.' \
  --data-urlencode 'companyAddress=Vakman 1' \
  --data-urlencode 'companyZipCode=3232HE' \
  --data-urlencode 'firstName=Jan' \
  --data-urlencode 'lastName=De Vakman' \
  --data-urlencode 'phone=0612345678' \
  --data-urlencode 'phone=Vakman 1' \
  --data-urlencode 'companyDescription=Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.' \
  --data-urlencode 'companySlogan=Voor elke klus, vakman BV dus' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw Linsta profiel is gewijzigd en opgeslagen",
  "status": 200
}
```

This endpoint update business by id of the user.

### HTTP Request

`POST https://api.linsta.nl/v1/business/update`

### Body Parameters

| Parameter          | Default   | Description                  |
| ------------------ | --------- | ---------------------------- |
| KvkNumber          | undefined | String of KvkNumber          |
| companyName        | undefined | String of companyName        |
| companyAddress     | undefined | String of companyAddress     |
| companyZipCode     | undefined | String of companyZipCode     |
| firstName          | undefined | String of firstName          |
| lastName           | undefined | String of lastName           |
| phone              | undefined | String of phone              |
| companyDescription | undefined | String of companyDescription |
| companySlogan      | undefined | String of companySlogan      |

## Update business industries

```shell
curl --location --request PUT "https://api.linsta.nl/v1/business/update-industries" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'industries=test,test2,test3' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw Linsta profiel is gewijzigd en opgeslagen",
  "status": 200
}
```

This endpoint update business industries by id of the user.

### HTTP Request

`PUT https://api.linsta.nl/v1/business/update-industries`

### Body Parameters

| Parameter  | Default   | Description                 |
| ---------- | --------- | --------------------------- |
| industries | undefined | String of industries with , |

## Update business project picture

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/upload-project-picture" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'projectPicture=base64 image' 
```

>The above command returns JSON structured like this:

```json
{
  "image": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/linsta/vakmannen/portfolio/project-afbeelding-487844543.png",
  "fileName": "project-afbeelding-487844543",
  "message": "Uw project foto is aan uw persoonlijke pagina toegevoegd",
  "status": 200
}
```

This endpoint update business project picture

### HTTP Request

`POST https://api.linsta.nl/v1/business/upload-project-picture`

### Body Parameters

| Parameter      | Default   | Description            |
| -------------- | --------- | ---------------------- |
| projectPicture | undefined | String of base64 image |

## Update business project picture

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/delete-project-picture/:imageId" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw projectfoto is verwijderd op uw persoonlijke pagina",
  "status": 200
}
```

This endpoint delete business project picture.

### HTTP Request

`POST https://api.linsta.nl/v1/business/delete-project-picture/:imageId`

### Body Parameters

| Parameter | Default   | Description            |
| --------- | --------- | ---------------------- |
| imageId   | undefined | String of the image id |

## Update business logo

```shell
curl --location --request PUT "https://api.linsta.nl/v1/business/update-logo" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'companyLogo=base64 image' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw Linsta profiel logo is gewijzigd en opgeslagen",
  "status": 200
}
```

This endpoint update business logo.

### HTTP Request

`PUT https://api.linsta.nl/v1/business/update-logo`

### Body Parameters

| Parameter   | Default   | Description                  |
| ----------- | --------- | ---------------------------- |
| companyLogo | undefined | String of base 64 logo image |

## Update business email

```shell
curl --location --request PUT "https://api.linsta.nl/v1/business/update-email" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=nathan.henniges@scopeweb.nl' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw e-mailadres is gewijzigd en opgeslagen",
  "status": 200
}
```

This endpoint update business email.

### HTTP Request

`PUT https://api.linsta.nl/v1/business/update-email`

### Body Parameters

| Parameter | Default   | Description         |
| --------- | --------- | ------------------- |
| email     | undefined | String of new email |

## Update business visibility

```shell
curl --location --request PUT "https://api.linsta.nl/v1/business/page-settings" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'pageVisible=false' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Page visibility has been updated",
  "status": 200
}
```

This endpoint update business visibility.

### HTTP Request

`PUT https://api.linsta.nl/v1/business/page-settings`

### Body Parameters

| Parameter   | Default   | Description             |
| ----------- | --------- | ----------------------- |
| pageVisible | undefined | String of true or false |

## Post a job

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/list-a-job" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'functionTitle=Test' \
  --data-urlencode 'functionProfile=Aannemer' \
  --data-urlencode 'jobDescription=Adding this vacature to test the update functionality.' \
  --data-urlencode 'phoneNumber=0123456789' \
  --data-urlencode 'hours=40' \
  --data-urlencode 'location=3071BG' \
  --data-urlencode 'salaryIndication=2485 - 2970' \
  --data-urlencode 'startDate=2020-01-13T22:57:00.000Z' \
  --data-urlencode 'endDate=ISODate("2020-01-27T22:44:00.000Z")' \
  --data-urlencode 'contactEmail=example@example.nl' \
  --data-urlencode 'contactTel=0123456789' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Job has been posted",
  "status": 200
}
```

This endpoint alllows the business owner to list a job.

### HTTP Request

`POST https://api.linsta.nl/v1/business/list-a-job`

### Body Parameters

| Parameter            | Default   | Description                    |
| -------------------- | --------- | ------------------------------ |
| functionTitle        | undefined | String of functionTitle        |
| functionProfile      | undefined | String of functionProfile      |
| jobDescription       | undefined | String of jobDescription       |
| phoneNumber          | undefined | String of phoneNumber          |
| hours                | undefined | String of hours                |
| location             | undefined | String of location             |
| salaryIndication     | undefined | String of salaryIndication     |
| salaryPer            | undefined | String of salaryPer            |
| industryName         | undefined | String of industryName         |
| distanceFromLocation | undefined | String of distanceFromLocation |
| totalFTE             | undefined | String of totalFTE             |
| experienceLevel      | undefined | String of experienceLevel      |
| startDateSelect      | undefined | String of startDateSelect      |
| startDate            | undefined | String of startDate            |
| endDate              | undefined | String of endDate              |
| jobDuration          | undefined | String of jobDuration          |
| sameContact          | undefined | String of sameContact          |
| contactEmail         | undefined | String of contactEmail         |
| contactTel           | undefined | String of contactTel           |

## Update Job

```shell
curl --location --request PUT "https://api.linsta.nl/v1/business/edit-job/:job_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'functionTitle=Test' \
  --data-urlencode 'functionProfile=Aannemer' \
  --data-urlencode 'jobDescription=Adding this vacature to test the update functionality.' \
  --data-urlencode 'phoneNumber=0123456789' \
  --data-urlencode 'hours=40' \
  --data-urlencode 'location=3071BG' \
  --data-urlencode 'salaryIndication=2485 - 2970' \
  --data-urlencode 'startDate=2020-01-13T22:57:00.000Z' \
  --data-urlencode 'endDate=ISODate("2020-01-27T22:44:00.000Z")' \
  --data-urlencode 'contactEmail=example@example.nl' \
  --data-urlencode 'contactTel=0123456789' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Job has been posted",
  "status": 200
}
```

This endpoint alllows the business owner to edit list a job.

### HTTP Request

`PUT https://api.linsta.nl/v1/business/edit-job/:job_id`

### Body Parameters

| Parameter            | Default   | Description                     |
| -------------------- | --------- | ------------------------------- |
| job_id               | undefined | String MongoDB Object ID of job |
| functionTitle        | undefined | String of functionTitle         |
| functionProfile      | undefined | String of functionProfile       |
| jobDescription       | undefined | String of jobDescription        |
| phoneNumber          | undefined | String of phoneNumber           |
| hours                | undefined | String of hours                 |
| location             | undefined | String of location              |
| salaryIndication     | undefined | String of salaryIndication      |
| salaryPer            | undefined | String of salaryPer             |
| industryName         | undefined | String of industryName          |
| distanceFromLocation | undefined | String of distanceFromLocation  |
| totalFTE             | undefined | String of totalFTE              |
| experienceLevel      | undefined | String of experienceLevel       |
| startDateSelect      | undefined | String of startDateSelect       |
| startDate            | undefined | String of startDate             |
| endDate              | undefined | String of endDate               |
| jobDuration          | undefined | String of jobDuration           |
| sameContact          | undefined | String of sameContact           |
| contactEmail         | undefined | String of contactEmail          |
| contactTel           | undefined | String of contactTel            |

## Delete Job

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/business/delete-job/:job_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Deleted job",
  "status": 200
}
```

This endpoint alllows the business owner to delete a job

### HTTP Request

`DELETE https://api.linsta.nl/v1/business/delete-job/:job_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| job_id    | undefined | String MongoDB Object ID of job |

## View Job

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view-job/:job_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "job": {
        "contactDetails": {
            "email": ""
        },
        "comments": [],
        "_id": "5e165e7d6bed775a52c5d039",
        "functionTitle": "Test",
        "functionProfile": "Aannemer",
        "jobDescription": "Adding this vacature to test the update functionality.",
        "salaryIndication": "2485 - 2970",
        "totalFTE": "Specifieke periode",
        "experienceLevel": "MBO",
        "startDate": "2020-01-13T22:57:00.000Z",
        "sameContact": false,
        "businessProfile": "5e09b6027521a16081b1b389",
        "createdAt": "2020-01-08T22:58:05.214Z",
        "updatedAt": "2020-01-18T15:36:44.534Z",
        "__v": 0,
        "location": "3071BG",
        "endDate": "2020-04-30T14:26:00.000Z",
        "salaryPer": "per maand",
        "hours": "40"
    },
    "status": 200
}
```

This endpoint alllows the view of a job.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view-job/:job_id`

### Body Parameters

| Parameter | Default   | Description                     |
| --------- | --------- | ------------------------------- |
| job_id    | undefined | String MongoDB Object ID of job |

## View Gigs

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/gigs" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "gigs": [
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e4579c00d5ede2990081f94",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": null,
            "createdAt": "2020-02-13T16:30:56.201Z",
            "updatedAt": "2020-02-13T16:30:56.201Z",
            "__v": 0
        },
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e457a0f0d5ede2990081f99",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.9078123,
                        4.5079956
                    ]
                },
                "matchedProfessionals": [
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f97"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f98"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f99"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f9a"
                    }
                ],
                "approvedProfessionals": [],
                "invitedProfessionals": [],
                "declinedProfessionals": [],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [],
                "_id": "5e457a0f0d5ede2990081f96",
                "title": "Aanbouw of opbouw plaatsen",
                "zipCode": "3071BG",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.",
                "projectPictures": [
                    {
                        "src": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579385353/linsta/opdrachten/klus-afbeelding/klus-afbeelding-05559785.jpg",
                        "fileName": "klus-afbeelding-05559785"
                    }
                ],
                "industry": "Aannemer",
                "consumer": "5e05427728248507d762ec88",
                "budgetIndication": "€ 10.000 of meer",
                "city": "test",
                "steps": [
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "60",
                        "fieldType": "other",
                        "title": "Hoe groot is de te bouwen uitbreiding in m²? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8ce"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Moet er fundering worden geplaatst?",
                        "ref": "5e237e11e9a7910190daa8cf"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Schuin dak"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wat voor soort dak wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d1"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "6",
                        "fieldType": "other",
                        "title": "Hoeveel ramen wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d2"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "2",
                        "fieldType": "other",
                        "title": "Hoeveel deuren wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d3"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al bouwtekeningen?",
                        "ref": "5e237e11e9a7910190daa8d5"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee - ik moet nog een vergunning regelen"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouw vergunning?",
                        "ref": "5e237e11e9a7910190daa8d6"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Zo snel mogelijk"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wanneer wil je dat de vakman start? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d8"
                    }
                ],
                "createdAt": "2020-02-13T16:32:15.663Z",
                "updatedAt": "2020-02-13T16:32:15.663Z",
                "orderNumber": 1067762937,
                "__v": 0
            },
            "createdAt": "2020-02-13T16:32:15.642Z",
            "updatedAt": "2020-02-13T16:32:15.642Z",
            "__v": 0
        },
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e457a4f0d5ede2990081f9e",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.9078123,
                        4.5079956
                    ]
                },
                "matchedProfessionals": [
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9c"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9d"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9e"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9f"
                    }
                ],
                "approvedProfessionals": [],
                "invitedProfessionals": [],
                "declinedProfessionals": [],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [],
                "_id": "5e457a4f0d5ede2990081f9b",
                "title": "Aanbouw of opbouw plaatsen",
                "zipCode": "3071BG",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.",
                "projectPictures": [],
                "industry": "Aannemer",
                "consumer": "5e09b6027521a16081b1b389",
                "budgetIndication": "€ 10.000 of meer",
                "city": "test",
                "steps": [
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "60",
                        "fieldType": "other",
                        "title": "Hoe groot is de te bouwen uitbreiding in m²? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8ce"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Moet er fundering worden geplaatst?",
                        "ref": "5e237e11e9a7910190daa8cf"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Schuin dak"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wat voor soort dak wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d1"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "6",
                        "fieldType": "other",
                        "title": "Hoeveel ramen wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d2"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "2",
                        "fieldType": "other",
                        "title": "Hoeveel deuren wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d3"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al bouwtekeningen?",
                        "ref": "5e237e11e9a7910190daa8d5"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee - ik moet nog een vergunning regelen"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouw vergunning?",
                        "ref": "5e237e11e9a7910190daa8d6"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Zo snel mogelijk"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wanneer wil je dat de vakman start? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d8"
                    }
                ],
                "createdAt": "2020-02-13T16:33:19.733Z",
                "updatedAt": "2020-02-13T16:35:26.227Z",
                "orderNumber": 8898997185,
                "__v": 0
            },
            "createdAt": "2020-02-13T16:33:19.718Z",
            "updatedAt": "2020-02-13T16:33:19.718Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint allows the business owner to view consumer created gigs.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/gigs`

### Query Parameters

| Parameter | Default   | Description                               |
| --------- | --------- | ----------------------------------------- |
| date      | undefined | String date supported (newest and oldest) |
| industry  | undefined | String industry                           |

## View Won Gigs

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/won-gigs" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "gigs": [
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e4579c00d5ede2990081f94",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": null,
            "createdAt": "2020-02-13T16:30:56.201Z",
            "updatedAt": "2020-02-13T16:30:56.201Z",
            "__v": 0
        },
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e457a0f0d5ede2990081f99",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.9078123,
                        4.5079956
                    ]
                },
                "matchedProfessionals": [
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f97"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f98"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f99"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f9a"
                    }
                ],
                "approvedProfessionals": [],
                "invitedProfessionals": [],
                "declinedProfessionals": [],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [],
                "_id": "5e457a0f0d5ede2990081f96",
                "title": "Aanbouw of opbouw plaatsen",
                "zipCode": "3071BG",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.",
                "projectPictures": [
                    {
                        "src": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579385353/linsta/opdrachten/klus-afbeelding/klus-afbeelding-05559785.jpg",
                        "fileName": "klus-afbeelding-05559785"
                    }
                ],
                "industry": "Aannemer",
                "consumer": "5e05427728248507d762ec88",
                "budgetIndication": "€ 10.000 of meer",
                "city": "test",
                "steps": [
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "60",
                        "fieldType": "other",
                        "title": "Hoe groot is de te bouwen uitbreiding in m²? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8ce"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Moet er fundering worden geplaatst?",
                        "ref": "5e237e11e9a7910190daa8cf"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Schuin dak"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wat voor soort dak wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d1"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "6",
                        "fieldType": "other",
                        "title": "Hoeveel ramen wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d2"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "2",
                        "fieldType": "other",
                        "title": "Hoeveel deuren wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d3"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al bouwtekeningen?",
                        "ref": "5e237e11e9a7910190daa8d5"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee - ik moet nog een vergunning regelen"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouw vergunning?",
                        "ref": "5e237e11e9a7910190daa8d6"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Zo snel mogelijk"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wanneer wil je dat de vakman start? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d8"
                    }
                ],
                "createdAt": "2020-02-13T16:32:15.663Z",
                "updatedAt": "2020-02-13T16:32:15.663Z",
                "orderNumber": 1067762937,
                "__v": 0
            },
            "createdAt": "2020-02-13T16:32:15.642Z",
            "updatedAt": "2020-02-13T16:32:15.642Z",
            "__v": 0
        },
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e457a4f0d5ede2990081f9e",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.9078123,
                        4.5079956
                    ]
                },
                "matchedProfessionals": [
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9c"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9d"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9e"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9f"
                    }
                ],
                "approvedProfessionals": [],
                "invitedProfessionals": [],
                "declinedProfessionals": [],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [],
                "_id": "5e457a4f0d5ede2990081f9b",
                "title": "Aanbouw of opbouw plaatsen",
                "zipCode": "3071BG",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.",
                "projectPictures": [],
                "industry": "Aannemer",
                "consumer": "5e09b6027521a16081b1b389",
                "budgetIndication": "€ 10.000 of meer",
                "city": "test",
                "steps": [
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "60",
                        "fieldType": "other",
                        "title": "Hoe groot is de te bouwen uitbreiding in m²? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8ce"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Moet er fundering worden geplaatst?",
                        "ref": "5e237e11e9a7910190daa8cf"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Schuin dak"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wat voor soort dak wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d1"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "6",
                        "fieldType": "other",
                        "title": "Hoeveel ramen wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d2"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "2",
                        "fieldType": "other",
                        "title": "Hoeveel deuren wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d3"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al bouwtekeningen?",
                        "ref": "5e237e11e9a7910190daa8d5"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee - ik moet nog een vergunning regelen"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouw vergunning?",
                        "ref": "5e237e11e9a7910190daa8d6"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Zo snel mogelijk"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wanneer wil je dat de vakman start? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d8"
                    }
                ],
                "createdAt": "2020-02-13T16:33:19.733Z",
                "updatedAt": "2020-02-13T16:35:26.227Z",
                "orderNumber": 8898997185,
                "__v": 0
            },
            "createdAt": "2020-02-13T16:33:19.718Z",
            "updatedAt": "2020-02-13T16:33:19.718Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint allows the business owner to won gigs.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/won-gigs`

## View Invited Gigs

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/invited-gigs" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "gigs": [
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e4579c00d5ede2990081f94",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": null,
            "createdAt": "2020-02-13T16:30:56.201Z",
            "updatedAt": "2020-02-13T16:30:56.201Z",
            "__v": 0
        },
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e457a0f0d5ede2990081f99",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.9078123,
                        4.5079956
                    ]
                },
                "matchedProfessionals": [
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f97"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f98"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f99"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a0f0d5ede2990081f9a"
                    }
                ],
                "approvedProfessionals": [],
                "invitedProfessionals": [],
                "declinedProfessionals": [],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [],
                "_id": "5e457a0f0d5ede2990081f96",
                "title": "Aanbouw of opbouw plaatsen",
                "zipCode": "3071BG",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.",
                "projectPictures": [
                    {
                        "src": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579385353/linsta/opdrachten/klus-afbeelding/klus-afbeelding-05559785.jpg",
                        "fileName": "klus-afbeelding-05559785"
                    }
                ],
                "industry": "Aannemer",
                "consumer": "5e05427728248507d762ec88",
                "budgetIndication": "€ 10.000 of meer",
                "city": "test",
                "steps": [
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "60",
                        "fieldType": "other",
                        "title": "Hoe groot is de te bouwen uitbreiding in m²? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8ce"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Moet er fundering worden geplaatst?",
                        "ref": "5e237e11e9a7910190daa8cf"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Schuin dak"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wat voor soort dak wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d1"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "6",
                        "fieldType": "other",
                        "title": "Hoeveel ramen wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d2"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "2",
                        "fieldType": "other",
                        "title": "Hoeveel deuren wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d3"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al bouwtekeningen?",
                        "ref": "5e237e11e9a7910190daa8d5"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee - ik moet nog een vergunning regelen"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouw vergunning?",
                        "ref": "5e237e11e9a7910190daa8d6"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Zo snel mogelijk"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wanneer wil je dat de vakman start? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d8"
                    }
                ],
                "createdAt": "2020-02-13T16:32:15.663Z",
                "updatedAt": "2020-02-13T16:32:15.663Z",
                "orderNumber": 1067762937,
                "__v": 0
            },
            "createdAt": "2020-02-13T16:32:15.642Z",
            "updatedAt": "2020-02-13T16:32:15.642Z",
            "__v": 0
        },
        {
            "gigStatus": 0,
            "hasReplied": false,
            "_id": "5e457a4f0d5ede2990081f9e",
            "professional": "5e09b6027521a16081b1b389",
            "industry": "Aannemer",
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.9078123,
                        4.5079956
                    ]
                },
                "matchedProfessionals": [
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9c"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9d"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9e"
                    },
                    {
                        "gigStatus": 0,
                        "_id": "5e457a4f0d5ede2990081f9f"
                    }
                ],
                "approvedProfessionals": [],
                "invitedProfessionals": [],
                "declinedProfessionals": [],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [],
                "_id": "5e457a4f0d5ede2990081f9b",
                "title": "Aanbouw of opbouw plaatsen",
                "zipCode": "3071BG",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.",
                "projectPictures": [],
                "industry": "Aannemer",
                "consumer": "5e09b6027521a16081b1b389",
                "budgetIndication": "€ 10.000 of meer",
                "city": "test",
                "steps": [
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "60",
                        "fieldType": "other",
                        "title": "Hoe groot is de te bouwen uitbreiding in m²? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8ce"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Moet er fundering worden geplaatst?",
                        "ref": "5e237e11e9a7910190daa8cf"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Schuin dak"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wat voor soort dak wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d1"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "6",
                        "fieldType": "other",
                        "title": "Hoeveel ramen wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d2"
                    },
                    {
                        "select": [],
                        "radio": [],
                        "checkbox": [],
                        "value": "2",
                        "fieldType": "other",
                        "title": "Hoeveel deuren wil je laten plaatsen? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d3"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al bouwtekeningen?",
                        "ref": "5e237e11e9a7910190daa8d5"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Nee - ik moet nog een vergunning regelen"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouw vergunning?",
                        "ref": "5e237e11e9a7910190daa8d6"
                    },
                    {
                        "select": [],
                        "radio": [
                            "Zo snel mogelijk"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Wanneer wil je dat de vakman start? (Optioneel)",
                        "ref": "5e237e11e9a7910190daa8d8"
                    }
                ],
                "createdAt": "2020-02-13T16:33:19.733Z",
                "updatedAt": "2020-02-13T16:35:26.227Z",
                "orderNumber": 8898997185,
                "__v": 0
            },
            "createdAt": "2020-02-13T16:33:19.718Z",
            "updatedAt": "2020-02-13T16:33:19.718Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint allows the business owner to invited gigs.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/invited-gigs`

## Find Gigs

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/find/gigs" \
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
                "5e4303ec8cf85ee10b5e038b",
                "5e4303ec8cf85ee10b5e038c"
            ],
            "approvedProfessionals": [
                "5e4303ec8cf85ee10b5e038c"
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
            "updatedAt": "2020-02-13T22:20:53.850Z",
            "orderNumber": 8403869585,
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint allows the business owner to find gigs.

### HTTP Request

`GET https://api.linsta.nl/v1/business/find/gigs`

### Query Parameters

| Parameter    | Default   | Description                |
| ------------ | --------- | -------------------------- |
| distanceFrom | undefined | String of the distanceFrom |
| industry     | undefined | String of the industry     |
| price        | undefined | String of the price        |

## View gig by id

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/gigs/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "gig": {
        "location": {
            "type": "Point",
            "coordinates": [
                52.17905700000001,
                5.27834
            ]
        },
        "matchedProfessionals": [
            "5e4303ec8cf85ee10b5e038b",
            "5e4303ec8cf85ee10b5e038c"
        ],
        "approvedProfessionals": [
            "5e4303ec8cf85ee10b5e038c"
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
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d6d",
                    "fieldType": "input",
                    "name": "watisdegroottevandeaanofuitbouwinm",
                    "label": "Wat is de grootte van de aan- of uitbouw in m2? ",
                    "isRequired": true,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [],
                    "selectValues": [],
                    "__v": 0
                }
            },
            {
                "select": [],
                "radio": [
                    "Nee"
                ],
                "checkbox": [],
                "fieldType": "radio",
                "title": "Is een fundering noodzakelijk?",
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d6e",
                    "fieldType": "radio",
                    "name": "iseenfunderingnoodzakelijk",
                    "label": "Is een fundering noodzakelijk?",
                    "isRequired": false,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [
                        {
                            "name": "iseenfunderingnoodzakelijk",
                            "value": "Ja",
                            "id": "30491027211905470948"
                        },
                        {
                            "name": "iseenfunderingnoodzakelijk",
                            "value": "Nee",
                            "id": "03671265479576968429"
                        },
                        {
                            "name": "iseenfunderingnoodzakelijk",
                            "value": "In overleg vakman",
                            "id": "74870954378394908337"
                        },
                        {
                            "name": "iseenfunderingnoodzakelijk",
                            "value": "Weet ik niet",
                            "id": "45246736172292713415"
                        }
                    ],
                    "selectValues": [],
                    "__v": 0
                }
            },
            {
                "select": [],
                "radio": [
                    "Plat dak"
                ],
                "checkbox": [],
                "fieldType": "radio",
                "title": "Welk soort dak wil je laten plaatsen?",
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d70",
                    "fieldType": "radio",
                    "name": "welksoortdakwiljelatenplaatsen",
                    "label": "Welk soort dak wil je laten plaatsen?",
                    "isRequired": false,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [
                        {
                            "name": "welksoortdakwiljelatenplaatsen",
                            "value": "Schuin dak",
                            "id": "82658946998736614560"
                        },
                        {
                            "name": "welksoortdakwiljelatenplaatsen",
                            "value": "Plat dak",
                            "id": "52221917480798271319"
                        },
                        {
                            "name": "welksoortdakwiljelatenplaatsen",
                            "value": "Anders",
                            "id": "24034961406217677357"
                        }
                    ],
                    "selectValues": [],
                    "__v": 0
                }
            },
            {
                "select": [],
                "radio": [],
                "checkbox": [],
                "value": "6",
                "fieldType": "other",
                "title": "Hoeveel ramen wil je laten plaatsen?",
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d71",
                    "fieldType": "input",
                    "name": "hoeveelramenwiljelatenplaatsen",
                    "label": "Hoeveel ramen wil je laten plaatsen?",
                    "isRequired": false,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [],
                    "selectValues": [],
                    "__v": 0
                }
            },
            {
                "select": [],
                "radio": [],
                "checkbox": [],
                "value": "2",
                "fieldType": "other",
                "title": "Hoeveel deuren wil je laten plaatsen?",
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d72",
                    "fieldType": "input",
                    "name": "hoeveeldeurenwiljelatenplaatsen",
                    "label": "Hoeveel deuren wil je laten plaatsen?",
                    "isRequired": false,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [],
                    "selectValues": [],
                    "__v": 0
                }
            },
            {
                "select": [],
                "radio": [
                    "Nee"
                ],
                "checkbox": [],
                "fieldType": "radio",
                "title": "Heb je al bouwtekeningen?",
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d74",
                    "fieldType": "radio",
                    "name": "hebjealbouwtekeningen",
                    "label": "Heb je al bouwtekeningen?",
                    "isRequired": false,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [
                        {
                            "name": "hebjealbouwtekeningen",
                            "value": "Ja",
                            "id": "77448307934056880630"
                        },
                        {
                            "name": "hebjealbouwtekeningen",
                            "value": "Nee",
                            "id": "23428122330856405183"
                        },
                        {
                            "name": "hebjealbouwtekeningen",
                            "value": "In overleg vakman",
                            "id": "72331874448296331743"
                        },
                        {
                            "name": "hebjealbouwtekeningen",
                            "value": "Weet ik niet",
                            "id": "15780643322061840913"
                        }
                    ],
                    "selectValues": [],
                    "__v": 0
                }
            },
            {
                "select": [],
                "radio": [
                    "Nee - niet nodig"
                ],
                "checkbox": [],
                "fieldType": "radio",
                "title": "Heb je al een bouwvergunning?",
                "ref": {
                    "required": true,
                    "readOnly": false,
                    "disabled": false,
                    "isActive": true,
                    "_id": "5e2efe83123cb54da3be0d75",
                    "fieldType": "radio",
                    "name": "hebjealeenbouwvergunning",
                    "label": "Heb je al een bouwvergunning?",
                    "isRequired": true,
                    "placeholder": "",
                    "checkBoxValues": [],
                    "radioValues": [
                        {
                            "name": "hebjealeenbouwvergunning",
                            "value": "Ja",
                            "id": "11938436525583490028"
                        },
                        {
                            "name": "hebjealeenbouwvergunning",
                            "value": "Nee - niet nodig",
                            "id": "09286062135844455983"
                        },
                        {
                            "name": "hebjealeenbouwvergunning",
                            "value": "Nee - moet ik nog regelen",
                            "id": "97431806377950424387"
                        },
                        {
                            "name": "hebjealeenbouwvergunning",
                            "value": "Weet ik niet",
                            "id": "24355291395104735226"
                        }
                    ],
                    "selectValues": [],
                    "__v": 0
                }
            }
        ],
        "createdAt": "2020-02-11T19:43:40.269Z",
        "updatedAt": "2020-02-13T22:20:53.850Z",
        "orderNumber": 8403869585,
        "__v": 0
    },
    "status": 200
}
```

This endpoint allows the business owner to view gig by its id.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/gigs/:gig_id`

## Send Pitch

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/reply/gigs/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'price=1500' \
  --data-urlencode 'pitch=Give me your money' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw reactie is naar de consument verstuurd.",
  "status": 200
}
```

This endpoint allows the business to send a pitch to a gig.

### HTTP Request

`POST https://api.linsta.nl/v1/business/reply/gigs/:gig_id`

### Query Parameters

| Parameter | Default   | Description         |
| --------- | --------- | ------------------- |
| price     | undefined | String of the price |
| pitch     | undefined | String of the pitch |

## Decline Gig

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/decline/gig/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "You have declined the gig.",
  "status": 200
}
```

This endpoint allows the business to decline a gig.

### HTTP Request

`POST https://api.linsta.nl/v1/business/decline/gig/:gig_id`

### Body Parameters

| Parameter | Default   | Description                         |
| --------- | --------- | ----------------------------------- |
| gig_id    | undefined | String MongoDB Object ID of the gig |

## View pitches

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/pitches" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "pitches": [
        {
            "_id": "5e42d8e3b79ec91f3ac63679",
            "owner": {
                "_id": "5e05427728248507d762ec88",
                "businessProfile": {
                    "companyLogo": "https://res.cloudinary.com/scope-web-llc/image/upload/v1571863687/Klusnet/avatar-placeholder.png",
                    "_id": "5e09b6027521a16081b1b389",
                    "companyName": "Vakman",
                    "firstName": "Test",
                    "lastName": "Vakman"
                }
            },
            "gig": {
                "location": {
                    "type": "Point",
                    "coordinates": [
                        51.8975292,
                        4.1721361
                    ]
                },
                "matchedProfessionals": [],
                "approvedProfessionals": [
                    "5e42d8bcb79ec91f3ac63675"
                ],
                "invitedProfessionals": [],
                "declinedProfessionals": [
                    "5e42d8bcb79ec91f3ac63676",
                    "5e42d8bcb79ec91f3ac63677",
                    "5e42d8bcb79ec91f3ac63678"
                ],
                "underReviewProfessionals": [],
                "hasBeenUpdated": false,
                "pitches": [
                    "5e42d8e3b79ec91f3ac63679"
                ],
                "_id": "5e42d8bbb79ec91f3ac63674",
                "title": "Aan - & uitbouw",
                "zipCode": "3232HB",
                "comment": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin interdum lorem nulla, vitae ultrices nisi elementum id. Nullam at sagittis nisi. Morbi pharetra risus a nunc posuere, vel porttitor dui commodo. Suspendisse malesuada leo ut tristique facilisis. Aenean commodo sit amet ex a tristique. Mauris tempus pharetra urna lobortis sollicitudin. Sed et congue nulla. Donec accumsan interdum aliquam. Nulla vel viverra nisi, nec auctor eros. Ut varius leo ut condimentum bibendum. Aliquam vehicula cursus egestas. Maecenas diam odio, sodales id pharetra sed, fermentum sit amet risus. Integer rutrum aliquet augue et tincidunt. Nulla facilisi. Morbi tincidunt nibh sed posuere blandit. Nullam quis mi eget diam ullamcorper lobortis.",
                "projectPictures": [],
                "industry": "Aannemer",
                "consumer": "5dca7a9a3d5cc53294ff0cff",
                "budgetIndication": "€ 5000 - € 10.000",
                "city": "Brielle",
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
                            "Ja"
                        ],
                        "checkbox": [],
                        "fieldType": "radio",
                        "title": "Heb je al een bouwvergunning?",
                        "ref": "5e2efe83123cb54da3be0d75"
                    }
                ],
                "createdAt": "2020-02-11T16:39:24.131Z",
                "updatedAt": "2020-02-11T19:39:04.786Z",
                "orderNumber": 7536715943,
                "__v": 4
            },
            "price": 5500,
            "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin interdum lorem nulla, vitae ultrices nisi elementum id. Nullam at sagittis nisi. Morbi pharetra risus a nunc posuere, vel porttitor dui commodo. Suspendisse malesuada leo ut tristique facilisis. Aenean commodo sit amet ex a tristique. Mauris tempus pharetra urna lobortis sollicitudin. Sed et congue nulla. Donec accumsan interdum aliquam. Nulla vel viverra nisi, nec auctor eros. Ut varius leo ut condimentum bibendum. Aliquam vehicula cursus egestas. Maecenas diam odio, sodales id pharetra sed, fermentum sit amet risus. Integer rutrum aliquet augue et tincidunt. Nulla facilisi. Morbi tincidunt nibh sed posuere blandit. Nullam quis mi eget diam ullamcorper lobortis.",
            "createdAt": "2020-02-11T16:40:03.722Z",
            "updatedAt": "2020-02-11T16:40:03.722Z",
            "pitchId": 7486826855,
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint allows the business to view pitchs.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/pitches`

### Body Parameters

| Parameter  | Default   | Description                                                      |
| ---------- | --------- | ---------------------------------------------------------------- |
| filterType | undefined | String of filterType supported (newest,oldest, priceHL, priceLH) |

## View jobs

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/jobs" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "jobs": [
        {
            "contactDetails": {
                "email": ""
            },
            "comments": [],
            "_id": "5e165e7d6bed775a52c5d039",
            "functionTitle": "Test",
            "functionProfile": "Aannemer",
            "jobDescription": "Adding this vacature to test the update functionality.",
            "salaryIndication": "2485 - 2970",
            "totalFTE": "Specifieke periode",
            "experienceLevel": "MBO",
            "startDate": "2020-01-13T22:57:00.000Z",
            "sameContact": false,
            "businessProfile": "5e09b6027521a16081b1b389",
            "createdAt": "2020-01-08T22:58:05.214Z",
            "updatedAt": "2020-01-18T15:36:44.534Z",
            "__v": 0,
            "location": "3071BG",
            "endDate": "2020-04-30T14:26:00.000Z",
            "salaryPer": "per maand",
            "hours": "40"
        }
    ],
    "status": 200
}
```

This endpoint allows the business to view jobs.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/jobs`

## View job by id

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/jobs/:job_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "job": {
        "contactDetails": {
            "email": ""
        },
        "comments": [],
        "_id": "5e165e7d6bed775a52c5d039",
        "functionTitle": "Test",
        "functionProfile": "Aannemer",
        "jobDescription": "Adding this vacature to test the update functionality.",
        "salaryIndication": "2485 - 2970",
        "totalFTE": "Specifieke periode",
        "experienceLevel": "MBO",
        "startDate": "2020-01-13T22:57:00.000Z",
        "sameContact": false,
        "businessProfile": "5e09b6027521a16081b1b389",
        "createdAt": "2020-01-08T22:58:05.214Z",
        "updatedAt": "2020-01-18T15:36:44.534Z",
        "__v": 0,
        "location": "3071BG",
        "endDate": "2020-04-30T14:26:00.000Z",
        "salaryPer": "per maand",
        "hours": "40"
    },
    "business": {
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
            {
                "_id": "5e189faf796f851bce1ea314",
                "reviewer": {
                    "_id": "5dca7a9a3d5cc53294ff0cff",
                    "userProfile": {
                        "_id": "5dca7ab63d5cc53294ff0d00",
                        "firstName": "Teunis",
                        "lastName": "van Kerkhof"
                    }
                },
                "company": "5e09b6027521a16081b1b389",
                "rating": 5,
                "industry": "Aannemer",
                "title": "Leverage agile frameworks ",
                "description": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
                "createdAt": "2020-01-10T16:00:47.591Z",
                "updatedAt": "2020-01-10T16:00:47.591Z",
                "__v": 0
            },
            {
                "_id": "5ddc39d93512431f7d33a9da",
                "reviewer": {
                    "_id": "5dca7a9a3d5cc53294ff0cff",
                    "userProfile": {
                        "_id": "5dca7ab63d5cc53294ff0d00",
                        "firstName": "Teunis",
                        "lastName": "van Kerkhof"
                    }
                },
                "company": "5e09b6027521a16081b1b389",
                "rating": 4.9,
                "title": "Draagbalk plaatsen",
                "industry": "Loodgieter",
                "description": "In contact gekomen met Teunis via Klusnet. Hij was veruit de betrouwbaarste. Een dag later stond hij al bij ons binnen. Duidelijke afspraken gemaakt. Een paar dagen voor dat de klus uitgevoerd werd nam hij weer contact met ons op om de afspraken nog eens door te nemen. Wim en zijn team werken als een razende en binnen een halve dag was de klus geklaard. Kortom een vakman die snel werkt en duidelijke afspraken maakt.",
                "createdAt": "2019-11-25T20:30:17.660Z",
                "updatedAt": "2019-11-25T20:30:17.660Z",
                "__v": 0
            },
            {
                "_id": "5ddc2d8309469d93f9c61e28",
                "reviewer": {
                    "_id": "5dd569fd84501322bb9bcb07",
                    "userProfile": {
                        "_id": "5dd56a4f84501322bb9bcb08",
                        "firstName": "Nathan",
                        "lastName": "Henniges"
                    }
                },
                "company": "5e09b6027521a16081b1b389",
                "rating": 4.9,
                "industry": "Glaszetter",
                "title": "Draagbalk plaatsen",
                "description": "In contact gekomen met Dhr. De Jong via Klusnet. Hij was veruit de betrouwbaarste. Een dag later stond hij al bij ons binnen. Duidelijke afspraken gemaakt. Een paar dagen voor dat de klus uitgevoerd werd nam hij weer contact met ons op om de afspraken nog eens door te nemen. Wim en zijn team werken als een razende en binnen een halve dag was de klus geklaard. Kortom een vakman die snel werkt en duidelijke afspraken maakt.",
                "createdAt": "2019-11-25T19:37:39.767Z",
                "updatedAt": "2019-11-25T19:37:39.767Z",
                "__v": 0
            },
            {
                "_id": "5dd3ebcf57077ed184631a64",
                "reviewer": {
                    "_id": "5dca7a9a3d5cc53294ff0cff",
                    "userProfile": {
                        "_id": "5dca7ab63d5cc53294ff0d00",
                        "firstName": "Teunis",
                        "lastName": "van Kerkhof"
                    }
                },
                "company": "5e09b6027521a16081b1b389",
                "rating": 4.4,
                "industry": "Badkamer specialist",
                "title": "Buitenkraan plaatsen in achtertuin",
                "description": "Een vriendelijke, netjes werkenende en snelle vakman. Werkzaamheden al binnen enkele dagen na eerste contact uitgevoerd. Heldere uitleg ná de installatie. Ik beveel deze vakman dan ook van harte aan.",
                "createdAt": "2019-11-19T13:19:11.996Z",
                "updatedAt": "2019-11-19T13:19:11.996Z",
                "__v": 0
            }
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
    "status": 200
}
```

This endpoint allows the business to view job by its ID

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/jobs/:job_id`

### Body Parameters

| Parameter | Default   | Description                         |
| --------- | --------- | ----------------------------------- |
| job_id    | undefined | String MongoDB Object ID of the job |

## View industries

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/view/industries" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "industries": [
        "Aannemer",
        "Badkamer specialist",
        "Behanger",
        "Dakspecialist",
        "Domotica specialist",
        "Elektricien",
        "Gevelspecialist",
        "Glaszetter",
        "Hovenier",
        "Installatiebedrijf",
        "Isolatiebedrijf",
        "Keukenmonteur",
        "Klusbedrijf",
        "Kozijnspecialist",
        "Loodgieter",
        "Metselaar",
        "Ontwerper",
        "Schilder",
        "Schoonmaakbedrijf",
        "Sloopbedrijf",
        "Stoffeerder",
        "Stratenmaker",
        "Stukadoor",
        "Tegelzetter",
        "Timmerman",
        "Verhuisbedrijf",
        "Vloerspecialist",
        "Voertuig monteur",
        "Witgoed reparateur",
        "Radio button invoer"
    ],
    "status": 200
}
```

This endpoint allows the business view industries.

### HTTP Request

`GET https://api.linsta.nl/v1/business/view/industries`

## Complate Gig

```shell
curl --location --request POST "https://api.linsta.nl/v1/business/complete/gig/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw opdracht is voltooid en komt in uw voltooide opdrachten overzoek te staan",
  "status": 200
}
```

This endpoint allows the business to complate a gig.

### HTTP Request

`POST https://api.linsta.nl/v1/business/complete/gig/:gig_id`

### Body Parameters

| Parameter | Default   | Description                         |
| --------- | --------- | ----------------------------------- |
| gig_id    | undefined | String MongoDB Object ID of the gig |

## List orders

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/list/orders" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "orders": [
        {
            "status": "paid",
            "_id": "5e30689405bdd556a23c8d6e",
            "orderedBy": "5e05427728248507d762ec88",
            "orderNumber": "2947186430",
            "paymentMethod": "iDeal",
            "price": 640.09,
            "billingCycle": "yearly",
            "plan": "Enterprise",
            "paymentId": "tr_WGWbBt8sbD",
            "createdAt": "2020-01-28T17:00:07.705Z",
            "updatedAt": "2020-01-28T17:00:32.498Z",
            "__v": 0,
            "orderInvoice": "https://res.cloudinary.com/scope-web-llc/raw/upload/v1580230832/linsta/test/Linsta-factuur-2947186430.pdf"
        }
    ],
    "status": 200
}
```

This endpoint lists orders.

### HTTP Request

`GET https://api.linsta.nl/v1/business/list/orders`

## List bookmarks

```shell
curl --location --request GET "https://api.linsta.nl/v1/business/list/bookmarks" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "bookmarks": [],
    "status": 200
}
```

This endpoint lists bookmarks.

### HTTP Request

`GET https://api.linsta.nl/v1/business/list/bookmarks`

# User

## Current User

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/current" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "user": {
        "profileCompleted": true,
        "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579191185/linsta/vakmannen/portfolio/project-afbeelding-65882723.jpg",
        "role": "admin",
        "notifications": "daily",
        "newsletter": false,
        "twoFactor": false,
        "bookmarkedBusinesses": [
            "5dd57df18d4bd0cdd93a1919",
            "5e19ec5a2156e739680c6e71"
        ],
        "_id": "5dd569fd84501322bb9bcb07",
        "email": "nathan@scopeweb.nl",
        "accountType": "developer",
        "lastLogin": "2020-02-14T00:56:29.201Z",
        "token": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjVkZDU2OWZkODQ1MDEzMjJiYjliY2IwNyIsImF2YXRhciI6Imh0dHBzOi8vcmVzLmNsb3VkaW5hcnkuY29tL3Njb3BlLXdlYi1sbGMvaW1hZ2UvdXBsb2FkL3YxNTc5MTkxMTg1L2xpbnN0YS92YWttYW5uZW4vcG9ydGZvbGlvL3Byb2plY3QtYWZiZWVsZGluZy02NTg4MjcyMy5qcGciLCJyb2xlIjoiYWRtaW4iLCJpYXQiOjE1ODE2NDE3ODksImV4cCI6MTU4MTY4NDk4OX0.OOCHcNIOHJWiT1olxL_GMNRplJ21pMk3NYyQQyq9l88",
        "userProfile": {
            "_id": "5dd56a4f84501322bb9bcb08",
            "firstName": "Nathan",
            "lastName": "Henniges",
            "street": " Wielingen 8",
            "zipCode": "3232HH",
            "city": "Brielle",
            "phone": "12456789",
            "createdAt": "2019-11-20T16:31:11.154Z",
            "updatedAt": "2019-11-20T16:31:11.154Z",
            "__v": 0
        },
        "twoFactorToken": "yXF4m8Q5",
        "twoFactorTokenExpire": "2019-12-06T18:15:43.030Z"
    },
    "status": 200
}
```

This endpoint lets you view the current logged in user.

### HTTP Request

`GET https://api.linsta.nl/v1/user/current`

## View user by ID

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/:user_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "user": {
        "avatar": "https://res.cloudinary.com/scope-web-llc/image/upload/v1579191185/linsta/vakmannen/portfolio/project-afbeelding-65882723.jpg",
        "role": "admin",
        "_id": "5dd569fd84501322bb9bcb07",
        "email": "nathan@scopeweb.nl",
        "lastLogin": "2020-02-14T00:56:29.201Z"
    },
    "status": 200
}
```

This endpoint lets you view via the user id

### HTTP Request

`GET https://api.linsta.nl/v1/user/:user_id`

### Body Parameters

| Parameter | Default   | Description                          |
| --------- | --------- | ------------------------------------ |
| user_id   | undefined | String MongoDB Object ID of the user |

## View reviews by user id

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/:user_id/reviews" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "reviews": [
        {
            "_id": "5ddc2d8309469d93f9c61e28",
            "reviewer": "5dd569fd84501322bb9bcb07",
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
            "industry": "Glaszetter",
            "title": "Draagbalk plaatsen",
            "description": "In contact gekomen met Dhr. De Jong via Klusnet. Hij was veruit de betrouwbaarste. Een dag later stond hij al bij ons binnen. Duidelijke afspraken gemaakt. Een paar dagen voor dat de klus uitgevoerd werd nam hij weer contact met ons op om de afspraken nog eens door te nemen. Wim en zijn team werken als een razende en binnen een halve dag was de klus geklaard. Kortom een vakman die snel werkt en duidelijke afspraken maakt.",
            "createdAt": "2019-11-25T19:37:39.767Z",
            "updatedAt": "2019-11-25T19:37:39.767Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint returns reviews from the user id.

### HTTP Request

`GET https://api.linsta.nl/v1/user/:user_id/reviews`

### Body Parameters

| Parameter | Default   | Description                          |
| --------- | --------- | ------------------------------------ |
| user_id   | undefined | String MongoDB Object ID of the user |

## Update User

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/update" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'firstName=Nathan' \
  --data-urlencode 'lastName=Henniges' \
  --data-urlencode 'phone=1123456789' \
  --data-urlencode 'street=Wielingen 8' \
  --data-urlencode 'zipCode=3232HH' \
  --data-urlencode 'city=Brielle'
```

>The above command returns JSON structured like this:

```json
{
  "message": "Linsta Account profiel wijzigingen zijn opgeslagen",
  "status": 200
}
```

This endpoint update the user.

### HTTP Request

`POST https://api.linsta.nl/v1/user/update`

### Body Parameters

| Parameter | Default   | Description             |
| --------- | --------- | ----------------------- |
| firstName | undefined | String of the firstName |
| lastName  | undefined | String of the lastName  |
| phone     | undefined | String of the phone     |
| street    | undefined | String of the street    |
| zipCode   | undefined | String of the zipCode   |
| city      | undefined | String of the city      |

## Update notification preferences

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/update/notifications" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'notifications=true' \
  --data-urlencode 'newsletter=true' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Linsta Account profiel wijzigingen zijn opgeslagen",
  "status": 200
}
```

This endpoint update users notification preferences

### HTTP Request

`POST https://api.linsta.nl/v1/user/update/notifications`

### Body Parameters

| Parameter     | Default   | Description                 |
| ------------- | --------- | --------------------------- |
| notifications | undefined | String of the notifications |
| newsletter    | undefined | String of the newsletter    |

## Update password

```shell
curl --location --request PUT "https://api.linsta.nl/v1/user/update-password" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'currentPassword=true' \
  --data-urlencode 'password=true' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw Linsta wachtwoord is gewijzigd",
  "status": 200
}
```

This endpoint update users password.

### HTTP Request

`PUT https://api.linsta.nl/v1/user/update-password`

### Body Parameters

| Parameter       | Default   | Description                   |
| --------------- | --------- | ----------------------------- |
| currentPassword | undefined | String of the currentPassword |
| password        | undefined | String of the new password    |

## Delete User

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/user/:user_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw Linsta wachtwoord is gewijzigd",
  "status": 200
}
```

This endpoint update users password.

### HTTP Request

`DELETE https://api.linsta.nl/v1/user/:user_id`

### Body Parameters

| Parameter | Default   | Description                         |
| --------- | --------- | ----------------------------------- |
| user_id   | undefined | String of MongoDB Object ID of user |

## Update Two Factor

```shell
curl --location --request PUT "https://api.linsta.nl/v1/user/update-twofactor" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'status=true' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "Updated two factor options.",
  "status": 200
}
```

This endpoint update two factor status.

### HTTP Request

`PUT https://api.linsta.nl/v1/user/update-twofactor`

### Body Parameters

| Parameter | Default   | Description                        |
| --------- | --------- | ---------------------------------- |
| status    | undefined | String of true or false for status |

## Bookmark a business

```shell
curl --location --request PUT "https://api.linsta.nl/v1/user/bookmarks/:business_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'bookmarked=true' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "De vakman is aan uw favorieten toegevoegd",
  "status": 200
}
```

> Or

```json
{
  "message": "De vakman is uit uw favoriete verwijderd",
  "status": 200
}
```
This endpoint add or remove bookmark business.

### HTTP Request

`PUT https://api.linsta.nl/v1/user/bookmarks/:business_id`

### Body Parameters

| Parameter | Default   | Description                        |
| --------- | --------- | ---------------------------------- |
| status    | undefined | String of true or false for status |

## List bookmarks

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/list/bookmarks" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "bookmarks": [
        {
            "location": {
                "type": "Point",
                "coordinates": [
                    51.8961104,
                    4.1722762
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
            "_id": "5e19ec5a2156e739680c6e71",
            "KvkNumber": "12345678",
            "companyName": "De Vakman",
            "companyAddress": "Vakman 1",
            "companyZipCode": "3232HE",
            "region": "XZH",
            "firstName": "Jan",
            "lastName": "De Vakman",
            "phone": "0612345678",
            "pageSlug": "Family-Roofing-BV",
            "createdAt": "2020-01-11T15:40:10.892Z",
            "updatedAt": "2020-01-14T23:11:12.819Z",
            "__v": 1,
            "companyDescription": "Leverage agile frameworks to provide a robust synopsis for high level overviews. Iterative approaches to corporate strategy foster collaborative thinking to further the overall value proposition. Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.",
            "companySlogan": "Your roofing is not heated more.",
            "avgReviews": 0,
            "projectPictures": [],
            "subscriptionLevel": "Basic"
        }
    ],
    "status": 200
}
```

This endpoint list bookmarked businesses

### HTTP Request

`GET https://api.linsta.nl/v1/user/list/bookmarks`

## Find category

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/find/category" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "category": [
        {
            "keywords": [
                "Vl",
                " vloer",
                " vloerverwarming",
                " ver",
                " verwarming",
                " vloeren",
                " aannemer"
            ],
            "steps": [],
            "images": [],
            "_id": "5e20ac15b7de01eed9c8e7cc",
            "serviceName": "Vloerverwarming plaatsen",
            "industry": "Aannemer",
            "createdAt": "2020-01-16T18:31:49.276Z",
            "updatedAt": "2020-01-16T18:31:49.276Z",
            "__v": 0
        },
        {
            "keywords": [
                "Per",
                " pergola",
                " tuin",
                " tuinhuis",
                " huis",
                " huisje",
                " tuinhuisje",
                " plaatsen",
                " aannemer"
            ],
            "steps": [],
            "images": [],
            "_id": "5e20aaaab7de01eed9c8e7c1",
            "serviceName": "Pergola of Tuinhuis plaatsen",
            "industry": "Aannemer",
            "createdAt": "2020-01-16T18:25:46.869Z",
            "updatedAt": "2020-01-16T18:25:46.869Z",
            "__v": 0
        }
    ],
    "status": 200
}
```

This endpoint finds a businness category

### HTTP Request

`GET https://api.linsta.nl/v1/user/find/category`

### Query Parameters

| Parameter | Default   | Description        |
| --------- | --------- | ------------------ |
| industry  | undefined | String of industry |

## Find service

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/service-name/:service_name" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
    "serviceName": "Dakkapel plaatsen",
    "keywords": [
        "Dak",
        " Dakkapel",
        " Kapel",
        " Da",
        " Dakkapel plaatsen",
        " Renovatie dakkapel"
    ],
    "status": 200
}
```

This endpoint finds a businness service

### HTTP Request

`GET https://api.linsta.nl/v1/user/service-name/:service_name`

### Body Parameters

| Parameter    | Default   | Description            |
| ------------ | --------- | ---------------------- |
| service_name | undefined | String of service_name |

## Update comment on gig

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/place-a-job/update-comment/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'comment=Test' \
  --data-urlencode 'isChanged=true' \
  --data-urlencode 'notify=true' 
```

>The above command returns JSON structured like this:

```json
{
   "message": "De klus omschrijving is gewijzigd en opgeslagen",
   "status": 200
}
```

This endpoint update a comment on a gig.

### HTTP Request

`GET https://api.linsta.nl/v1/user/service-name/:service_name`

### Body Parameters

| Parameter | Default   | Description                           |
| --------- | --------- | ------------------------------------- |
| gig_id    | undefined | String of MongoDB Object ID of gig_id |
| comment   | undefined | String of the comment                 |
| isChanged | undefined | String of the comment                 |
| notify    | undefined | String of the notify                  |

## Verify location

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/verify-location" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'zipCode=1322 AB' 
```

>The above command returns JSON structured like this:

```json
{
    "city": "Almere",
    "coordinates": [
        52.3525621,
        5.1916845
    ],
    "status": 200
}
```

This endpoint verify the users zipcode.

### HTTP Request

`POST https://api.linsta.nl/v1/user/verify-location`

### Body Parameters

| Parameter | Default   | Description           |
| --------- | --------- | --------------------- |
| zipCode   | undefined | String of the zipCode |

## Place a job

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/place-a-job " \
  -H "Authorization: Bearer jsonwebtoken" \
 --header 'Content-Type: application/json' \
  --data-raw '{
    "title": "Test",
    "zipCode": "Test",
    "comment": "Test",
    "email": "Test",
    "budgetIndication": "Test",
    "industry": "zipCode",
    "city": "zipCode",
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
  "message": "Uw klus is geplaatst. U ontvangt een e-mail ter bevestiging",
  "status"  : 200
}
```

This endpoint allows user to place a job.

### HTTP Request

`POST https://api.linsta.nl/v1/user/place-a-job`

### Body Parameters

| Parameter        | Default   | Description                    |
| ---------------- | --------- | ------------------------------ |
| steps            | undefined | Array of steps                 |
| title            | undefined | String of the title            |
| zipCode          | undefined | String of the zipCode          |
| comment          | undefined | String of the email            |
| images           | undefined | Array of  images               |
| industry         | undefined | String of the industry         |
| budgetIndication | undefined | String of the budgetIndication |
| city             | undefined | String of the city             |

## Delete Gig

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/user/gig/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "Uw klus is geplaatst. U ontvangt een e-mail ter bevestiging",
  "status"  : 200
}
```

This endpoint allows user to place a job.

### HTTP Request

`DELETE https://api.linsta.nl/v1/user/gig/:gig_id`

### Body Parameters

| Parameter | Default   | Description                      |
| --------- | --------- | -------------------------------- |
| steps     | undefined | String MongoDB Object ID  of gig |

## Place Custom Job

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/user/place-custom-job" \
  -H "Authorization: Bearer jsonwebtoken" \
    -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'zipCode=3071BG' \
  --data-urlencode 'title=Aanbouw of opbouw plaatsen' \
  --data-urlencode 'description=Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris vel ante non libero aliquet ultricies in eu erat. Ut id metus mollis, tincidunt ex a, varius augue. Integer posuere dolor non interdum elementum. Nunc eu ullamcorper mi. Nulla gravida, nisi in euismod cursus, lorem ex mattis enim, eu ullamcorper erat enim at tellus. Nulla rhoncus pellentesque placerat. Aenean ante ante, pulvinar ac sapien eget, ornare posuere lacus. Phasellus viverra, nunc ut fermentum venenatis, massa quam placerat leo, eu rutrum orci nisl sit amet ex. In pretium semper odio et faucibus. Sed eleifend nisi nibh, vitae malesuada nisl consectetur quis. Aliquam erat volutpat. Integer maximus lacinia ante a rhoncus.' \
  --data-urlencode 'firstName=Nathan' \
  --data-urlencode 'lastName=Henniges' \
  --data-urlencode 'email=nathan@scopeweb.nl' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "De klus is geplaatst. Zodra er een match is ontvang je een email",
  "status"  : 200
}
```

This endpoint allows user to place a job.

### HTTP Request

`DELETE https://api.linsta.nl/v1/user/place-custom-job`

### Body Parameters

| Parameter   | Default   | Description                 |
| ----------- | --------- | --------------------------- |
| zipCode     | undefined | String  of the  zipCode     |
| title       | undefined | String  of the  title       |
| description | undefined | String  of the  description |
| firstName   | undefined | String  of the  firstName   |
| lastName    | undefined | String  of the  lastName    |
| email       | undefined | String  of the  email       |

## Upload Gig Image

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/upload-gig-image" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'gigImage=base64image' 
```

>The above command returns JSON structured like this:

```json
{
  imgResult: "https://res.cloudinary.com/scope-web-llc/image/upload/v1579385353/linsta/opdrachten/klus-afbeelding/klus-afbeelding-05559785.jpg",
  fileName: "klus-afbeelding-05559785",
  status: 200
}
```

This endpoint allows user upload an image for a new gig

### HTTP Request

`POST https://api.linsta.nl/v1/user/upload-gig-image`

### Body Parameters

| Parameter | Default   | Description            |
| --------- | --------- | ---------------------- |
| gigImage  | undefined | String of base64 image |

## Delete gig image

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/delete-gig-image/:imageId" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{ "message": "De afbeelding is verwijderd", "status": 200 }
```

This endpoint allows user delete an image for a new gig

### HTTP Request

`POST https://api.linsta.nl/v1/user/delete-gig-image/:imageId`

### Body Parameters

| Parameter  | Default   | Description          |
| ---------- | --------- | -------------------- |
| image_name | undefined | String of image name |

## Delete image

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/delete-image/:image_name" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{ "message": "Image has been deleted", "status": 200 }
```

This endpoint allows user delete an image

### HTTP Request

`POST https://api.linsta.nl/v1/user/delete-image/:image_name`

### Body Parameters

| Parameter  | Default   | Description          |
| ---------- | --------- | -------------------- |
| image_name | undefined | String of image name |

## Email check

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/email-check" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'email=nathan@scopeweb.nl' 
```

>The above command returns JSON structured like this:

```json
{ "message": "User with this email exists", "status": 200 }
```

This endpoint checks the email is in used.

### HTTP Request

`POST https://api.linsta.nl/v1/user/email-check`

### Body Parameters

| Parameter | Default   | Description         |
| --------- | --------- | ------------------- |
| email     | undefined | String of the email |

## List created gigs

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/gigs/created-gigs" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "error": "Je hebt nog geen opdrachten geplaatst",
  "gigs": [],
  "status": 200
}
```

This endpoint list all created gigs for the user.

### HTTP Request

`GET https://api.linsta.nl/v1/user/gigs/created-gigs`

## Upload image for gig

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/gigs/add-image/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'gigImage=base64image' 
```

>The above command returns JSON structured like this:

```json
{
  "message": "De afbeelding is aan je klus toegevoegd",
  "status": 200
}
```

This endpoint allows user upload an image for a new gig

### HTTP Request

`POST https://api.linsta.nl/v1/user/gigs/add-image/:gig_id`

### Body Parameters

| Parameter | Default   | Description            |
| --------- | --------- | ---------------------- |
| gigImage  | undefined | String of base64 image |

## Get gig

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/gigs/created-gigs/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "error": "De opdracht kon niet gevonden worden",
  "gig": [],
  "status": 200
}
```

This endpoint view gig infomation by its ID

### HTTP Request

`GET https://api.linsta.nl/v1/user/gigs/created-gigs/:gig_id`

### Body Parameters

| Parameter | Default   | Description                        |
| --------- | --------- | ---------------------------------- |
| gig_id    | undefined | String of MongoDB Object ID of gig |

## Delete Gig

```shell
curl --location --request DELETE "https://api.linsta.nl/v1/user/gigs/created-gigs/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "De opdracht is verwijderd en niet meer zichtbaar",
  "status": 200
}
```

This endpoint view gig infomation by its ID

### HTTP Request

`DELETE https://api.linsta.nl/v1/user/gigs/created-gigs/:gig_id`

### Body Parameters

| Parameter | Default   | Description                        |
| --------- | --------- | ---------------------------------- |
| gig_id    | undefined | String of MongoDB Object ID of gig |

## Invite Pro to Gig

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/professionals/invite/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'selected=id,id2,id3' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "De geselecteerde vakmannen zijn voor uw opdracht uitgenodigd",
  "status": 200
}
```

This endpoint invite pros to a gig.

### HTTP Request

`POST https://api.linsta.nl/v1/user/gigs/professionals/invite/:gig_id`

### Body Parameters

| Parameter | Default   | Description                        |
| --------- | --------- | ---------------------------------- |
| gig_id    | undefined | String of MongoDB Object ID of gig |
| selected  | undefined | Array of selected pros             |

## Decline Pro to Gig

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/professionals/decline/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'declinedProfessional=id' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "De vakman is uit uw overzicht verwijderd",
  "status": 200
}
```

This endpoint decline pros to a gig.

### HTTP Request

`POST https://api.linsta.nl/v1/user/gigs/professionals/decline/:gig_id`

### Body Parameters

| Parameter            | Default   | Description                        |
| -------------------- | --------- | ---------------------------------- |
| gig_id               | undefined | String of MongoDB Object ID of gig |
| declinedProfessional | undefined | String of MongoDB Object ID of pro |

## Add review to gig

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/review/business/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'declinedProfessional=id' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "Thank you for your review",
  "status": 200
}
```

This endpoint decline pros to a gig.

### HTTP Request

`POST https://api.linsta.nl/v1/user/gig/review/business/:gig_id`

### Body Parameters

| Parameter   | Default   | Description                        |
| ----------- | --------- | ---------------------------------- |
| gig_id      | undefined | String of MongoDB Object ID of gig |
| rating      | undefined | Number Rating                      |
| title       | undefined | String of the  title               |
| description | undefined | String of the  description         |

## Choose Pro

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/professionals/choose/:gig_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'professionalId=id' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "De vakman is geselecteerd voor uw opdracht",
  "status": 200
}
```

This endpoint allows a user to pick a pitch.

### HTTP Request

`POST https://api.linsta.nl/v1/user/professionals/choose/:gig_id`

### Body Parameters

| Parameter      | Default   | Description                                 |
| -------------- | --------- | ------------------------------------------- |
| gig_id         | undefined | String of MongoDB Object ID of gig          |
| professionalId | undefined | String of MongoDB Object ID of professional |

## Find KB

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/find/kb" \
  -H "Authorization: Bearer jsonwebtoken" 
```

>The above command returns JSON structured like this:

```json
{
  "message": "De vakman is geselecteerd voor uw opdracht",
  "status": 200
}
```

This endpoint serach KB.

### HTTP Request

`GET https://api.linsta.nl/v1/user/find/kb`

### Body Parameters

| Parameter | Default   | Description      |
| --------- | --------- | ---------------- |
| search    | undefined | String of search |

## Find KB by category

```shell
curl --location --request GET "https://api.linsta.nl/v1/user/find-articles/:kb_category" \
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
            "category": "5e1f7926efac6e58c731b346",
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

This endpoint retrieve articles in a KB category

### HTTP Request

`GET https://api.linsta.nl/v1/user/find-articles/:kb_category`

### Body Parameters

| Parameter   | Default   | Description               |
| ----------- | --------- | ------------------------- |
| kb_category | undefined | String of the kb_category |

## Send feedback on KB

```shell
curl --location --request POST "https://api.linsta.nl/v1/user/submit/kb/:kb_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'votedHelpful=Good' \
  --data-urlencode 'comment=Thanks' \
```

>The above command returns JSON structured like this:

```json
{
  "message": "Bedankt voor uw feedback",
  "status": 200
}
```

This endpoint allows a user to send feedback to KB

### HTTP Request

`POST https://api.linsta.nl/v1/user/submit/kb/:kb_id`

### Body Parameters

| Parameter    | Default   | Description                       |
| ------------ | --------- | --------------------------------- |
| kb_id        | undefined | String of MongoDB Object ID of kb |
| votedHelpful | undefined | String of the votedHelpful        |
| comment      | undefined | String of the comment             |
