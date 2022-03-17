# Laravel GraphQL

* My note

* https://lighthouse-php.com/5/getting-started/installation.html#install-via-composer

```
composer require nuwave/lighthouse
php artisan vendor:publish --tag=lighthouse-schema
php artisan lighthouse:ide-helper
composer require mll-lab/laravel-graphql-playground
```

* Check url (http://laravel-graphql.test/graphql)

* Check url (http://laravel-graphql.test/graphql-playground)

```
php artisan migrate
php artisan tinker
User::factory()->create()
```

* Check url (http://laravel-graphql.test/graphql-playground)

```
{
  user(id:1) {
    id,
    name,
    email
  }
}
php artisan vendor:publish --tag=lighthouse-config
```

* Test graphql > schema.graphql

```
# All users
type Query
{
  users: [User] @all
}

type User
{
  id: ID,
  name: String
  email_verified_at: String
}
```

```
php artisan tinker
User::factory()->create()
```

* Check url (http://laravel-graphql.test/graphql-playground)

```
{
  users {
    id,
    name,
    email_verified_at
  }
}
```
<img src="https://i.ibb.co/Zf33xdg/laravel-graphql-test.jpg">


* Test graphql > schema.graphql

* ! => Cannot return null for non-nullable field for @all user

```
type User
{
  id: ID,
  name: String
  email_verified_at: String!
}
```

<img src="https://i.ibb.co/8BvZ6gP/02laravel-graphql-test.jpg">

```
type Query
{
  users: [User!] @all
}
```
<img src="https://i.ibb.co/gjHHKzZ/01laravel-graphql-test.jpg">

```
php artisan tinker
User::factory()->count(5)->create()
```

* Test graphql > schema.graphql

```
type Query
{
  user(id: ID @eq): User @find
}
```

* Check url (http://laravel-graphql.test/graphql-playground)

```
{
  user(id: 1){
    id
  }
}
```

* Test graphql > schema.graphql

```
  #for paginate
  users: [User!]! @paginate
```

* Check url (http://laravel-graphql.test/graphql-playground)

```
{
  users(first: 2){
    data{
      name
    }
  }
}
```