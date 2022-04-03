---
description: You could get memes whether its paginated or not
---

# Get Meme

## GraphQL

### Getting  All memes

```graphql
query {
    memes {
        id
        title
        image_link
        category
    }
}
```

{% hint style="info" %}
**Good to know:** These queries can be modified to get valid fields as needed
{% endhint %}

### Paginated memes

Get a list of memes with limit and offset.

```graphql
query getPaginatedMeme {
  memes(limit: 10, offset: 0) {
    id
    category
    title
  }
}
```

## Updating a pet

{% swagger src="https://petstore.swagger.io/v2/swagger.json" path="/pet" method="put" %}
[https://petstore.swagger.io/v2/swagger.json](https://petstore.swagger.io/v2/swagger.json)
{% endswagger %}

{% hint style="info" %}
**Good to know:** This API method was auto-generated from an example Swagger file. You'll see that it's not editable – that's because the contents are synced to an URL! Any time the linked file changes, the documentation will change too.
{% endhint %}
