1. A count of all posts having the word "Hello" inside the body created or updated on January 1, 2016.

```
Post.where("body LIKE '%Hello%' AND created_at BETWEEN '2016-01-01 00:00:00' AND '2016-01-01 23:59:59' AND updated_at BETWEEN '2016-01-01 00:00:00' AND '2016-01-01 23:59:59'").count
```

``` sql
SELECT COUNT(*)
FROM posts
WHERE body LIKE '%Hello%'
AND (created_at BETWEEN '2016-01-01 00:00:00' AND '2016-01-01 23:59:59')
AND (updated_at BETWEEN '2016-01-01 00:00:00' AND '2016-01-01 23:59:59');
```

2. A list of all users that do not have any posts yet.

```
User.join("LEFT OUTER JOIN posts ON user_id=users.id").group(:username).having("COUNT(*)=0")
```

``` sql
SELECT username, COUNT(*)
FROM users LEFT OUTER JOIN posts ON user_id=users.id
GROUP BY users.id
HAVING COUNT(*)=0;
```

3. An average of each user's post count.

```
User.join("LEFT OUTER JOIN posts ON user_id=users.id").group("users.id").average("IFNULL(posts.id, 0)")
```

``` sql
SELECT username, AVG(IFNULL(posts.id, 0))
FROM users LEFT OUTER JOIN posts ON user_id=users.id
GROUP BY users.id;
```
