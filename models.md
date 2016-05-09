# Models definition
+ The store needs to be able to map type names to TS classes.

### Proposition 1

```typescript
@JsonApiModel({
  type: 'posts',
  endpoint: '/posts',
  baseUrl: 'http://api.example.com'
})
class Post {
  @JsonApiAttribute()
  title: string

  @JsonApiAttribute()
  content: string

  @JsonApiAttribute({
    key: 'published_at'
  })
  publishedAt: Date

  @JsonApiRelationship({
    type: 'HasOne',
    inverseOf: 'comments'
  })
  author: User

  @JsonApiRelationship({
    type: 'HasMany'
  })
  comments: Array<Comment>
}
```