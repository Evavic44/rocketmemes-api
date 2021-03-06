---
description: >-
  In this quick guide we will look making simple requests to our the Rocketmeme
  GraphQL API.
---

# Get Started

{% hint style="info" %}
**Good to know:** You could make a your requests with everyday programming tools you use. All it takes is a simple post request containing the query as a string.
{% endhint %}

## Access is free

You don't need an API key to use our API.

## Making your first request

### GraphQL API

We'll do a simple query to get meme categories using different languages.

{% tabs %}
{% tab title="JavaScript" %}
```javascript
fetch('https://rocketmeme-user.hasura.app/v1/graphql', {
    method: 'POST',
    headers: {
        'content-type': 'application/json',
    },
    body: JSON.stringify({"operationName":"getPaginatedMemeCategories","variables":{},"query":"query getPaginatedMemeCategories {\n  meme_categories_aggregate(limit: 10, offset: 0) {\n    nodes {\n      id\n      category_title\n      no_of_memes\n      thumb_nail\n      __typename\n    }\n    __typename\n  }\n  count: memes_aggregate(offset: 0) {\n    aggregate {\n      count\n      __typename\n    }\n    __typename\n  }\n}\n"})
});
```
{% endtab %}

{% tab title="Node" %}
```javascript
import fetch from "node-fetch";

const query = `
  query getMemes {
    memes(limit: 3) {
      id
      title
      image_link
    }
  }
`;

const result = await fetch("https://rocketmeme-user.hasura.app/v1/graphql", {
  method: "POST",
  headers: {
    "content-type": "application/json",
  },
  body: JSON.stringify({
    operationName: "getMemes",
    variables: {},
    query: query,
  }),
});

const data = await result.json();
console.log(data);
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

json_data = {
    'operationName': 'getPaginatedMemeCategories',
    'variables': {},
    'query': 'query getPaginatedMemeCategories {\n  meme_categories_aggregate(limit: 10, offset: 0) {\n    nodes {\n      id\n      category_title\n      no_of_memes\n      thumb_nail\n      __typename\n    }\n    __typename\n  }\n  count: memes_aggregate(offset: 0) {\n    aggregate {\n      count\n      __typename\n    }\n    __typename\n  }\n}\n',
}

response = requests.post('https://rocketmeme-user.hasura.app/v1/graphql', json=json_data)
print(response.content)
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Good to know:** You could use GraphQL client libraries to simplify requests.&#x20;
{% endhint %}

### Rest API

To make your first request, send a request to the memes endpoint. This will return a list of memes, which is nice.

{% swagger baseUrl="https://api.myapi.com/v1" method="post" path="/pet" summary="Create pet." %}
{% swagger-description %}
Creates a new pet.
{% endswagger-description %}

{% swagger-parameter in="body" name="name" required="true" type="string" %}
The name of the pet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="owner_id" required="false" type="string" %}
The

`id`

of the user who owns the pet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="species" required="false" type="string" %}
The species of the pet
{% endswagger-parameter %}

{% swagger-parameter in="body" name="breed" required="false" type="string" %}
The breed of the pet
{% endswagger-parameter %}

{% swagger-response status="200" description="Pet successfully created" %}
```javascript
{
    "name"="Wilson",
    "owner": {
        "id": "sha7891bikojbkreuy",
        "name": "Samuel Passet",
    "species": "Dog",}
    "breed": "Golden Retriever",
}
```
{% endswagger-response %}

{% swagger-response status="401" description="Permission denied" %}

{% endswagger-response %}
{% endswagger %}

****

