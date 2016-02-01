### Translate from SQL to Active Record

1.

``` sql
SELECT *
FROM
  users;
```

```
User.all
```

2.

``` sql
SELECT *
FROM
  users
WHERE
  user.id = 1;
```

```
User.find(1)
```

3.

``` sql
SELECT *
FROM
  posts
ORDER BY
  created_at DESC
LIMIT 1;
```

```
User.last
```

4.

``` sql
SELECT *
FROM
  users
JOIN
  posts
ON
  posts.author_id = users.id
WHERE
  posts.created_at >= '2014-08-31 00:00:00';
```

```
User.join("posts").where("posts.created_at >= '2014-08-31 00:00:00'")
```

5.

``` sql
SELECT
  count(*)
FROM
  users
GROUP BY
  favorite_color
HAVING
  count(*) > 1;
```

```
User.group(:favorite_color).having('count(*) > 1').count
```

* The most recently updated user

```
User.order(:updated_at).last
```

* The oldest user (by age)

```
User.order("age").last
```

* all the users

```
User.all
```

* all posts sorted in descending order by date created

```
Post.order("created_at DESC")
```
