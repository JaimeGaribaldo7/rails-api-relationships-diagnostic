# Rails API Relationships Diagnostic

Place your responses inside the fenced code-blocks where indivated by comments.

1.  Describe a reason why a join tables may be valuable.

```sh
A join table is valuable in many ways, but it depends on what kind of
information the user might need. For example we created an appointments table
that gave us information about both, patients and doctors.
```

1.  Provide a database table structure and explain the Entity Relationship that
describes a many-to-many relationship for `Profiles`, `Movies` and `Favorites`
(Think of Netflix). A `Profile` has a `given_name`, `surname` and `email` and a
`Movies` have `title`, `release_date`, and `length` and `Favorites` would be the
join table with references to `Movies` and `Profiles`.

```sh
Profiles(
given_name TEXT,
surname TEXT,
email TEXT,
)
Movies(
title TEXT,
release_date DATE,
length TEXT,
)
Favorites(
profile_id
Movie_id
)
```

1.  For the above example, what needs to be added to the Model files?

```rb
class Profile < ActiveRecord::Base
has_many Movies
end
```

```rb
class Movie < ActiveRecord::Base
has_many Profiles
end
```

```rb
class Favorite < ActiveRecord::Base
belongs_to Profiles
belongs to Movies
end
```

1.  What is the purpose of a serializer? What would our `Profile` serializer
look like to show all movies favorited by a profile on
`http://localhost:3000/profiles/1`

```sh
Movies{
  Profile#1{
  given_name:
  surname:
    Favorites{
    index of all movies
    }
  }
}
```

```rb
class ProfileSerializer < ActiveModel::Serializer
attributes :given_name, :surname, :email
end
```

1.  What would the command be to _scaffold_ out a **join table** for Favorites
from the above `Movies` and `Profiles`.

```sh
bundle exec rails g scaffold GoodMovies favorites:string profiles:string
```

1.  What is `Dependent: Destroy` and where/why would we use it?

```sh
this decides what will happen when something gets destroyed and you would use it on the join table when you dont need information from it.
```

1.  Think of **ANY** example where you would have a one-to-many relationship as
well as a many-to-many relationship in an application. You only need to list the
description about the resources and how they relate to one another.

```sh
  # < Your Response Here >
```
