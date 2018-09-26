---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - PHP


toc_footers:
  - <a href='https://github.com/lord/slate'>Powered by Designvox</a>

includes:
  - errors

search: true
---

# Introduction

## API Reference

The SpringHill API is organized around REST. Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We use built-in HTTP features, like HTTP authentication and HTTP verbs, which are understood by off-the-shelf HTTP clients. We support cross-origin resource sharing, allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). JSON is returned by all API responses, including errors, although our API libraries convert responses to appropriate language-specific objects.

To make the API as explorable as possible, accounts have test mode and live mode API keys. There is no "switch" for changing between modes, just use the appropriate key to perform a live or test transaction. Requests made with test mode credentials never hit the banking networks and incur no cost.

Be sure to subscribe to SpringHill's API announce mailing list to receive information on new additions and changes to SpringHill's API and language libraries.

# Authentication

> To authorize, use this code:

```PHP
require 'springhill'

api = SpringHill::APIClient.authorize!('sk_test_4eC39HqLyjWDarjtT1zdp7dc')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```
> Make sure to replace `sk_test_4eC39HqLyjWDarjtT1zdp7dc` with your API key.

SpringHill uses API keys to allow access to the API. You can register a new SpringHill API key at our [developer portal](http://example.com/developers).

SpringHill expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: sk_test_4eC39HqLyjWDarjtT1zdp7dc`

<aside class="notice">
You must replace <code>sk_test_4eC39HqLyjWDarjtT1zdp7dc</code> with your personal API key.
</aside>

# Registration

## Register Individuals

```php
\SpringHill\SpringHill::setApiKey("sk_test_4eC39HqLyjWDarjtT1zdp7dc");

\SpringHill\RegisterIndividual::create(array(
  "name" => "Test",
  "last_name" => "TestUser",
  "birth_date" => "9/30/1970"
));
```

```shell
curl https://api.stripe.com/v1/registerindividual \
   -u sk_test_4eC39HqLyjWDarjtT1zdp7dc: \
   -d name=Test \
   -d last_name=TestUser \
   -d birth_date="9/30/1970"
```

> The above command returns JSON response structured like this:

```json
[
  {
    "code":200,
    "status": "Individual created successfuly"
  }
  {
    "id": 1,
    "name": "Test",
    "last_name": "TestUser",
    "birth_date": 9/30/1970,
    "entity_id": 9930
  }
]
```

This endpoint retrieves all Individuals.

### HTTP Request

`GET http://api.springhill.com/api/createindividuals`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
name | string | Name of the Individual
last_name | string | Last Name of the Individual
birth_date | date | Birth Date of Individuale

<aside class="success">
Remember — a happy individual is an authenticated individual!
</aside>

## Get a Specific Individual

```php
require 'springhill'

\SpringHill\SpringHill::setApiKey("sk_test_4eC39HqLyjWDarjtT1zdp7dc");

\SpringHill\Individual::retrieve("9930");
```

```shell
curl https://api.springhill.com/v1/individual/9930 \
   -u sk_test_4eC39HqLyjWDarjtT1zdp7dc:
```

> The above command returns JSON response structured like this:

```json
{
  "id": 1,
  "name": "Test",
  "last_name": "TestUser",
  "birth_date": 9/30/1970,
  "entity_id": 9930
}
```

This endpoint retrieves a specific individual.


### HTTP Request

`GET https://api.springhill.com/v1/individual/9930`

### URL Parameters

Parameter | Description
--------- | -----------
entity_id | The entity ID of the individual to retrieve



# People Management

# Groups + Housing

# Scheduling + Attendance

# Transportation

# Check-in + Check-out

# Staffing + Resourcing

# My Dashboard (Staff)

# Health Center

# Analytics and Reporting
