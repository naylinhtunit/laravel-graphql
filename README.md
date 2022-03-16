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
<img src="https://i.ibb.co/Zf33xdg/laravel-graphql-test.jpg" alt="laravel-graphql-test" border="0">