# Models definition
+ The store needs to be able to map type names to TS classes.

### Proposition 1

Store configuration/declaration:
```typescript
@Injectable()
@JsonApiDatastoreConfig({
  baseUrl: 'http://api.example.com',
  models: {
    posts: Post,
    users: User,
    comments: Comment
  }
})
class Datastore extends JsonApiDatastore { }
```

```typescript
@JsonApiModelConfig({
  type: 'posts', // optional
  endpoint: '/posts', // optional
  baseUrl: 'http://api.other.com' // optional
})
class Post extends JsonApiModel {
  @Attribute()
  title: string

  @Attribute()
  content: string

  @Attribute({
    key: 'published_at' // optional
  })
  publishedAt: Date

  @BelongsTo({
    inverseOf: 'comments' // optional
  })
  author: User

  @HasMany()
  comments: Array<Comment>
}
```