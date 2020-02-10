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

`GET https://dev.linsta.nl/v1/admin/place-jobs/add-fieldtype`

## Add a review to a business

```shell
curl --location --request POST "https://dev.linsta.nl/v1/admin/business/add-review/:business_id" \
  -H "Authorization: Bearer jsonwebtoken" \
  -H 'Content-Type: application/x-www-form-urlencoded' \
  --data-urlencode 'reviewer=5dd570d1873225ab198e47d4' \
  --data-urlencode 'rating=10' \
  --data-urlencode 'title=Great enterprise business.' \
  --data-urlencode 'description=Helped make my company a lot more enterprise by offering me great service at a great price.'
```

>The above command returns JSON structured like this:

```json
{ "message": "Saved new review for business", "status": 200 }
```

This endpoint adds a review to a business.

### HTTP Request

`POST https://dev.linsta.nl/v1/admin/business/add-review/:business_id"`

### Body Parameters

| Parameter   | Default   | Description                         |
| ----------- | --------- | ----------------------------------- |
| reviewer    | undefined | Mongoose Object ID of the reviewer  |
| rating      | undefined | Number out of 1-10 of review rating |
| title       | undefined | Title of the review                 |
| description | undefined | Description of the review           |

## Get reviews

```shell
curl --location --request POST "https://dev.linsta.nl/v1/admin/reviews/:filter_type" \
  -H "Authorization: Bearer jsonwebtoken"
```

>The above command returns JSON structured like this:

```json
{ "message": "Saved new review for business", "status": 200 }
```

This endpoint retrieves all reviews with the ability to filter then.

### HTTP Request

`POST https://dev.linsta.nl/v1/admin/reviews/:filter_type`

### Query Parameters

| Parameter   | Default   | Description                                                        |
| ----------- | --------- | ------------------------------------------------------------------ |
| filter_type | undefined | Type of filter.  Supported ones are newest, oldest, rateHL, rateLH |
| industry    | undefined | String ofindustry name                                             |
