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

### Body

| Parameter   | Default   | Description                 |
| ----------- | --------- | --------------------------- |
| steps       | undefined | Array of steps              |
| serviceName | undefined | String of the service name  |
| keywords    | undefined | String array of keywords    |
| images      | undefined | Array of image urls         |
| industry    | undefined | String of the industry name |

## Add Field type

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

### Body

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
  -H "Authorization: Bearer jsonwebtoken" \
```

>The above command returns JSON structured like this:

```json
{
    "message": "Industry has been added.",
    "status": 200
}
```

This endpoint creates a new fieldtype.

### HTTP Request

`DELETE https://dev.linsta.nl/v1/admin/category/:job_id`
