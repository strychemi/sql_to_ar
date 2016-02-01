1.

```
Post.all
```

``` sql
SELECT *
FROM posts;
```

2.

```
Post.first
```

``` sql
SELECT *
FROM posts
ORDER BY created_at
LIMIT 1;
```

3.

```
Post.last
```

``` sql
SELECT *
FROM posts
ORDER BY created_at DESC
LIMIT 1;
```

4.

```
Post.where(:id => 4)
```

``` sql
SELECT *
FROM posts
WHERE id=4;
```

5.

```
Post.find(4)
```

``` sql
SELECT *
FROM posts
WHERE id=4
LIMIT 1;
```

6.

```
User.count
```

``` sql
SELECT COUNT(*)
FROM users;
```

7.

```
Post.select(:name).where(:created_at > 3.days.ago).order(:created_at)
```

``` sql
SELECT name
FROM posts
WHERE created_at > 3.days.ago
ORDER BY created_at;
```

8.

```
Post.select("COUNT(*)").group(:category_id)
```

``` sql
SELECT COUNT(*)
FROM posts
GROUP BY category_id;
```

9.

```
All posts created before 2014
```

``` sql
SELECT *
FROM posts
WHERE created_at < '2014-01-01 00:00:00';
```

10.

```
A list of all (unique) first names for authors who have written at least 3 posts
```

``` sql
SELECT DISTINCT first_name
FROM posts JOIN authors ON author_id=authors.id
GROUP BY authors.id
HAVING COUNT(posts.id) >= 3;
```

11.

```
The posts with titles that start with the word "The"
```

``` sql
SELECT *
FROM posts
WHERE title LIKE 'The%';
```

12.

```
Posts with IDs of 3,5,7, and 9
```

``` sql
SELECT *
FROM posts
WHERE id IN (3,5,7,9);
```
