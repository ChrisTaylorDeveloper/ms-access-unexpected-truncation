# MS Access unexpected truncation

Demo of unexpected column truncation, when selecting a query result into a new table.

## Description
`qry1` is based on `tbl1`.

`qry1` selects `blog_post` and the result of `blog_post` returned from a `ToUpperCase` function.

`select_qry1_into_new_tbl` creates `tbl_made_from_qry1` but the column which is the result of `ToUpperCase` is truncated to type Short Text.

Running `select_qry1_into_existing_tbl` creates a table with two columns of type Long Text, as expected.

## SQL

### qry1
```
SELECT
    blog_post,
    ToUpperCase(blog_post) As blog_post_uc
FROM tbl1;
```

### select_qry1_into_new_tbl
```
SELECT * INTO tbl_made_from_qry1 FROM qry1
```

### select_qry1_into_existing_tbl
```
INSERT INTO tbl2 (blog_post, blog_post_uc)
SELECT blog_post, blog_post_uc FROM qry1;
```

### create_tbl2  
```
CREATE TABLE tbl2 (
    blog_post Memo, 
    blog_post_uc Memo
);
```